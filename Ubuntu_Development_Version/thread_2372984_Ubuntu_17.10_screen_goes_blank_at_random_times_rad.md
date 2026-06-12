---
title: "Ubuntu 17.10 screen goes blank at random times radeon card"
date: 2017-10-01
forum: Ubuntu Development Version
---

### Post by wildmanne39 on 2017-10-01
Hi, does any one know how to fix the issue of the screen going blank at random times with a radeon 6 card? this issue also effects 16.04 and above, I was hoping it would be fixed in this release. I am using the proprietary driver. I am using gnome 3.26 and this happens using ubuntu or ubuntu with x.org.

Thanks

---

### Post by cariboo on 2017-10-01
I have the same problem here, using an Nvidia GT-218 and a Samsung 32" TV via HDMI. It seems to me that the problem happens when some audio files are played.

---

### Post by wildmanne39 on 2017-10-01
Thanks for the reply cariboo! I am going to report it as a bug and see if I can find a work-around.

---

### Post by Trenchbroom on 2017-10-19
The Radeon R6 graphics card in my laptop has been preventing me from running Ubuntu (screen goes black after a while) and I do not see where the card is supported in the newer [AMDGPU-PRO]("https://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver–Release-Notes.aspx") compatibility list.  Hopefully there will be an update to the drivers soon.

---

### Post by wildmanne39 on 2017-10-19
It is working good with 17.10, I chose Ubuntu with x.org at the login screen, I did not activate or install additional drivers Ubuntu did that for me, when upgrading it says the firmware may be missing but if you install it the screen will go blank.  I am just having a little keyboard issue but it is usable at the moment.

---

### Post by ventrical on 2017-10-19
This is an across the board problem with intel and nVidia  graphics. on wayland and xorg. I think it is a serious security problem.

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.2.2 Direct Render: Yes

```


regards..

---

### Post by wildmanne39 on 2017-10-19
It is now fixed for me in 17.10.

---

### Post by cariboo on 2017-10-20
Closed, as the problem has be resolved, and Artful has been released.

---

