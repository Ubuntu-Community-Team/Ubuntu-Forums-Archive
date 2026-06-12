---
title: "can someone access my mac via linux?"
date: 2006-07-16
forum: Server Platforms
---

### Post by macgig on 2006-07-16
I have two physical hard drives... one osx, the other ubuntu... 

question: 

if somehow someone gained access to my linux account/area, could they get to my mac osx stuff? 

if yes, how do I prevent this? thanks. :)

---

### Post by bluecherry on 2006-07-16
1. If someone has access to your linux install with a normal user account you can prevent them from accessing the other drive by removing the drive's entry in the /etc/fstab file.

This way it will not be mounted on boot and the user will not be able to manually mount it.

To mount it from your own account you would have to do this as root (or using sudo) as this is a system-wide setting.

2. If someone hacks into your linux install he will probably go for the root account and he will be able to manually mount any device. The entries in the fstab file won't matter anymore.

Hope this helped,

---

### Post by aysiu on 2006-07-16
Anyone has physical access to your computer has access to everything. Everything.

---

### Post by MrHorus on 2006-07-17
> **bluecherry said:**
> 1. If someone has access to your linux install with a normal user account you can prevent them from accessing the other drive by removing the drive's entry in the /etc/fstab file.

This way it will not be mounted on boot and the user will not be able to manually mount it.


It won't be mounted but if the user can run sudo then there is nothing stopping them from running a mount command and gaining access to the device.

---

