---
title: "Video Pass Through with 1 Video Card?"
date: 2015-03-13
forum: Virtualisation
---

### Post by marseille2 on 2015-03-13
I've been reading through virtualization posts trying to understand if I can ... or how ... get video pass through with only 1 video card.


I've been using Virtualbox ... and it's pretty good since I'm not a gamer, but I'd like better performance for 3D apps. So I'd like to try KVM or XEN, but don't know if my new machine can do it ... since I don't have 2 video cards. I do have AMD virtualization, can enable both it and IOMMU on the motherboard's bios, and have an extra sound card. But I have no onboard video. So until I get another, I only have one graphics card, that I've been using with OpenGL. 


Also... I did try to install proprietary drivers, but wound up with a black screen. I probably did something wrong, since I haven't used proprietary drivers since Ubuntu 8.10. I read a lot of help pages, and some things helped... but some just got me completely lost. Where should a virtualization beginner really start?


```
$ glxinfo | grep "direct rendering"
direct rendering: Yes
```


```
$ lspci
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]

```


----
SPECS:

AMD-FX8350
Asrock 970 Extreme4
Asus Radeon HD 6450
8 gigs RAM
UbuntuStudio 14.04

---

### Post by TheFu on 2015-03-14
Initial reply: You cannot.

Keep reading ... there appear to be options.

---

### Post by KillerKelvUK on 2015-03-14
My original thought was the same as TheFu's however I've just been reading a thread where a user has reporting working primary VGA passthrough... [http://ubuntuforums.org/showthread.php?t=2111175&p=13230187#post13230187](http://ubuntuforums.org/showthread.php?t=2111175&p=13230187#post13230187)

Keep us posted if you manage this.

---

### Post by TheFu on 2015-03-14
> **KillerKelvUK said:**
> My original thought was the same as TheFu's however I've just been reading a thread where a user has reporting working primary VGA passthrough... [http://ubuntuforums.org/showthread.php?t=2111175&p=13230187#post13230187](http://ubuntuforums.org/showthread.php?t=2111175&p=13230187#post13230187)

Keep us posted if you manage this.

So he 
* blacklisted the video card for the hostOS
* started the VM either by ssh or from a serial port connection?

I have a few headless servers (only power and network connected) ... perhaps ... 

BTW - happy Pi day!

---

### Post by redger on 2015-03-14
yes it is possible

the host runs headless and the single gfx card is passed through. On AMD hardware no patches required

not to be confused with passing integrated graphics through to a guest, which will not work... yet. Coming soon - see xen-gt and kvm-gt from Intel, which are still experimental but coming along  [http://lists.freedesktop.org/archives/intel-gfx/2014-December/056652.html]("http://lists.freedesktop.org/archives/intel-gfx/2014-December/056652.html")

---

### Post by marseille2 on 2015-03-14
Ok, Cool! This really clears up a lot of my own misunderstanding ... Now I get the reason for the mixed info, and see what's a reasonable next move. 

So incredibly interesting! Thank-you all very much:D

---

