---
title: "Blank screen after install ubuntu 12.10 Beta 2"
date: 2012-10-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Penguin360 on 2012-10-03
I installed Ubuntu 12.10 Beta 2 this morning, but got a blank screen after the installation and reboot. Please see the attached screen shot.

Any help will be highly appreciated.

---

### Post by Penguin360 on 2012-10-03
Anyone please?

---

### Post by thotz on 2012-10-03
Is this also happening with the current daily dvd image?

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by Penguin360 on 2012-10-03
I haven't tried yet, but I did update the system after the install by doing Ctrl+Alt+F2 to log into the terminal and running apt-get update and upgrade. The update does not help. I assume the update is the same as the daily image?

---

### Post by ventrical on 2012-10-03
In terminal you can try:

sudo apt-get install ubuntu-desktop

---

### Post by ventrical on 2012-10-03
What are the specs of your PC?

---

### Post by Penguin360 on 2012-10-04
apt-get install ubuntu-desktop tells me I already have the latest ubuntu desktop.

here are the specs:

CPU: Pentinum 4 2.8GHz
RAM: 2GB
Graphic card: NVIDIA GeForce4 4000 64MB RAM

Thanks in advance.

---

### Post by Penguin360 on 2012-10-04
I think the problem is caused by a bad video card. I am going to see if I can change the video card and try again.

---

### Post by Penguin360 on 2012-10-04
OK, I gave up on that old pc because I could not find a video card to replace the current one. Got a different and better pc to test 12.10. Now it is working.

---

### Post by ventrical on 2012-10-05
> **CodingBeaver said:**
> apt-get install ubuntu-desktop tells me I already have the latest ubuntu desktop.

here are the specs:

CPU: Pentinum 4 2.8GHz
RAM: 2GB
Graphic card: NVIDIA GeForce4 4000 64MB RAM

Thanks in advance.

You can try and use =nomodeset during your installation but 12.10 will not work with that  graphics card... perhaps llvmpipe.. which is just awful. (or definetly try xubuntu or kubuntu. Kubuntu  will revive and find good use for older graphics cards and the old P4s. I have a quantal install of Kubuntu that  is just great on an old nVidia.

---

### Post by ventrical on 2012-10-05
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
ventrical@ventrical-desktop:~$ 


kubuntu+ above video card = working compiz (no llvmpipe)

---

### Post by ventrical on 2012-10-05
Here :

[http://www.youtube.com/watch?v=59Vlc0HtP_g&feature=youtu.be](http://www.youtube.com/watch?v=59Vlc0HtP_g&feature=youtu.be)

---

