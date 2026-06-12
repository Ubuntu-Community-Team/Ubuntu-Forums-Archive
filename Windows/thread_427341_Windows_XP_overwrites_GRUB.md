---
title: "Windows XP overwrites GRUB?"
date: 2007-04-29
forum: Windows
---

### Post by sndrspk on 2007-04-29
Hi all,

Since I expect this forum to contain Windows and Ubuntu dual users, I post this here. I apologise if it is not the most appropriate place.

I have a laptop that has Windows XP pre-installed on it (and unfortunately it has to stay there), but I managed to create separate partitions for Ubuntu, to make it a dual-boot machine. While working on Ubuntu I have no problem at all. Also, when selecting Windows everything works fine, except when I end my session and boot the laptop again. The laptop then gets into a small booting cycle, like it cannot find anything to boot and keeps on retrying. With the Ubuntu CD I can go to rescue mode, reinstall the GRUB boot loader, and fix everything.

I figure that Windows XP in some way overrides GRUB. 

Of course, this is not ideal. I don't want to go through this whole procedure, every time I ran windows. Is there anything I can do about this?

Thanks in advance.

---

### Post by karellen on 2007-04-29
did you install ubuntu after windows xp? from the alternate disk? it should ask you where to place GRUB. I always choose MBR and it boots windows perfectly afterwards

---

### Post by sndrspk on 2007-04-30
> **karellen said:**
> did you install ubuntu after windows xp? from the alternate disk? it should ask you where to place GRUB. I always choose MBR and it boots windows perfectly afterwards

Yes, Windows was on there first. It's a company laptop, with XP pre-installed.

I don't know what you mean with alternate disk. I installed it on a separate partition I made with the kubuntu cd.

GRUB asks me where to place it, and I choose MBR, because that's the only place where I don't get errors during install.

---

### Post by seshomaru samma on 2007-04-30
Do you mean to say that after everytime you run Windows it overwrites the MBR?

This is very unusuall.....

windows only writes to the MBR during installation
do you have some sort of autoamtic recovery option on that laptop?

---

### Post by sndrspk on 2007-04-30
> **seshomaru samma said:**
> Do you mean to say that after everytime you run Windows it overwrites the MBR?

Well, that's my little analysis. It just doesn't boot untill I reinstall grub. Indeed, after every time I run windows.

> do you have some sort of autoamtic recovery option on that laptop?

In Windows? Could be. It's a company laptop, and every time it boots Windows it starts to do some 'standard operations', like cleaning locations and standard-configure certain program options. Do you think that could cause the problem?

---

### Post by mrgeesbigcircus on 2007-05-01
> **sndrspk said:**
> Well, that's my little analysis. It just doesn't boot untill I reinstall grub. Indeed, after every time I run windows.



In Windows? Could be. It's a company laptop, and every time it boots Windows it starts to do some 'standard operations', like cleaning locations and standard-configure certain program options. Do you think that could cause the problem?

This could be the issue. When I used windows I had a recovery system which actually sat in the BIOS, and on evry boot it checked the MBR for changes and auto-repaired them. THANKS A LOT. :(

---

### Post by sndrspk on 2007-05-02
Crap, than that must be it... I was hoping for a solvable problem. :(

---

### Post by seshomaru samma on 2007-05-02
You might be able to disable it
From the little I know about XP if you go
Start>Run>msconfig
then in the last tab you can see all the applications that start on boot in Windows
if you can identify that programme you might be able to disable it

---

### Post by davin on 2007-05-03
if you first install xp then ubuntu then it not overwrites GRUB.

---

### Post by sndrspk on 2007-05-03
> **seshomaru samma said:**
> You might be able to disable it
From the little I know about XP if you go
Start>Run>msconfig
then in the last tab you can see all the applications that start on boot in Windows
if you can identify that programme you might be able to disable it

Thanks, I'll try that.

> **davin said:**
> if you first install xp then ubuntu then it not overwrites GRUB.

XP was first.

Sander

---

### Post by karobchip on 2007-05-04
I am having the same problem -- my setup is 

40 GB partition for XP
1 GB Linux Swap
140 GB partition for Linux

I installed Ubuntu first but left the 1st parition open for XP. Last weekend I installed XP, and as expected, it overwrote the MBR. No problem, I was expecting that and reinstalled grub. What I was not expecting.. is that after I shut down the laptop after being booted in XP, I have to reinstall grub every time. Very tiresome.

I have a Dell Inspiron 9400. 

Anyone else with a Dell having this issue?

---

### Post by tafsen on 2007-07-26
I have also this problem.  It's really anoying!

---

