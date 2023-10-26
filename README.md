This contains instructions to launch 
1. Hesai Lidar
2. ArduXXX RTK GNSS
3. Intel RealSense
4. OrbSLAM3
5. ROSBridge
6. Husky controller


## To setup Lidar(ROS1) - General(ROS2) bridge

Two terminals reserved for ROS Bridge

Terminal A: (Inside humble_noetic_rosbridge_docker)
```
# First source ROS1
# source ${ROS1_INSTALL_PATH}/setup.bash
source ros_noetic_base_2204/catkin_ws/devel/setup.bash
roscore
```

Terminal B: (Inside humble_noetic_rosbridge_docker)

Build rosbridge package
Source ros2_ws/install/setup.bash
```
source ros2_ws/install/setup.bash
```

Build the ros2 workspace with the ros1_bridge package
```
# Takes more than 5 minutes
colon build
```

```
# First source ROS1
#source ${ROS1_INSTALL_PATH}/setup.bash
source ros_noetic_base_2204/catkin_ws/devel/setup.bash

# Source ROS2
# source ${ROS2_INSTALL_PATH}/setup.bash
source ros2_ws/install/setup.bash

# Bridge all topics both ways
ros2 run ros1_bridge dynamic_bridge --bridge-all-topics
```

Terminal C for launch ROS1 - Hesai Lidar Sensor (Inside Hesai Docker)
```
make launch_hesai_lidar_alfredo 
```
Terminal D for Visualizing exchange of topics between ROS1 and ROS2
Launch RVIZ from any container or host machine (ROS1 or ROS2 version)
```
make enter
```

```
source /opt/ros/noetic/setup.bash 
rviz
```
Set global frame as "PandarXT-32" in the RViz
