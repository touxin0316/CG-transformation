# CG-transformation
1.	Basic Matrix

   * Transition matrix
 
     ![image](https://user-images.githubusercontent.com/67257073/166504536-bbf1b81e-5696-4eb6-b834-6db7830536f4.png)
      
      Dx, dy, dz為model 的translation
      
   * Rotation matrix

      i.	RX
      
      ![image](https://user-images.githubusercontent.com/67257073/166504552-198fdc91-1e82-408f-a194-676f23d15fcc.png)

      ii.	RY
      
      ![image](https://user-images.githubusercontent.com/67257073/166504618-b961f605-c8d2-457e-ab01-70258300c177.png)
      
      iii.	RZ
      
      ![image](https://user-images.githubusercontent.com/67257073/166504713-cc11471a-6688-4963-a7c3-0591079b0fe0.png)

      ![image](https://user-images.githubusercontent.com/67257073/166504806-0110acc0-e32a-4c9c-ae16-56d810f878a8.png)
      
      theta為model 的rotation角度，需要將其先轉換成角度
 
   * Scaling matrix
   
      ![image](https://user-images.githubusercontent.com/67257073/166504873-1793a692-55e6-47c7-a50d-8f275c517360.png)

      Dx, dy, dz為model 的translation
      
   * View matrix
   
      相似於glu look at
      
      根據相機的角度賦值:
      
      ![image](https://user-images.githubusercontent.com/67257073/166504974-c545f414-1265-4898-a0a0-54b876fd1500.png)

   * Projection matrix
   
      i.	Orthogonal
      
      ![image](https://user-images.githubusercontent.com/67257073/166505115-45340286-9761-46ff-80a0-ae03be8d8653.png)

      ii.	Perspective
      
      ![image](https://user-images.githubusercontent.com/67257073/166505143-6c60fae2-f881-4af5-8722-00fedbdff112.png)
 
  **Final MVP matrix : 將所有得到的matrix相乘，並把row major轉成column major**
  
  ![image](https://user-images.githubusercontent.com/67257073/166505530-d29f9b32-9ac4-41e4-90db-37f1f4a0dbaf.png)

 
2.	Changing between wireframe and solid mode

使用glPolygonMode 函數

![image](https://user-images.githubusercontent.com/67257073/166505567-23b499a5-7bbc-4a8d-9eb1-d4ea3b036292.png)

因為地板不受wireframe的影響，所以在drawplane()之前需要再把polygon mode切回fill mode

3.	Keyboard control

    * Z/X : 切換不同的model
    
    * W : 切換wireframe以及solid mode
    
    * I : 印出所有matrix的資訊
    
    * O/P : 分別切換至orthogon al projection 和 perspective projection
    
    * T/S/R : 切換至transition / scaling / rotation mode
    
    * E/C/U : 切換至translate eye position mode / translate viewing center position mode / translate camera up vector position mode
    
4.	Mouse control

    * 按下右鍵，mouse press == true
     
    * 滾輪控制更新model的position / rotation / scaling或相機的z位置資訊
    
    * 根據滑鼠的移動位置與原先位置的變化去更新model的position / rotation / scaling或相機的x y位置資訊
 
5.	Draw plane

    畫平面一樣需要MVP matrix，但因為不需要隨著model移動而移動，不需要乘M matrix
    
    使用drawarray根據給定的頂點座標畫出平面
    
6.	Change window size

    縮放會依當下的project模式跟winow width / height (aspect ratio)是否大於一對projection matrix進行調整 
    
    ![image](https://user-images.githubusercontent.com/67257073/166505870-f6bb0d07-4e62-4498-9767-1280a165c392.png)

