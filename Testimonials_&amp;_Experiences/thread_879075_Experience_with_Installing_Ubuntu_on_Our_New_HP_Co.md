---
title: "Experience with Installing Ubuntu on Our New HP Computer bought from Costco"
date: 2008-08-03
forum: Testimonials &amp; Experiences
---

### Post by margazhang on 2008-08-03
My wife and I bought a HP computer (a6457c-b with HP w2207h monitor) which came with Windows Vista pre-installed.

From our friend and coworker, Steve, we learned about the wonder of Ubuntu as we had some problems using Windows Vista - it did not support two of the Logitech webcams we have. So we played with installing Ubuntu and eventually get it worked - I am using it now to access this forum and post this very thread. Hope that our experience will help those who had problem installing Ubuntu on HP computers.

Anyway, I tried to install Ubuntu and learned that I have to download Ubuntu 8.0.4 for 64-bit PC (AMD64) as that is what our new HP computer belongs to. Downloading it and burning it onto CD had no problem. The problem I had was to install it.

First, we tried installing it by booting from the AMD64 Ubuntu CD. Because of an appears-to-be video problem, the installation got stuck somewhere. We even had problem running Ubuntu from the CD.

Then we tried installing it via VirtualBox, the same problem happened. from this point we sort of lost the hope that Ubuntu could even work on our HP machine. Then one day I tried running the Ubuntu CD from within Windows Vista and selected the second option to install Ubuntu as a Windows program.

As a precaution, I picked the second option after rebooting - I forgot its exact wording but it is something like "(select this if you have a display problem). It worked! I mean I could see all what displayed on the monitor, only the resolution was low (800x600) and everything looked pretty big but it was better than nothing!

After searching for ways to improve screen resolution, I found one on Launchpad website that worked for me:

[https://answers.launchpad.net/ubuntu/+question/32250](https://answers.launchpad.net/ubuntu/+question/32250)

For those who do not have a launchpad account, I post here the solution (question asked and answered by dh):

> I figured out how to install the proprietary NVIDIA GeForce 6150 LE driver and that solved the problem.

To install, go to System-->Administration-->Hardware Drivers

Ubuntu recognized that there was a new driver for my video card and downloaded the package and installed. After reboot, I was able to change the resolution of the screen by going to System-->Preferences-->Screen Resolution

Hope this helps some other newbie.

Mine says "NVIDIA accelerated graphic driver (latest cards)" now but before I picked to install it, it said something like 3D graphic which made me hesitant to install it in the first place.

Anyway, I am glad that I chose to install the latest card driver and now I can set our monitor's resolution settings to 1280x800-58Hz. Still not the recommended 1680x1050-60Hz (as suggested from the monitor prompt), but that is better than 800x600!

I just love Ubuntu. I tried installing Lindows/Linspire years ago but it was not good enough for me to make it as my primary OS. Now while my wife still uses Windows Vista, I use Ubuntu (Hardy Heron) - yes, we have dual boot. Cheers!

Now I would like to see if I can install Ubuntu on my Samsung Q1 (UMPC) and an old old computer (the latter does not have a workable CD-ROM). Anyone knows how to install Ubuntu without using a CD-ROM?

**Update:** I find this interesting thread "[How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528")" - going to try that when I have time :-)

OK, I have tried all kinds of tutorials for Windows and Linux for running Ubuntu on USB thumb drive. I picked two easiest approaches for me. Because of space, [I posted the two approaches here on my own blog]("http://gain4you.net/offline-tools/free-software-programs-running-on-a-free-operating-system-ubuntu/"). Hope it saves you many hours of testing :-)

---

### Post by Sef on 2008-08-03
Moved to Testimonials & Experiences.

---

### Post by armandh on 2008-08-04
I found I had to reduce the vista partition with a utility in vista. nothing, not gparted or parted magic would budge it.

then I installed selecting the "use unpartitioned space" option.

---

### Post by houseofmore on 2008-11-18
Any luck ever getting 1680x1050-60Hz to work?

---

### Post by armandh on 2008-11-18
I have had no problem getting any screen resolution that the monitor will report back, and the video card will produce. I have one monitor that the PnP function is broken. It gets 800x600 max unless I plug in a different monitor first.

---

### Post by margazhang on 2008-11-24
> **houseofmore said:**
> Any luck ever getting 1680x1050-60Hz to work?

Yes, I get the 1680x1050-60Hz working and I am using it right now!

---

