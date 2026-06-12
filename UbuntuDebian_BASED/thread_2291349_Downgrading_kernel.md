---
title: "Downgrading kernel"
date: 2015-08-19
forum: Ubuntu/Debian BASED
---

### Post by sreejith4 on 2015-08-19
Hi All,

I am new to ubuntu.

for some reason, i have to downgrade from Linux 3.2.0-86-virtual to Linux 3.2.0-54-virtual.

i followed the followwing steps

 apt-cache search linux-image - find the images involved
 sudo apt-get install linux-image-extra-3.2.0-54-virtual linux-image-extra-3.2.0-54-virtual- install the necessary packages
 fgrep menuentry /boot/grub/grub.cfg - find the installed kernels
 vi 	 - edit the grub.config file
 make the changes as 
 "GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 3.2.0-54-virtual" 


 update-grub - update the grub
 reboot - reboot the server.
 uname -mrs -- find out the newly installed(dowgraded) kernel.


it did not wwork

please help if i am wrong


regards,
sreejith

---

