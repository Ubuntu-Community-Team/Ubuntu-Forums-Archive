---
title: "Error to Install Ubuntu Server in Dell Dimention 9100"
date: 2008-10-22
forum: Server Platforms
---

### Post by namkhai on 2008-10-22
Hi Erverybody, i have a Dell Dimension 9100 dual core 3Ghz, 8Gbyte RAM and 1 TB of hard disk and I have too 1 video card Gforce9600 512 Ram, I have presently Windows PRO and Ubuntu Desktop, I would like to install Ubuntu Server to use my 8Gb Ram, but I have problem to install in the step of install the services (DNS, SSH, LAMP) I have the error after this step, and when I try to restart with Ubuntu Server I have the error (please see the pic), if you have ideas, please letme know

Namkhai

---

### Post by prshah on 2008-10-22
> **namkhai said:**
>  8Gbyte RAM 
I have presently Windows PRO and Ubuntu Desktop,

Ubuntu Server to use my 8Gb Ram, but I have problem to install in the step 


a) Check the CD. (Burn at a lower speed?)
b) check the RAM. (The other installed OS's may not see/use all of the 8Gb RAM, and the fault may be present only on RAM over 3Gb). Just a guess.

---

### Post by linux_tech on 2008-10-22
Is your bios upgraded to most recent version?

---

### Post by ajwak95 on 2008-10-22
> **namkhai said:**
> Hi Erverybody, i have a Dell Dimension 9100 dual core 3Ghz, 8Gbyte RAM and 1 TB of hard disk and I have too 1 video card Gforce9600 512 Ram, I have presently Windows PRO and Ubuntu Desktop, I would like to install Ubuntu Server to use my 8Gb Ram, but I have problem to install in the step of install the services (DNS, SSH, LAMP) I have the error after this step, and when I try to restart with Ubuntu Server I have the error (please see the pic), if you have ideas, please letme know

Namkhai

Are you using 64-bit? If you can have more than 4 gigs (I believe), then it is 64 bit.

---

### Post by namkhai on 2008-10-22
Hi Everybody.. thank you for your advices. i change the memory, i put only 4GB, i tested with 2Gb too, i change the harddisk, i update the Bios with the last version, I changed the CD Too, juste  to mention that in this pc, I run presently Windows xp and Ubuntu Desktop too.. and the both run very good.. without problem….. I attach the step of my installation and the error

Thanks

Namkhai

---

### Post by lykwydchykyn on 2008-10-22
try not selecting anything at the second screen (you can run tasksel after install). I've found that some choices are mutually exclusive, but it doesn't tell you so (never liked tasksel much).

---

