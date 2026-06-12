---
title: "HP Webcam doesnt work in VirtualBox Windows XP"
date: 2009-07-12
forum: Virtualisation
---

### Post by countryjake on 2009-07-12
I cannot seem to get my webcam to work on windows xp on virtualbox 3.0.2 on ubuntu 9.04. The webcam works fine with ubuntu, and when i go to devices and then usb devices, it shows the webcam, but it is grayed out and i cannot check the box. I added it to the usb filter list and checked it off, then rebooted xp on virtualbox and it still did not work.
when running the old version of virtualbox, the webcam didnt even show up at all under devices, so i figure I am getting a little bit closer but still not sure how to get it to run.

EDIT: SOLVED, just had to add myself to vboxusers. sorry for wasting anyone's time.

---

### Post by countryjake on 2009-07-12
ok i believe i have discovered the source of the problem: i need to disconnect the webcam from ubuntu before i can connect it to windows. can someone please tell me how to do this? here is my output from lsusb
Bus 002 Device 002: ID 064e:a110 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Suyin Corp. is the webcam.

---

### Post by Elep.Repu on 2009-08-26
I am interested in this as well.

---

### Post by countryjake on 2009-08-26
I actually have figured it out Elep.Repu
I have an hp dv9812us, part of the dv9700 series i believe, and i have every aspect of this computer working perfectly. If you are having issues with the webcam, make sure to add yourself to the group vboxusers with this command:

sudo usermod -a -G vboxusers username

where username is your username obviously. next, before you start the virtual machine, go to settings, click USB on the left, and press Add Filter from Device on the left, and press on Suyin HP Webcam. if you do not want it to load on start up, unclick the checkmark after you have added the filter to the list.
If, after you start it up, you want to use the webcam, click the Devices tab up top, go to USB Devices, and click the checkmark next to the webcam.

Now it should work!

---

### Post by yakupm on 2010-02-13
> **countryjake said:**
>  
sudo usermod -a -G vboxusers username

Now it should work!

 Worked perfectly for me, countryjake.  Thanks!

---

### Post by fatriff on 2011-03-21
Wow, you spent a month and a half working it out?

---

### Post by countryjake on 2011-07-14
no, i figured it out in a day if you look at the post i LAST EDITED it later that day... i posted the fix for it later as requested. please dont bash for no reason thanks.

---

