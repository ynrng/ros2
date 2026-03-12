# Build on mac on 12/Mar/2026
There are some dependency and environment issues from the original ros2.repos. mainly on rviz. fixed by changing branch of some packages.

```sh
conda install python=3.10
conda install cmake=3.22

brew install asio assimp bison bullet cmake console_bridge cppcheck \
   cunit eigen freetype graphviz opencv openssl orocos-kdl pcre poco \
   pyqt@5 python qt@5 sip spdlog osrf/simulation/tinyxml1 tinyxml2


python3 -m pip install --upgrade pip

python3 -m pip install -U \
  --config-settings="--global-option=build_ext" \
  --config-settings="--global-option=-I$(brew --prefix graphviz)/include/" \
  --config-settings="--global-option=-L$(brew --prefix graphviz)/lib/" \
  argcomplete catkin_pkg colcon-common-extensions coverage \
  cryptography empy<4.0 flake8 flake8-blind-except==0.1.1 flake8-builtins \
  flake8-class-newline flake8-comprehensions flake8-deprecated \
  flake8-docstrings flake8-import-order flake8-quotes \
  importlib-metadata lark==1.1.1 lxml matplotlib mock mypy==0.931 netifaces \
  nose pep8 psutil pydocstyle pydot pygraphviz pyparsing==2.4.7 \
  pytest-mock rosdep rosdistro setuptools==59.6.0 vcstool


mkdir -p ~/ros2_humble/src
cd ~/ros2_humble
vcs import --input https://raw.githubusercontent.com/ynrng/ros2/refs/heads/humble/ros2.repos src

cd ~/ros2_humble/ 
colcon build --symlink-install --packages-skip-by-dep python_qt_binding --cmake-args -DBUILD_TESTING=OFF   

```

# About
The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications.
From drivers to state-of-the-art algorithms, and with powerful developer tools, ROS has what you need for your next robotics project.
And it's all open source.
Full project details on [ROS.org](https://ros.org/)

# Getting Started
Looking to get started with ROS?
Our [installation guide is here](https://www.ros.org/blog/getting-started/).
Once you've installed ROS start by learning some [basic concepts](https://docs.ros.org/en/humble/Concepts/Basic.html) and take a look at our [beginner tutorials](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools.html).

# Join the ROS Community

## Community Resources

* [ROS Discussion Forum](https://discourse.ros.org/)
* [ROS Zulip Server](https://openrobotics.zulipchat.com/)
* [Robotics Stack Exchange](https://robotics.stackexchange.com/) (preferred ROS support forum).
* [Official ROS Videos](https://vimeo.com/osrfoundation)
* [ROSCon](https://roscon.ros.org), our yearly developer conference.
* Cite ROS 2 in academic work using [DOI: 10.1126/scirobotics.abm6074](https://www.science.org/doi/10.1126/scirobotics.abm6074)

## Developer Resources
* [ROS 2 Documentation](https://docs.ros.org/)
* [ROS Package API reference](https://docs.ros.org/en/humble/p/)
* [ROS Package Index](https://index.ros.org/)
* [ROS on Docker Hub](https://hub.docker.com/_/ros/)
* [ROS Resource Status Page](https://status.openrobotics.org/)
* [REP-2000](https://ros.org/reps/rep-2000.html): ROS 2 Releases and Target Platforms

## Project Resources
* [Purchase ROS Swag](https://spring.ros.org/)
* [Information about the ROS Trademark](https://www.ros.org/blog/media/)
* On Social Media
  * [Open Robotics on LinkedIn](https://www.linkedin.com/company/open-source-robotics-foundation)
  * [Open Robotics on Twitter](https://twitter.com/OpenRoboticsOrg)
  * [ROS.org on Twitter](https://twitter.com/ROSOrg)

ROS is made possible through the generous support of open source contributors and the non-profit [Open Source Robotics Foundation (OSRF)](https://www.openrobotics.org/).
Tax deductible donations to the OSRF can be [made here.](https://donorbox.org/support-open-robotics?utm_medium=qrcode&utm_source=qrcode)
