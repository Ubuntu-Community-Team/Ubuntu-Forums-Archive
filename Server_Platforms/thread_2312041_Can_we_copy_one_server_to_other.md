---
title: "Can we copy one server to other ?"
date: 2016-02-01
forum: Server Platforms
---

### Post by soamz on 2016-02-01
Hi, I run a speedtest host server on a Dell 2950 server It has 2 SATA HDD in RAID0 config. 
It runs on Ubuntu server OS.

I got a new Dell PowerEdge R220 server and want to simply copy the Dell 2950 to this directly.
Is there an easy way ?

So, I will copy and then plug the same cable to this directly new server ?

---

### Post by nerdtron on 2016-02-01
Better to rebuild a new server:

1. Install the Ubuntu server OS
2. Install the same software as the old server
3. Copy the config files of the applications that you use from the old server to the new server.


BTW: Using RAID0 is not recommended on any server build.

---

### Post by soamz on 2016-02-02
So there is no way to copy over the exact clone of a server ?

And if not RAID0, then what to set ?
Which is better ?
I only see RAID0, 1,10 in Dell iDRAC panel.

---

### Post by nerdtron on 2016-02-02
RAID1 if you have 2 disks. RAID 10 if you have at least four disk.

You can clone the server and it's partition using CloneZilla. 
1. Shutdown server
2. Boot into Clonezilla and create an image of the whole disks partition. You'll need a big storage for this to hold the copied system image.
3. Boot clonezilla on the new server and restore the copied server image. 

But since you are going to change the RAID configuration you need to reinstall the new server. Reinstalling the server OS, installing software and copying config files will make you familiar with the system too. Thus, you'll get better understanding on how the system works.

RAID0 is not recommended because if one of the disks fails, your data is lost.

---

### Post by soamz on 2016-02-02
> **nerdtron said:**
> RAID1 if you have 2 disks. RAID 10 if you have at least four disk.

You can clone the server and it's partition using CloneZilla. 
1. Shutdown server
2. Boot into Clonezilla and create an image of the whole disks partition. You'll need a big storage for this to hold the copied system image.
3. Boot clonezilla on the new server and restore the copied server image. 

But since you are going to change the RAID configuration you need to reinstall the new server. Reinstalling the server OS, installing software and copying config files will make you familiar with the system too. Thus, you'll get better understanding on how the system works.

RAID0 is not recommended because if one of the disks fails, your data is lost.


Oh!
I guess that has happened to one of my media server. 
When it restarts, one mount is completely gone. 
I have to click S and skip and start it. 

Then manually mount it to work.

---

