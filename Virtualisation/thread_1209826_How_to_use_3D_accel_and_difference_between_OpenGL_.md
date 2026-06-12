---
title: "How to use 3D accel and difference between OpenGL and Direct3.0"
date: 2009-07-10
forum: Virtualisation
---

### Post by razorboy5 on 2009-07-10
Hi

i recently learned that WINE does not support nProtect games (which i want to play) thus turning to virtualization for help

I read some forums that most of the virtual machines do not support 3D acceleration. Can anyone recommend which ones do?

also what's the difference between the OpenGL and Direct3.0 acceleration? Since i heard VMare supports Direct3.0 and VirtualBox supports OpenGL

---

### Post by Perryg on 2009-07-11
VirtualBox 3.0.2 does support OpenGL and DirectX 8/9 up to a fashion now.  Still in the experimental stage but others are reporting success.

---

### Post by ZeldaFan on 2009-07-12
How do you activate the 3D acceleration in a guest? Besides ticking the option in the settings of my guest, how do I enable 3D acceleration in my Windows Vista guest? It's still showing a score of 1.0 in the Windows Experience Index, which doesn't let me activate aero.

---

### Post by Perryg on 2009-07-12
Aero is not supported yet.  I know for a fact that it is on their to do list!  This is still considered as an experimental area for VirtualBox.  DriectX 8/9 support came out with release 3.0.x, but some games do in fact work as well as the OpenGL screen savers.

---

### Post by ZeldaFan on 2009-07-12
So how do you tell if directX 8/9 is enabled on your (vista) guest? Should I expect to boot up an older game (like CS?) and be able to play it relatively satisfactorily?

---

### Post by Perryg on 2009-07-12
Dxdiag will tell you what is running.  I don't know about specific games though sorry.  I don't play them :-(

Try and see what happens.  From what I read most of the older games work and some rather well. Some not so well.  Give them a few more revisions and I bet it will be fine.

---

### Post by ZeldaFan on 2009-08-05
Sorry for the delayed response, but dxdiag says that I have DirectX 10. However, while DirectDraw acceleration is enabled, DirectX 3D acceleration is not. I have 3D acceleration enabled in my virtualbox settings, so I'm not sure why this would be the case.

---

### Post by Cheesemill on 2009-08-06
I've heard that you have to be in safe mode whilst installing the Guest Additions to get 3D working properly.

---

