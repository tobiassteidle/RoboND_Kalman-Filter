[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)

# RoboND_Kalman-Filter
Lab for Robotics Software Engineer "Kalman Filter"

### Steps to launch the simulation

#### Step 1 Update and upgrade the Workspace image
```sh
$ sudo apt-get update
$ sudo apt-get upgrade -y
```

#### Step 2 Clone the lab folder in /home/workspace/
```sh
$ cd /home/workspace/
$ git clone https://github.com/tobiassteidle/RoboND_Kalman-Filter.git
```

#### Step 3 Compile the code
```sh
$ cd /home/workspace/RoboND_Kalman-Filter/catkin_ws
$ catkin_make
```

#### Step 4 Clone required packages
```sh
$ cd /home/workspace/RoboND_Kalman-Filter/catkin_ws/src
$ git clone https://github.com/turtlebot/turtlebot_simulator
$ git clone https://github.com/udacity/robot_pose_ekf 
$ git clone https://github.com/udacity/odom_to_trajectory
$ git clone https://github.com/turtlebot/turtlebot
```

#### Step 5 Edit `robot_pose_ekf.launch` 
```xml
<launch>

<node pkg="robot_pose_ekf" type="robot_pose_ekf" name="robot_pose_ekf">
  <param name="output_frame" value="odom_combined"/>
  <param name="base_footprint_frame" value="base_footprint"/>
  <param name="freq" value="30.0"/>
  <param name="sensor_timeout" value="1.0"/>  
  <param name="odom_used" value="true"/>
  <param name="imu_used" value="true"/>
  <param name="vo_used" value="false"/>

  <remap from="imu_data" to="/mobile_base/sensors/imu_data" />    

</node>

</launch>
```

#### Step 6 Install dependencies
```sh
$ cd /home/workspace/RoboND_Kalman-Filter/catkin_ws
$ source devel/setup.bash
$ rosdep -i install turtlebot_teleop
$ rosdep -i install turtlebot_gazebo
```

#### Step 7 Build Package
```sh
$ cd /home/workspace/RoboND_Kalman-Filter/catkin_ws
$ catkin_make
$ source devel/setup.bash
```

#### Step 8 Run the Simulation  
```sh
$ roslaunch turtlebot_gazebo turtlebot_world.launch
```

#### Step 8 Topics  
```sh
$ rostopic list
Or
$ rosrun rqt_graph rqt_graph
```

### Output
![alt text](images/output.png)
