---
title: "couple more problems"
date: 2008-08-30
forum: Virtualisation
---

### Post by Friendly_hazard on 2008-08-30
it isnt detecting my external hard drives. Last time i installed ubuntu, i stumbled across an option to have them on my desktop but i dont remember what i did

Also EnvyNG does not appear to be working. i installed it and ran it and restarted but now it is stuck in low resolution.
it also says it can't detect video card/screen.

---

### Post by overdrank on 2008-08-30
> **Friendly_hazard said:**
> it isnt detecting my external hard drives. Last time i installed ubuntu, i stumbled across an option to have them on my desktop but i dont remember what i did

Also EnvyNG does not appear to be working. i installed it and ran it and restarted but now it is stuck in low resolution.
it also says it can't detect video card/screen.

Hi and what is the model of the graphics card? I am assume you are using Hardy 8.04?

---

### Post by sayakb on 2008-08-30
Do:
```
sudo fdisk -l
```
Note down the /dev/sdb(x) for the removable HDD. Now, do:
```
sudo mkdir /media/disk
sudo /dev/sdb1 /media/disk
```
Assuming the drive is /dev/sdb1

---

### Post by sayakb on 2008-08-30
And yes, 
> It is advised to use a descriptive topic title

---

### Post by Friendly_hazard on 2008-08-30
thanks i fixed the HDD problem

overdrank: Nvidia geforce 8 series with an acer lcd monitor

i guess i should also mention im on XP using VMware to run ubuntu. Also this problem happened after i used EnvyNG

---

### Post by overdrank on 2008-08-30
> **Friendly_hazard said:**
> thanks i fixed the HDD problem

overdrank: Nvidia geforce 8 series with an acer lcd monitor

i guess i should also mention im on XP using VMware to run ubuntu. Also this problem happened after i used EnvyNG

Hi and I believe that VMware can not support 3d. I will move to Virtualization  :)

---

### Post by Friendly_hazard on 2008-08-31
any advice?

---

### Post by Friendly_hazard on 2008-09-01
its still on low resolution :confused::confused:

---

