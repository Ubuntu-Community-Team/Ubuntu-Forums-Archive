---
title: "vitual box 2.2 freezes"
date: 2009-04-13
forum: Virtualisation
---

### Post by Dai777 on 2009-04-13
Installed the new version of VB in hardy heron LTS but I can only get it to work if I've loged in to VB the first time. If I shut it down and then start it later on all I ge is a black screen where it has frozen. Any ideas why this is happening and how to solve it. For now gone back to previous version.

---

### Post by lime4x4 on 2009-04-18
i had the same problem in jaunty here is what i did to resolve it

in a terminal i removed virtualbox

sudo apt-get remove --purge virtualbox-2.2

then i deleted the .virtualbox folder in my home folder
then reinstalled virtualbox and restarted the computer
this is what worked for me

---

### Post by Dai777 on 2009-04-18
> **lime4x4 said:**
> i had the same problem in jaunty here is what i did to resolve it

in a terminal i removed virtualbox

sudo apt-get remove --purge virtualbox-2.2

then i deleted the .virtualbox folder in my home folder
then reinstalled virtualbox and restarted the computer
this is what worked for me

tried your suggestion then could not start virtual box as xml file was misssing.

---

### Post by lime4x4 on 2009-04-19
odd. When i reinstalled all i had to do was start virtualbox and have it point to where the virtual disks were located

---

### Post by Dai777 on 2009-04-21
> **lime4x4 said:**
> odd. When i reinstalled all i had to do was start virtualbox and have it point to where the virtual disks were located

that is what should happen but it's not. It should act like a brandnew install.

---

