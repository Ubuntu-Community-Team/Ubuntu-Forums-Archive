---
title: "Best way to transfer windows to a Virtual Environment"
date: 2013-12-21
forum: Virtualisation
---

### Post by Ski_HolmaNM on 2013-12-21
I currently have ubuntu in a dual boot with windows. I need some windows programs that are wine incompatible. I do not want to do some small tasks in windows, save, go to ubuntu, come back to windows, and continue this cycle. I want to know if I can transfer my current windows os into a virtual environment, data and all, then wipe the windows partition from my hard disc. My computer has a core i3 processor, a 500 Gb Hard drive, and 7.7 Gb Ram.
*If at all possible, the Virtual Environment should be free.

---

### Post by Bucky Ball on 2013-12-21
*Thread moved to **Virtualisation**.*

Welcome. Install Virtualbox (it's in the repositories), create a virtual machine, install Windows in it from the Windows install disk. You're done.

You are going to need to do more detailed research re. virtual machines and installing OSs in them, etc., obviously, but that's the basic plan. 

I advise you install Virtualbox for a start and start having a look about then work from there. Pretty straightforward. You install Win in there just like you would install Win anywhere else.

An important thing to keep in mind: You need adequate RAM to run a virtual machine as you are effectively running two OSs at the same time and they need to share what is available (2Gb for Ubuntu, 2Gb for Win if you have 4Gb physical RAM that is).

Your specs look fine. Jump in. ;)
> 
*If at all possible, the Virtual Environment should be free. 

Don't understand that bit.

---

### Post by coldraven on 2013-12-22
It's better to download Virtualbox from their web-site, the version in the Software Centre is usually several versions out of date.
[https://www.virtualbox.org/](https://www.virtualbox.org/)

You don't mention what version of Windows you have, I only know how to make a VM of XP.
You need to have an install disc with a serial number.
If you only have an OEM version of Windows it can be done but is a bit technical.

---

