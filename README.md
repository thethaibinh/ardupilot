## Ardupilot SITL simulation for a quadplane
A SITL simulation with Ardupilot controller, Mission Planner GCS, and a quadplane model from X-Plane.

[Project website](http://thaibinhnguyen.xyz/project-view/ardupilot-sitl-simulation-for-a-quadplane/)

# 1. Overview
This project provides a configuration to run a light and precise SITL simulation for a Quadplane using the Ardupilot controller with an aircraft model in X-Plane.
Many individual developers do not have a PC that strong enough to run a full-featured flight simulation with a high frame rate, especially when it comes to a professional platform such as X-Plane. However, if we only want a flight to evaluate algorithms at navigational levels, we can still manipulate tools and configurations to archive that. 
Ardupilot does support X-Plane simulations if it has a stable frame rate, data rate, and not too much drop-out. Error from frame rate missing would integrate into a failure. I modified the way it calculates aircraft position so that it rejects combined error.

# 2. Getting started
  * Run X-Plane with your quadplane model. You have to manual adjust 
  * In X-Plane, go to Settings --> tab Data Output --> NETWORK CONFIGURATION,
      Choose "Send network data output". Set IP address: 127.0.0.1
      Port 49005
  * Run Ardupilot SITL by the command
      sim_vehicle.py -v ArduPlane -f xplane 
      option parameters: --console --map    
      > /ardupilot$ sim_vehicle.py -v ArduPlane -f xplane --console --map
  * Flight operation by mavproxy cmd or GCS Mission Planner or QgroundControl      
  * Parameters file for autopilot:
      Simulation: xplane_sil_6H.param
      Sample flight mission 915 Hoa Lac: 916_15012020.waypoint 
      in libraries/SITL/params Xplane của project. 
# 3. Flight your own models and learn.
  * Refer [modelling instruction](https://developer.x-plane.com/manuals/planemaker/#The_Plane_Maker_Interface) from Laminar Research
  to build your own aircraft models. 
  * Try the [Penguin drone](https://forums.x-plane.org/index.php?/files/file/33625-tactical-drone-penguin-like/) if you like. 
  It's a inverted V-tail configuration and is the same UAV class with my model. Therefore, it's compatible with the control model.
  You might need to fine tune several PID parameters to make it flight.
    
  ![quadplane](https://github.com/thethaibinh/ardupilot/blob/Quadplane-Xplane/2020-04-23%204.07.16%20AM.png?raw=true)
