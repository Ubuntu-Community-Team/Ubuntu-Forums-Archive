---
title: "Embedded Device Development questions"
date: 2015-04-05
forum: Ubuntu Application Development
---

### Post by amr rahmy on 2015-04-05
Hello, I had a few questions to ask about embedded device development and Would like some guidance on my next project. its a long post so bare with me.

Background:
I have been using Ubuntu Desktop as a user for a few years.
I have been using Ubuntu Server as an admin for a few years.
Can develop in C, C++, Java, PHP among other languages.
Have Developed Android and iOS apps.

Hardware(SBC (single board computer) not written in stone):
equivalent to Raspberry pi 2 model b or Odroid-C1 (something without a fan would be better)
CPU: ARMv7(with NEON) or ARMv8(also called AARCH64 i think)
RAM: 1-2GB
Camera (webcam)
Micro-controller (Cortex-M3)
Small Touch Screen
USB port
Ethernet port / Wifi
SDCard or MicroSDCard or the system image

Project Overview:
Commercial hardware/software solution similar to Security Camera Systems.
can interface with a manual webcam or camera, adjust settings, stream video, take snapshots or photos.
process images using OpenCV.
can interface through a network.
can interface with USB drive or connect to a Computer.

the question:
Can I use Ubuntu or Ubuntu Touch or Ubuntu Snappy as the basis of this system, add ROS framework or OpenCV and develop a full screen app that would start instead of the normal log-in and Ubuntu desktop?

I would like the system to boot with a background image.
Not see any Ubuntu related UI elements.
Start the app in full screen.
closing the app shuts down the system.

Is this possible with Ubuntu, is there anything wrong with choosing Ubuntu for this task instead of any other Linux distribution? or not starting with just a Linux kernel?
any getting started guides or suggestions are welcomed. And a development SDK/API or framework for ARM development on Linux is appreciated.

---

### Post by Eric_Fellip on 2015-04-06
Well, I would not know about Ubuntu being able to work on a ARMvX SBC, but I know that there are some Linux-based OS's out there that are specifically made to use with credit card-sized computers like Raspberry Pi. Look around, because if Ubuntu does not solve your problem, other OS will, that won't stop your project. :)

---

### Post by ian-weisser on 2015-04-06
CAN you use Ubuntu for this kind of project?  Sure.
SHOULD you use Ubuntu for this kind of project? Maybe, maybe not.

For real embedded development, look at Ubuntu snappy. It's both  small and easily updatable, with Ubuntu (not you) handling those  security updates. So your thousands of sold units will be updating  themselves regularly instead of sitting unpatched and vulnerable.

Ubuntu is designed to be a general-purpose OS. Substituting your own  single-purpose, proprietary GUI may require a lot of (perhaps  unnecessary) work. Reconsider your design - can the software work as an  application on a general-purpose system instead? Can an existing GUI be adapted to your needs? Those might be a lot  less development work, and a lot less expensive to create.

When you eliminate all Ubuntu branding, you run afoul of Canonical's terms for using Ubuntu - meaning you can't rely upon Ubuntu to provide security updates, bugfixes, distribution, update servers, time servers, etc. Canonical won't subsidize a non-revenue product that carries somebody else's brand. Building your proprietary software on top of Ubuntu will also expose you to Open Source license issues. You must abide by the terms of the open software you use, including making source code available. A partnership or other agreement with Canonical can resolve those problems.

---

### Post by amr rahmy on 2015-04-06
the premade ubuntu images for my development board
Ubuntu mininal (not sure if that's Ubuntu core or something else)
Ubuntu server
Lubuntu

these are the ones readily available for me. I would have liked Xubuntu, Ubuntu Desktop (unity or gnome) or Debian desktop instead of Lubuntu.
if i try to add Unity from the command line through apt-get, it breaks the Ubuntu image upon restart. the Ubuntu image is available on removable storage media (microSDCard and emmc) and I can munipilate the image if I knew what I was doing!!
there are more options and a better community at raspberry pi, but its not the development board I currently have.

the images uses U boot. I can download the kernel I think. don't exactly know where to go from there.

about the questions,
lets say I have lubuntu or Ubuntu snappy and I wanted to have a splash screen similar to elementary os or older ubuntu splash screens, and I wanted to go from kernal startup to the application without a login screen and go directly to a full screen application.

what is needed for me to learn? I want to hide the Uboot and kernel startup with a splash screen.
what tools and frameworks for the app? do I use ubuntu sdk? is it possible to create a full screen app using GTK or GTK2+, QT, what plugins for QT? any other options? html5 for the GUI? gnome interface? I know xbmc(xmbc?) is full screen.

---

### Post by amr rahmy on 2015-04-06
I am not sure what the OS will provide exactly or if its needed in this device. I know I will need a kernel.
I just need to be able to run c++ complied code for ARM.
I need to interface with camera(camera or webcam) and network (ipv4).
I need a GUI for a small color screen for menu and maintenance operations(few icons, one page deep).
I need the device to interface with USB drive.

If I am going with Ubuntu touch, I think that version has a splash screen with Ubuntu logo, which is fine, I will just need it to start up into the app that I made in full screen.

I don't mind putting Ubuntu logo at the first kernel boot up screen, but the device will not have a keyboard or mouse and I don't want it to be stuck at the log in screen or at the desktop screen.

---

