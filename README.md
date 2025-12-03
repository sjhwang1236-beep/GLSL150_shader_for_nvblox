#  Problem 1
- When the Nvblox quickstart shutdowned, follow this solution
- Isaac ROS NVBlox visualization in RViz was failing due to missing GLSL 150 geometry shaders.
- The error was related to box.geom not being found.

# What We Created
- box.geom, Geometry shader that generates axis-aligned boxes (the file causing the original error)
- billboard.geom, Geometry shader for billboard rendering
- pass_pos_color.vert, Vertex shader that passes position and color data
- glsl150.program, OGRE program definitions that register all the shaders.

# Installation Location
- Place 4 files at `/opt/ros/humble/share/rviz_rendering/ogre_media/materials/glsl150` in the container.

# Environment Variable
```
export ISAAC_ROS_NVBLOX_PLUGIN_FORCE_FALLBACK_MATERIAL=1
```

# Problem 2
- When nvblox output is not showed in rviz2, follow this solution.

# Install nvblox_rviz_plugin
```
git clone https://github.com/NVIDIA-ISAAC-ROS/isaac_ros_nvblox.git
colcon build --packages-up-to nvblox_rviz_plugin 2>&1
source /workspaces/isaac_ros-dev/install/setup.bash
```

# Nvblox worked well
```
ros2 launch nvblox_examples_bringup isaac_sim_example.launch.py \
rosbag:=${ISAAC_ROS_WS}/isaac_ros_assets/isaac_ros_nvblox/quickstart \
navigation:=False
```
