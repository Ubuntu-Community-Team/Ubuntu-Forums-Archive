---
title: "FreeNAS, Linux and external drives with ext4?"
date: 2013-06-02
forum: Server Platforms
---

### Post by Kdar on 2013-06-02
Hello everyone.

Recently I have install FreeNAS (which is based on FreeBSD) on my NAS that I have built, and I just starting using it today and found out that it can not mount ext4 (which is a file system of all my external drives)... transferring data to NAS and backing up data from NAS over network would be very slow, of course.. so I would like to find a better solution.

Because of that.. I am trying to decide what can I possibly do.....

Should I use Ubuntu or Arch as my server instead of FreeNAS? (possibly with WebGUI admin panel like Ajenti ( [http://ajenti.org/](http://ajenti.org/) ) to manager it all online like I can with FreeNAS...

Or should I better change filesystem on my external drives (which I plan to encrypt anyways... eventually) to something that is more friendlier to FreeNAS and to FreeBSD.... however.. from what I am reading, even reiserfs would be limited to reads only with FreeNAS.

What do you all use here for your NAS, servers? What file system do you use for your external drives to perform backups from your NAS? (I keep hearing that ext4 is bad, as all other ext... but I have always been using it on linux from probably very beginning).

---

### Post by tgalati4 on 2013-06-02
freenas will read ext2 and possibly ext3.  There may be a utility to convert ext4 to ext3 or ext2 that freenas can read.  I use ufs and zfs with my freenas box.  Or, as you have suggested, install Ubuntu (server or desktop) and use that to serve files.

---

### Post by Kdar on 2013-06-02
What do you use to backup files from your NAS? or to move files there (or you just do it all over the network?)

---

### Post by tgalati4 on 2013-06-02
I use a 3-2-1 strategy.  3 copies of important files on 2 physically different machines (or drives) and one off-site.  My NAS is my backup over my network.  I use burned DVD's for offsite storage and some cloud  storage.

---

### Post by Vegan on 2013-06-03
I use my old rig as a server, there is room in the chassis for 5 disks. Its beheaded as I manage it remotely over the network.

This frees me to use any file system I want and the share is transparent to the user

the default of late has been ext4 for Ubuntu server, its par. Still want a file system that can support 18EB+++.

---

