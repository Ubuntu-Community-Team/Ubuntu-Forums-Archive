---
title: "Full USB Install"
date: 2017-01-06
forum: Virtualisation
---

### Post by schyken on 2017-01-06
I've been using Linux for over a year now, but I've never used Ubuntu as my daily driver. About a week ago, I decided to set it up into VirtualBox and use it as my main OS that way. With a bit of customization, I really liked it. 

I'm an experienced user but I'm still learning. My question is about installing the OS to a USB flash drive in order to boot from it wherever I am. I've installed OSs this way before with much success. 

So finally, with Ubuntu running from a USB flash drive 25MB/s write speed, will my performance be alright? I know I'll take a small hit, but I'm not too familiar with how intense Ubuntu is, especially with Unity.

---

### Post by howefield on 2017-01-06
Thread moved to the "*Virtualisation*" forum, probably a better fit.

---

### Post by sudodus on 2017-01-06
There are some tweaks, that you should consider, when running Ubuntu installed into a USB pendrive. Maybe the most important thing to do is to ***disconnect or unplug the internal drive*** before installing Ubuntu with the standard installer. Otherwise it wants to install the bootloader into the internal drive. This can be fixed in BIOS mode, but not in UEFI mode. And in general, it makes the installation easier and less risky.

See the following links and links from them.

[Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

-o-

A good alternative is a persistent live USB drive.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by ODTech on 2017-01-19
I would suggest rather using LXLE for this. It's based on ubuntu but much lighter.

---

### Post by C.S.Cameron on 2017-01-20
My wife switched from running Ubuntu from internal drive to 500GB external USB drive about five years ago.
When we travel she plugs it into a spare laptop, when we get home she plugs it into her desktop.
Nether has USB3.
I never hear her complain about speed or smoothness.

---

