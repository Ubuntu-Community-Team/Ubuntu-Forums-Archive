---
title: "cam was not working in install on 12.04 like in 11.x."
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by irv on 2011-12-05
I notice that the cam was not found in the install when asking for setting up an Icon for login. This feature worked in 11.x but not in 12.04. I am not sure this is a bug, or something that will work in the finial release. In other words it might be shut off in early Alpha/Beta releases.

---

### Post by coffeecat on 2011-12-05
To be honest, I wasn't paying much attention during that phase of the installation, but I've just installed cheese in this 12.04 system on my Vaio laptop, and I don't see an image. The light by the webcam comes on with cheese open, but the cheese window is simply black where the image should be. It was working in Oneiric and earlier Ubuntu releases. Output of lsusb shows:

```
Bus 001 Device 002: ID 05ca:18b3 Ricoh Co., Ltd Sony Vaio Integrated Webcam
```

---

### Post by irv on 2011-12-05
> **coffeecat said:**
> To be honest, I wasn't paying much attention during that phase of the installation, but I've just installed cheese in this 12.04 system on my Vaio laptop, and I don't see an image. The light by the webcam comes on with cheese open, but the cheese window is simply black where the image should be. It was working in Oneiric and earlier Ubuntu releases. Output of lsusb shows:

```
Bus 001 Device 002: ID 05ca:18b3 Ricoh Co., Ltd Sony Vaio Integrated Webcam
```

You are right I installed chesse, and I get a black screen also with the cam light on.
Output from lsusb
```
Bus 001 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
```
[ATTACH]208600[/ATTACH]

---

### Post by loneowais on 2011-12-06
Same here. This is most probably because of the switch from ia32lib to ia32lib-multiarch.

Hopefully, new libs will be uploaded soon and this will start to work again.

---

### Post by matt_symes on 2011-12-06
There was a bug raised on this in Launchpad for web cams not working at the moment. 

My webcam is also not working.

Apparently there is a fix on the way.

I will try to find the bug report

EDIT:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/899165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/899165)

---

### Post by irv on 2011-12-10
As of today 12/10 @ 12pm CST the Cam is working again. I checked it in Cheese. The bug must have been fixed with the last update.

---

### Post by Bowmore on 2011-12-10
This was solved by the kernel upgrade to 3.2.0-3.9.
The problem was that the pixel format was wrong, in my case YV12 instead of YUYV.

---

### Post by irv on 2011-12-10
> **Bowmore said:**
> This was solved by the kernel upgrade to 3.2.0-3.9.
The problem was that the pixel format was wrong, in my case YV12 instead of YUYV.

Thanks for the info.

---

### Post by xyzzyman on 2011-12-10
> **Bowmore said:**
> This was solved by the kernel upgrade to 3.2.0-3.9.
The problem was that the pixel format was wrong, in my case YV12 instead of YUYV.

Awesome! Which would explain why my suyin based Acer Crystal Eye webcam was doing that with the 3.2 kernels on my Oneiric install. A few weeks ago I even tried updating some of cheese's dependencies but wound up just using my really tweaked 3.0 series kernel. Compiling 3.2.0.4-10 for my system from [https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-4.10](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-4.10) as we speak and in about 15 minutes we'll see. *crosses fingers*

---

### Post by irv on 2012-01-17
This problem is back in 12.04. Cheese will not find the cam again. Did something change in the kernel again?

---

### Post by Stovey on 2012-01-17
I tried installing 12.04 over the weekend, and it wouldn't take my photo.  And then the installation failed later in the process, so I installed 11.10 instead. (mind you I was installing the Alpha 1).

---

### Post by irv on 2012-01-17
> **Stovey said:**
> I tried installing 12.04 over the weekend, and it wouldn't take my photo.  And then the installation failed later in the process, so I installed 11.10 instead. (mind you I was installing the Alpha 1).

Alpha 1 is out for bug testing and that is what I have been doing since early December. This also is the part of the forum that deals with problems and discussion on what is going on in 12.04.

---

### Post by irv on 2012-01-17
OK, I did and update and upgrade again this morning and did a restart and the cam is back working again. I should have did this before posting and verified that it was not working. I know how things change during developing.

---

