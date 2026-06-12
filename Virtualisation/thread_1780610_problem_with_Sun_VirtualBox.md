---
title: "problem_with_Sun_VirtualBox"
date: 2011-06-12
forum: Virtualisation
---

### Post by shehpar on 2011-06-12
hi all

I have a problem with screen resolution of my virtual OS (Ubuntu 10.2) which i have installed in Sun VirtualBox version 3.1.6 r59338. It is pre set to 800 * 600 screen resolution, which wont change to my desired 1024 * 768. Earlier when i installed Ubuntu 6.06 there was no such problem neither with other window xp installed in vBox. Can somebody help me out of it or can somebody tell me whats the reason for it.

hoping for help,

regards,

complete description of my environment and machine is as following:



i use Sun VirtualBox version 3.1.6 r59338 wherein i have installed Ubuntu 10.2

parent window discription is: Microsoft Windows Version 5.1 (Build 2600.xpsp_sp2_rtm.040803-2158: Service Pack2)

Monitor discription is: IIYAMA MF-8617E/T VisionMaster

Main board: intel 915 chip type: Intel(R) 82915G/GV/910GL Express Chipset

---

### Post by Joe of loath on 2011-06-12
You need to have the guest additions installed, otherwise a max of only 800x600 is available.

Also, your Windows XP host is out of date; you need to install SP3, because there are no longer any security fixes for SP2. You might want to virus scan yourself, in case you're part of a botnet ;)

---

### Post by shehpar on 2011-06-14
hey joe,
since i am new to ubuntu can u do me another favor....? please tell me how and from where to install this guest addition?
 
regards,

---

### Post by DDDmatrix on 2011-06-14
Open terminal in your Ubuntu guest, type this command: 
sudo apt-get update 
sudo apt-get install **virtualbox-ose-guest-utils**

**may be**, you also need these packages before installing virtualbox addition:

sudo apt-get install **build-essential**
sudo apt-get install **linux-headers-generic**

---

