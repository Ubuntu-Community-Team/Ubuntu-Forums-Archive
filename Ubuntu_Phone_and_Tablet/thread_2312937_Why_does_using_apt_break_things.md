---
title: "Why does using apt break things?"
date: 2016-02-08
forum: Ubuntu Phone and Tablet
---

### Post by ZICODIAN on 2016-02-08
The new BQ M10 Ubuntu tablet has some promising features like running some X applications and providing [FONT=courier new]apt[/FONT] in a reliable way. Whenever I run [FONT=courier new]apt[/FONT] on my Aquaris E4.5, it usually works in a sensible way, but using it to upgrade things often results in the device entering a boot loop when it is rebooted -- necessitating a reflash of the system.

I understand that getting it working is work-in-progress, but does anyone have an explanation of why this tends to happen? Is there some obvious thing I could do that would make it less likely for [FONT=courier new]apt[/FONT] to break the system?

---

### Post by krusty8 on 2016-02-15
I can't really explain why it happens. Maybe simplest explanation is just that [FONT=courier new]apt upgrade[/FONT] is not a supported workflow, nobody is testing and fixing it. Maybe you could try to pinpoint the exact problem, by first checking what packages [FONT=courier new]apt upgrade[/FONT] wants to touch, then cancel it and instead do an [FONT=courier new]apt upgrade somepackagename[/FONT]. You can start with safe choices like language packs, check whether it still boots ok and thus step by step narrow it down until you find what breaks it. Then you could try apt pinning or something to exclude the problematic packages.

What I started doing for myself recently is just not do [FONT=courier new]apt upgrade[/FONT]. I still do [FONT=courier new]apt update[/FONT] and [FONT=courier new]apt install[/FONT], but for the system update I wait for the image to come along. I have little experience with this yet and I'm not sure what the problems with this approach will be.

Let us know if you find something out!

---

### Post by grahammechanical on 2016-02-15
> Maybe simplest explanation is just that [FONT=courier new]apt upgrade[/FONT] is not a supported workflow, nobody is testing and fixing it.

I would agree that explanation. I do not speak from experience of owning a Ubuntu phone but from reading about the technology. It is my understanding that the Ubuntu phone OS has transactional updates and apt-get is not used in this process. If we are not careful by using apt-get we take the OS off of the channel that is bringing the transactional or Over The Air (OTA) updates.

In future the Ubuntu phone and tablet OS will be based on Snappy Ubuntu Core where the kernel is a snap and the system is a snap and it will not be possible to use apt-get to update the OS.

Those x-applications that are shown running on a Ubuntu converged device are running in Linux container. And so are severely restricted as to access to the system. This is line with the security model. So, it may indeed be possible to run a terminal in one of these containers but we will not get very far with apt-get because of the security of the container. We certainly will not be able to upgrade the kernel or the OS.

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/)

See enabling read-write mode

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

> Recovering from read-write mode is possible but requires reinstalling the system from scratch.

Regards.

---

### Post by krusty8 on 2016-02-17
> **grahammechanical said:**
> 
Those x-applications that are shown running on a Ubuntu converged device are running in Linux container. And so are severely restricted as to access to the system. This is line with the security model. So, it may indeed be possible to run a terminal in one of these containers but we will not get very far with apt-get because of the security of the container. We certainly will not be able to upgrade the kernel or the OS.

Well, just to not scare off enthusiastic hackers too much - I think, right now most (some) of the X applications shown are *not* run in a container, nor is it *needed* to have a container. I understand that containers around X applications are part of Canonicals product strategy. I havent seen or used them, but it is indeed conceivable that this will restrict these X apps when installed from the store. But technically it is quite possible to use X applications in an unrestricted way. I have no problem getting root access in an xterm running on top of Xmir, or accessing all files in all folders, using apt, opening and editing any file I please in gedit. 

PS: Well, there are obviously some *usability* challenges to overcome when using X apps on a touchscreen, but what I'm saying is, you can well get by without a restricting *container*.

---

