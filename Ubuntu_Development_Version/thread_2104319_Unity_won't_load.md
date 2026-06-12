---
title: "Unity won't load"
date: 2013-01-12
forum: Ubuntu Development Version
---

### Post by rahuman on 2013-01-12
Hi,

I installed Kernel 3.8.2 successfully but unity-launcher failed to load and glx (It crashed) didn't compile for my system during the kernel installation. I am able to load back to 3.5. 

My VGA card is a legacy, Mobility Radeon HD 4300 Series. so i installed the drivers

I am on Ubuntu x64 12.10.

Sorry if this is a wrong place to post. but I searched up and low and landed here.

Thanks in Advance.

---

### Post by cariboo on 2013-01-12
Moved to a thread of it's own, as it has nothing to do with the 3.7 kernel.

@rahuman, make sure you have the kernel headers package installed, and reinstall your grpahics drivers.

---

### Post by rahuman on 2013-01-12
> **cariboo907 said:**
> Moved to a thread of it's own, as it has nothing to do with the 3.7 kernel.

@rahuman, make sure you have the kernel headers package installed, and reinstall your grpahics drivers.

Thanks, for the move and reply.

Let me try that and come back to you

---

### Post by rahuman on 2013-01-13
Hi, cariboo907.
Thank you for your previous suggestion. I just tried running this command after installing kernel 3.7.2 again.
> sudo apt-get install linux-headers-$(uname -r)
but the output was
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.7.2-030702-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Now i just tried purging the ATI Legacy Drivers as follows (These was the same steps I used to setup the drivers in the first place for kernel 3.5):
> [http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)
After the purge was complete, I did a reboot, it restored the system back to its former glory, Unity is running, and so is Compiz.
Under "About this computer", its says that my vga drivers are "Gallium 0.4 on AMD RV710".
but my grapics seems fine, I played a movie (Django Unchained (2012) :D) and its was running smooth. Do i need to change the driver for better performance? or should i leave it as it is.

rahuman@root:~$ glxgears
```
302 frames in 5.0 seconds = 60.232 FPS
300 frames in 5.0 seconds = 59.882 FPS
300 frames in 5.0 seconds = 59.891 FPS
300 frames in 5.0 seconds = 59.844 FPS

```

My Graphic card
> 02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4300 Series]

Thanks in Advance

---

### Post by rahuman on 2013-01-13
This is my output for "glxinfo"
> [http://pastebin.com/HzcxhPHj](http://pastebin.com/HzcxhPHj)

---

### Post by cariboo on 2013-01-13
If things are running to your satisfaction, why change anything. BTW I'm not an AMD/ATI fan, so I try to stay as far away as possible from those graphics adapters. :-D

---

### Post by grahammechanical on 2013-01-13
some information about this

> Under "About this computer", its says that my vga drivers are "Gallium 0.4 on AMD RV710".

Gallium is the video driver.

[http://en.wikipedia.org/wiki/Gallium3D]("http://en.wikipedia.org/wiki/Gallium3D")

"RV710" is the AMD code number for the the video adapter. I was also curious when I started seeing "Gallium 0.4 on NVA5."

In my case NVA5 is the Nvidia code number for my Nvidia GT210 video adapter. We are both using the open source Nouveau Driver. I think that Nouveau has improved considerably in the last couple of years. It is my preferred video driver.

Regards

---

### Post by rahuman on 2013-01-13
> **cariboo907 said:**
> If things are running to your satisfaction, why change anything. BTW I'm not an AMD/ATI fan, so I try to stay as far away as possible from those graphics adapters. :-D

Thanks, Cariboo. Also for the advise. ATI drivers are throwing me down a ditch (I heard AMD stopped update for some VGA adapters), never had that much of an issue when I was on my old thinkpad with a Nvidia Quadro inbuilt.

Anyway, the laptop i am currently on is about 2 years old, I am planning on getting a strong laptop with an Nvidia Card in it (GTX FTW!!! :D).

---

### Post by rahuman on 2013-01-13
> **grahammechanical said:**
> some information about this



Gallium is the video driver.

[http://en.wikipedia.org/wiki/Gallium3D]("http://en.wikipedia.org/wiki/Gallium3D")

"RV710" is the AMD code number for the the video adapter. I was also curious when I started seeing "Gallium 0.4 on NVA5."

In my case NVA5 is the Nvidia code number for my Nvidia GT210 video adapter. We are both using the open source Nouveau Driver. I think that Nouveau has improved considerably in the last couple of years. It is my preferred video driver.

Regards

Thanks for the info. I was wondering about that.

---

