---
title: "Backup Devices"
date: 2012-07-30
forum: The Cafe
---

### Post by Lymphocyte on 2012-07-30
What kind of device do you store your backups on? I used to have a 500GB hard drive, but that failed and i now use 2 32GB flash drives formatted as ext4.

---

### Post by Roasted on 2012-07-30
I have a server running in my basement that does a whole array of things. Its primary tasks are for storing Motion feeds (video surveillance on my property) as well as being an ownCloud (personal Dropbox-like cloud) server, but I also have file server features enabled as well, which is what stores my backups.

Currently the data resides on a 2x500 RAID 1 mirror via mdadm software RAID. In time I plan to purchase four 2TB drives and do a RAID 5, but I'm a bit too poor to drop ~400 on hard drives right now... In time, maybe. ;)

For the super super important data, aka Pictures, I often do a new set of DVD-R backups on a monthly basis.

---

### Post by miegiel on 2012-07-30
> **Lymphocyte said:**
> What kind of device do you store your backups on? I used to have a 500GB hard drive, but that failed and i now use 2 32GB flash drives formatted as ext4.

Personally I just copy my stuff with sshfs to the machine that I's using as a firewall (it has plenty of spare room). But if I wouldn't have the spare disk space there, I'd use a 2.5" external laptop disk. The regular 3.5" disks are, in my not so humble opinion, useless for backups. They are made to sit inside desktop machines and don't like to be moved around a lot, especially not while spinning. While laptop disks are built to be used in motion and when not spinning, can survive some serious abuse (I forgot I had one in my backpack once and threw it to the corner of my room :D about 3m horizontal 1m vertical).

(3.5" disks in an immobile server is not a problem of course ;))

---

### Post by Lightstar on 2012-07-30
I use a 16gb flash drive / usb stick for my mother's backup.  She uses windows.  So I do it through MS SyncToy.  It works pretty well actually.

For myself.  I put mine on a 2TB drive I have for my media / movies / music / shows.   Currently using LuckyBackup on linux... tried a few different programs, having a hard time finding the perfect fit.

-----------

I want to improve my backup system/process though.  
I see two options.

1)  Use TrueCrypt.  But I'm debating between doing an encrypted partition, or just an encrypted container... hmm...

2)  Use my eeepc 701 that I never use anymore.  Hide it somewhere ELSE in the house, along with my external HDD.  Do my backups through the home network.  So that my backup is actually far from my real pc.  Much safer.

3)  Do both at the same time.

---

