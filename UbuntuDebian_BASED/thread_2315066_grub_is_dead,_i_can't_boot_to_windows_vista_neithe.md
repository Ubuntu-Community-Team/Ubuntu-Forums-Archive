---
title: "grub is dead, i can't boot to windows vista neither linux"
date: 2016-02-25
forum: Ubuntu/Debian BASED
---

### Post by lostvaldivia on 2016-02-25
grub is dead, i can't boot to windows vista. I can only enter with live cd linux.
I deleted the partition containing Linux and now I can not boot to windows, I erased the linux partition and installed kali linux but failed to install GRUB. I used a live cd with Boot Repair Disk did not work. I need help, thank you very much.

[http://paste.ubuntu.com/15203091/](http://paste.ubuntu.com/15203091/)

---

### Post by yancek on 2016-02-25
You deleted the partition on which you had almost all the boot files, the Ubuntu partition.  That's why you can't boot.  You don't have a bootloader installed and when you installed Kali you failed to install the Grub bootloader so there is no way to boot anything.  What exactly do you want to do? 
If you want to just have windows, you will likely need the installation DVD for vista to put its bootloader in the MBR.  If you want some Linux installed, I would suggest you do a little searching to find something other than Kali.  Kali is a terrible choice for a new user of Linux and certainly was not  designed to run as a Desktop computer.  It is specifically designed for  experienced users for use in computer forensics and states that on  their home page.

---

### Post by lostvaldivia on 2016-02-26
i want to recovery the dual boot. 
I tried with kali (usb) because it is a .iso what i have dowloaded and I used Kali because it worked previously. 
I tried with windows vista repair (Win can not repair the problem as typical), i tried with dvd of xubuntu (a old release what i found in a cd), also tried with a light iso of linux and then tried to download a linux mint or ubuntu but the connection is too slow  so it will take a long time to download.

---

### Post by howefield on 2016-02-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

