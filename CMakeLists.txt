cmake_minimum_required(VERSION 3.0.2)
project(hedge_msg_adapter)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  sensor_msgs
  marvelmind_nav
  geometry_msgs
)

# Initialise the export variables
catkin_package(
  INCLUDE_DIRS src
  # LIBRARIES blah
  CATKIN_DEPENDS roscpp std_msgs sensor_msgs marvelmind_nav geometry_msgs 
  DEPENDS system_lib
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

# One per executable!
add_executable(msg_adapter src/hedge_msg_adapter.cpp)
target_link_libraries(msg_adapter ${catkin_LIBRARIES})

install(DIRECTORY launch
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)