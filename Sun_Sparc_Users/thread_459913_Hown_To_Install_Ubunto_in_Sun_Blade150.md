---
title: "Hown To Install Ubunto in Sun Blade150"
date: 2007-05-31
forum: Sun Sparc Users
---

### Post by palanca on 2007-05-31
good afternoon talves I nao wrote mine well questao.  I have a computer sun blade 150 and desire to install in it ubuntu in this computer. they sameone helps me where I can find step by step of this insatalation. Because I was to go in google and in I obtained to find

---

### Post by netztier on 2007-05-31
> **palanca said:**
> good afternoon talves I nao wrote mine well questao.  I have a computer sun blade 150 and desire to install in it ubuntu in this computer. they sameone helps me where I can find step by step of this insatalation. Because I was to go in google and in I obtained to find

Great, you've discovered google. Did you see that this forum has a **search** function, too? 

**[COLOR="Red"]A Forum is not an answer-my-question-machine[/COLOR]**, it's also a repository of accumulated knowledge. And yes, it has answers, and they can be found. There's many posts that tell you the basics about Sun systems:

[LIST]
[*]put the CD in the drive
[*]power-off the machine
[*]power-on the machine
[*]hit Stop-A on the Sun Keyboard
[*]type **boot cdrom** at the **ok>** prompt
[*]off you go, just like with the installation on a PC
[/LIST]

Sun Blades are notorious for DMA problems during install. You might have to add **ide=nodma** as option at the first prompt after the CD-ROM has started to boot. When you're asked to press <enter> to install, type **install ide=nodma** instead.

best regards

Marc

---

### Post by Lord_Vader on 2007-07-29
Thanks!!!! :)

---

### Post by jocumer on 2007-10-24
Hi! i have problem, a want install ubuntu 7.10  in sun blade 150, but i can't.

Allocate 8 Megs of memory at 0x40000000 for kernel
loaded kernel version 2.6.22
loading initial ramdisk (5844610 bytes at 0x4E002000 phys, 0x40C00000 virt)...
Memory Address not Aligned 
ok

a see on google but no my problem not fund.

bios version is:

release 4.6 version 5 create 2002/06/03 16:49
OBP 4.6.5 2002/06/03 17:13
POST 2.0.1 2001/08/23 16:50
OBDIAG 4.6.5 2002/06/03 16:50

tanks  for all.

---

### Post by jcastill on 2007-10-25
Is that OBP the latest for the Sunblade 150?

---

### Post by zanderred on 2007-10-25
> **palanca said:**
> good afternoon talves I nao wrote mine well questao.  I have a computer sun blade 150 and desire to install in it ubuntu in this computer. they sameone helps me where I can find step by step of this insatalation. Because I was to go in google and in I obtained to find

Hi, have a look at [http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1)
the only diffrerent thing is when the computer is first booting at the initializing memory press stop a before initializing stops, type boot cdrom (press return), :)and the key board is PC5 which should be auto detected (do-not change)
good luck.:)

---

