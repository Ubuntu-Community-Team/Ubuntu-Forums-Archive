---
title: "ZFS usage"
date: 2010-05-23
forum: Server Platforms
---

### Post by Tobas on 2010-05-23
Hi there,

i got a question about the ZFS filesystem & Usage


I got a home-server running Ubuntu-Server 10.04 LTS X64 that have to replace my old server.

I want in my new server all the HDD's from my old server (with data), and that my server see all the HDD's as one.
I did some reading and find uot that ZFS could do the job for me.

Is this the best solution (without the usage of aditional hardware) ?
And can i add one empty HDD so i can fill it with data from a other HDD (so this one becomes empty) and repeat it until al of my drives are migrated ?


Tobas

---

### Post by sylvester_0 on 2010-05-23
ZFS is not supported on Linux because of licensing concerns. I'd recommend you take a look at freenas if all you want is a storage server.

---

### Post by Tobas on 2010-05-23
Is there an other FS that can do almost the same as ZFS, and is available on linux ?

---

### Post by sylvester_0 on 2010-05-23
Btrfs is getting there, but at the moment it's highly experimental and not recommended for production use.

---

### Post by KiraLexi on 2010-05-23
If ZFS is that important, just use Solaris. It's similar enough to Linux that you should be able to use a lot of the same skills, and the Nexenta distribution even uses Ubuntu components on top of a Solaris kernel.

---

### Post by intel on 2010-05-25
the all disk as one big disk feature is called LVM in the linux world.  You do not need ZFS in order to do that.

---

### Post by Tobas on 2010-05-25
Thx i will look into the LVM docs

I dont want to switch from Linux to *BSD, so thank you for the tip

---

### Post by scorp123 on 2010-05-25
> **intel said:**
> the all disk as one big disk feature is called LVM in the linux world.  That's not exactly the same. ZFS puts all disks into a storage pool and offers on-the-fly mirroring, redundancy, snapshotting, cloning, rollback and what not. It's extremely cool.

In OpenSolaris you get a GUI called "Time Slider" that lets you grapically explore your ZFS snapshots. Video:

[http://blogs.sun.com/erwann/entry/time_slider_screencast]("http://blogs.sun.com/erwann/entry/time_slider_screencast")

Solaris 10 doesn't have that feature yet ... so unless you don't mind having to do this on the shell I'd recommend OpenSolaris. The current developer build 134 is very very nice and mature enough; it feels very Linux-like. There are a few smaller differences but it's easy to find explanations for everything via Google.

---

### Post by N.Simpson on 2010-05-26
If you want to stick with Ubuntu then you could try [zfs-fuse]("http://zfs-fuse.net/"). I've not tried this and being in user space there'd certainly be a performance penalty but it may well be good enough for your needs.

> **Tobas said:**
> 
Is this the best solution (without the usage of aditional hardware) ?
And can i add one empty HDD so i can fill it with data from a other HDD (so this one becomes empty) and repeat it until al of my drives are migrated ?


It's difficult to say it's the best solution (unless you are running OpenSolaris in which case it's the best) but it certainly is capable of performing the data copying using the method you mentioned. Be careful of spreading your data across all drives without any redundancy, if a drive fails then you may find yourself losing an awful lot of data.

---

### Post by dragos2 on 2010-05-26
You can always try Nexenta which is a Solaris kernel on top of Debian. It seems to be stable but I won't recommend it.

There are guides explaining how to install ZFS under Linux/Ubuntu but if you want to deploy it into production don't expect support.

I bet on btrfs too but it seems they are moving too slow for what the community is expecting. Expect a production release in 1-2 years. So far ZFS is the best you can get in the open source world.

---

### Post by Vegan on 2010-05-26
If you want big iron file systems, I have looked into LUSTRE as it has distributed features galore.

I have considered porting it to Ubuntu.

---

### Post by Tobas on 2010-05-27
I only want to create a big file Tank for my media streamer.

i now have:
1 x 500 GB (system files)
1 x 1 TB (Kids Movies)
1 x 1 TB ( usefull programs,audio-files,home movies ,...)
1x 1.5 TB (my movies)

and i have 20 GB free :( 

i have bought a new 1.5 TB HDD and want to make a file tank with 3 HDD's (2x 1.5 TB + 1 x 1TB)

This could be done with LVM right ?

---

