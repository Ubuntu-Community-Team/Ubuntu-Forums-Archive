---
title: "Error booting Ubuntu installing in VirtualBox"
date: 2010-11-18
forum: Virtualisation
---

### Post by Manini on 2010-11-18
hey,
m havin a problen installing ubantu 9.04 on virtualbox . whenever i click on start the following error occurs 
after gateway IP
TFTP.
PXE -TO1 : File not found
PXE -E3B TFTP Error file not found
PXE M0F :Exiting entel PXE ROM
FATAL : could not read from the boot medium ! system halted.
m not able to figure out where m going wrong 
Plz kindly help

---

### Post by CharlesA on 2010-11-18
It's trying to boot off the network. How did you install Ubuntu on it?

---

### Post by Manini on 2010-11-18
i could not install ubantu yet , i just configured ORACLE VM Virtual Box
i was trying to install it from a CD .

---

### Post by CharlesA on 2010-11-18
Ah. You need to mount the cd in order to boot off of it.

Check out the user manual for info on how to create and use virtual machines: [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by Manini on 2010-11-19
thanks a lot. the manual realy helped to intall it corectly.:p

---

