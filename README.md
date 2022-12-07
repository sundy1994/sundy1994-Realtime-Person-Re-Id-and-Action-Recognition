# Realtime-Person-Re-Id-and-Action-Recognition
A skeleton-based real-time online action recognition project, recognizing different person and classifying actions base on framewise joints.

------
## Source    
 - [Online-Realtime-Action-Recognition-based-on-OpenPose]([https://github.com/ildoonet/tf-pose-estimation](https://github.com/LZQthePlane/Online-Realtime-Action-Recognition-based-on-OpenPose)
 - This project was last commited on 2019. I made modifications to make it fit the newer version of many packages (e.g., TensorFlow 2.0 or higher).

------
## Introduction
*The **pipline** of this work is:*   
 - Realtime pose estimation by [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose);   
 - Online human tracking for multi-people scenario by [DeepSort algorithm](https://github.com/nwojke/deep_sortv);   
 - Action recognition with DNN for each person based on single framewise joints detected from Openpose.


------
## Dependencies
 - python >= 3.5
 - Opencv >= 3.4.1   
 - sklearn
 - tensorflow & keras
 - numpy & scipy 
 - pathlib
 
 
------
## Usage
 - Download the openpose VGG tf-model with command line `./download.sh`(/Pose/graph_models/VGG_origin), and place it under the corresponding folder; 
 - Run `python main.py`, the program will **start the webcam** and recognize person as well as action. 
 - Put video in the same folder and run `python main.py --video=<video_path>` to start recognition on videos.
 - Choose different openpose pretrained model in script by modifying `estimator = load_pretrain_model(<model_name>)` in `main.py`:    
 **VGG_origin**: training with the VGG net, as same as the CMU providing caffemodel, more accurate but slower, **mobilenet_thin**:  training with the Mobilenet, much smaller than the origin VGG, faster but less accurate.   
 **However, Please note that the Action Dataset in this repo is collected along with the** ***VGG model*** **running**.




-------
## Reason to choose this resource
 - 1. This project tackles both 2 questions: Person Re-Identification and Action Recognition. Some resources only focus on one of them. Comparing with traditional trackers like FairMOT or DeepSORT, this project only detects human movements not other objects, but it adds action recognition and especially recognize falling therefore very useful for safty surveillance. The performance may be not satisfying, but it's computationally cheap.
 - 2. This project directly tests the performances on real-time videos by using cv2. Many other projects only support recorded videos or images.
 - 3. There are 2 pre-trained models existing and we can even add more.
 - 4. A drawback is that the action recognition is frame-wise, so some movements can't be accurately recognized. It might be more appropriate to call it pose recognition.



-------
## Results example
![](https://github.com/sundy1994/sundy1994-Realtime-Person-Re-Id-and-Action-Recognition/blob/main/test_out.gif)
