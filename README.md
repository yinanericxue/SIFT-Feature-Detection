# SIFT Feature Detection

#### SIFT Introduction: Scale Invariant Feature Transform
#### https://medium.com/data-breach/introduction-to-sift-scale-invariant-feature-transform-65d7f3a72d40
#### https://www.analyticsvidhya.com/blog/2019/10/detailed-guide-powerful-sift-technique-image-matching-python/
#### https://www.geeksforgeeks.org/sift-interest-point-detector-using-python-opencv/

![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/e84b9f9f-7e89-41e6-bd83-0c1d590a90c3)

![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/4e108ca8-2c3f-4719-8865-800d7d6f4218)

#### Original Paper
#### https://www.cs.ubc.ca/~lowe/papers/ijcv04.pdf

#### Example Code
#### https://github.com/rmislam/PythonSIFT
#### https://medium.com/@russmislam/implementing-sift-in-python-a-complete-guide-part-1-306a99b50aa5
#### https://medium.com/@russmislam/implementing-sift-in-python-a-complete-guide-part-2-c4350274be2b

![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/fb3543a4-3458-4968-8ec8-2da10a13a659)

#### Use feature vectors from a image
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/c9c3799e-fa60-4af3-a97d-337dad930872)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/89e8a065-d7c5-4852-a928-e68ff93da930)

#### Generate feature vectors from a image
#### Step 1：Generate Base Image

#### Effect of Variance (sigma) at Gaussian Blur
#### https://stackoverflow.com/questions/23007064/effect-of-variance-sigma-at-gaussian-smoothing
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/26ecffca-345f-4372-a5d0-85878906b068)
#### The bigger the sigma in gaussian blurring, the more blurry the image in a kernel gets. Small sigma means the center of the curve is very sharp, which #### won't result in much blurring since the surrounding has no effect.

#### About Sigma
#### https://math.stackexchange.com/questions/3159846/what-is-the-resulting-sigma-after-applying-successive-gaussian-blur
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/1708d88b-a947-40a6-95a1-7a8c2a7515b0)

<img width="334" alt="Screen Shot 2023-12-21 at 8 28 52 PM" src="https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/facecd48-9988-4694-bf40-e765b8c305aa">

#### Step 2：Calculate the number of octaves![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/5ce8fa06-53ec-49a8-960c-1d09aa213c4e)

<img width="562" alt="Screen Shot 2023-12-21 at 8 29 25 PM" src="https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/84897442-7236-4beb-8f3b-8db4f3749e71">

![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/2961cba4-157e-463f-b170-ce4670045ce9)

#### Step 3：Calculate the sigmas for all layers in each Octave
#### Every gaussian pyramid = 8 groups (one group is one resize) and 6 stacks (every group has 6 different blurs)
#### n = 3 layers which participate the calculation in the DOG
<img width="859" alt="Screen Shot 2023-12-21 at 8 30 34 PM" src="https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/e0f82615-9794-4b43-9858-a6e01b75d494">
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/fb219bdd-daf8-482b-8194-23417f1d705a)

![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/47814179-2750-4ba3-9c5d-0bf137b46d7a)

#### Octave 0
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/8ac9db09-4077-4a77-8e8a-aac8db28409c)
#### Target_σ for each layer in the octave 0：
####  σ        σk        σKK      σKKK    σKKKK    σKKKKK
####  1.6     2.02    2.54     3.2        4.03       5.08

#### Source_σ ** 2 + Diff_σ ** 2 = Target_σ ** 2
####  σ      Diff = SQRT(T ** 2 - S ** 2)
#### [1.6, 1.22627, 1.54501, 1.94659, 2.45255, 3.09002]

#### Octave 1
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/14ae80e8-528e-402a-b62f-5a2b1da96de1

#### Step 4：Generate the Gaussian Pyramid
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/da183fc8-4026-4e5e-a89c-35666978a8de)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/92997198-f62c-4dfe-b0a6-a96a68911c24)

#### Step 5：Generate the DOG Pyramid
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/e27fea19-cabc-4a10-8cef-91dba6877491)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/e30492c2-8f9d-4410-9950-3965badd8f95)

#### Step 6：Find the extrema in the scale space
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/494ce81a-43c9-41c5-966d-d1c24102846a)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/20ad1708-a3a7-43ad-8437-270d17a58ea4)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/f5db3de9-4c62-4c79-b9f1-54f372ff4674)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/7e5046c5-17a9-467d-b98d-6147641ca736)
#### The histogram below plots the gradient magnitude / change of all dots in the square above.
#### If it's plotting only one dot, there's only one bar in this histogram.
#### If it's plotting 4 dots, there can be at most four.
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/f20b0e88-c038-4821-91b6-c2d8aecd0111)

#### Step 7：Rmove the duplicate keypoints

#### Step 8：Use the input image size

#### Step 9：Generate the feature vector for each key point
#### https://medium.com/data-breach/introduction-to-sift-scale-invariant-feature-transform-65d7f3a72d40#Keypoint%20descriptor
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/39896248-e1e6-48ab-a5ac-1ee4a72d794c)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/4f70bd2a-ddfb-431d-aacd-c09450f0d823)

#### 8 Directions x 2 x 2 = 32 values per key point:
#### 8 Directions x 4 x 4 = 128 values per key point:

#### The area surrounding one key point is a local property.
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/1282c3f6-0040-4f76-a7b7-af7112afd691)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/396097cf-3d6c-4cb0-9813-d34cb8d03fb7)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/d4c0d7df-790e-4b8c-90b9-9fec1fbd0353)

#### Taylor Expansion
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/2358c298-12dc-447b-adb8-dce8c443d791)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/ea107264-151f-41d4-8dd4-d912f562d570)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/044cc436-1a4e-49aa-a44e-ee7a0e0e98b8)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/b507f1e2-5c82-4ce0-8e56-bf65e8bac51b)


![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/82c4c290-9b63-4318-b713-67b1545d6cc0)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/e72cf7e6-58bf-4592-b327-e2c25211bcd8)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/0bff0876-3670-46f1-8547-136fa0a0e8f3)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/a903e140-555a-4ee0-ba56-d6b5bb9a1553)
![image](https://github.com/yinanericxue/SIFT-Feature-Detection/assets/102645083/48f82784-0dc0-4259-a472-73567c5d9c4a)

#### At (x,y,σ ):
