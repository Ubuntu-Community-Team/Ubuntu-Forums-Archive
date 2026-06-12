---
title: "Ubuntu Server reboots while booting"
date: 2006-06-15
forum: Server Platforms
---

### Post by melado on 2006-06-15
Hi. First of all, sorry for my English, it's not the best :D

Digging in the hardware of my room, I found a motherboard Epox MVP4A and a CPU AMD K6-2 450AFX, so I decided to build a little server, just for fun. The CPU is underclocked at 300 Mhz.

I installed Ubuntu Dapper LTS 6.06 on this machine, and the installation went OK. The problem came when it rebooted for the first time. GRUB loaded fine, but when it started to load the selected option, the computer rebooted. It always reboots when loading Ubuntu :sad: 

The last two lines I get to see in the screen before it reboots are "savedefault" and "boot".

Any ideas? I'm totally lost :confused:

---

### Post by momorr on 2006-06-16
I'm have the exact same problem on 2 systems.  
MSI MB K6-3 400mhz with 256 ram
MSI MD K6-2 500mhz with 256 ram

Any help would be appreciated.:?:

---

### Post by melado on 2006-06-16
momorr, I think I caught the problem.

Just try booting with the installation CD and do the integrity check. My installation CD was corrupted, so I think that's the problem.

---

### Post by madelman on 2006-06-16
I have the same problem. After installing ubuntu server 6.06my machine keeps rebooting and cannot do anything. 

Yesterday I installed ubuntu desktop without problems and today I decided to install the server version, but it does not boot. I have reinstalled twice and nothing seems to work. Also I checked  integrity of the CD and got a successfully message that the CD was valid. 

Any ideas what to do in this case?

Thank you.

---

### Post by cpress on 2006-06-25
I get the same thing, I did the integrity check and it passed. Any clues?

---

### Post by houstonbofh on 2006-06-25
[QUOTE=melado]Hi. First of all, sorry for my English, it's not the best :D

Digging in the hardware of my room, I found a motherboard Epox MVP4A and a CPU AMD K6-2 450AFX, so I decided to build a little server, just for fun. The CPU is underclocked at 300 Mhz.

I installed Ubuntu Dapper LTS 6.06 on this machine, and the installation went OK. The problem came when it rebooted for the first time. GRUB loaded fine, but when it started to load the selected option, the computer rebooted. It always reboots when loading Ubuntu :sad: 

The last two lines I get to see in the screen before it reboots are "savedefault" and "boot".

Any ideas? I'm totally lost :confused:[/QUOTE]
At boot, jump into the Grub menu, and choose the 386 kernel.  Once you boot, edit the menu.list in Grub.

---

### Post by cpress on 2006-06-25
I think I can honestly say  that, that didnt even makes scense more less help..

---

### Post by cpress on 2006-06-25
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48266](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48266)

will show you how to fix it.

---

### Post by ahobbs on 2006-06-26
I had the same problem with the Server Install CD.  Use the **Alternate Install CD** instead of the Server Install CD and build your packages from scratch...

---

