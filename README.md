# Highway Driving

The goal of this project is to build a path planner that creates smooth, safe trajectories for the car to follow. The highway track has other vehicles, all going different speeds, but approximately obeying the 50 MPH speed limit.

---

## Prerequisites

* Term 3 Simulator with uWebSocketIO
* cmake >= 3.5
* make >= 4.1
* gcc/g++ >= 5.4

If you want to install the libraries on linux Operating System use install-linux.sh(./install-linux.sh) or for OSX use install-mac.sh(./install-mac.sh).

---

## Basic Build Instructions

1. Clone this repo.
2. Select build directory: `cd build`
3. Compile: `cmake .. && make` 
4. Run it: `./path_planning `

---

## Results

The results can be visualized in the video file 'final_video_4x_speed.mp4'. 

The following specifications have been accomplished:
  1. The car is able to drive at least 4.32 miles without incident.
  2. The car drives according to the speed limit (50mph).
  3. Max Acceleration and Jerk are not Exceeded. (acceleration < 10m/s^2, jerk 10m/s^3).
  4. Car does not have collisions.
  5. The car stays in its lane, except for the time between changing lanes.
  6. The car is able to change lanes.
  
 ---
 
## Reflections
 
Using sensor fusion data, I was able to make the prediction in the following way:
  1. Verify if a car is in front of us and it's slowing us down.
  2. If 1. is true, we are looking at the left lane (if possible) and verify if there are any cars.
  3. If 2. returns cars we are looking also at the right lane (if possible) and verify if there are any cars.
  
Let's break this into small parts:
  1. If the car in front of us is closer than 25 meters, we start looking for cars in other lanes.
  2. Left lane and right lane cars are sorted.
  3. We are looking for the front car and back car from other lane compared to our position.
  4. If a gap has been found, we are also verifying the back car speed, and if that car's speed is lower or equal with our and the distance between us is greater than a custom threshold, we are changing the lane.
  5. Every time the left lane has priority over the right lane, considering that the left lane usually is meant for higher speeds.
 
