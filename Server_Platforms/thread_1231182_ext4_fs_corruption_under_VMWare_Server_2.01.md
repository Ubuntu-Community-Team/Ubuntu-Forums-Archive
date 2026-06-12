---
title: "ext4 fs corruption under VMWare Server 2.01"
date: 2009-08-04
forum: Server Platforms
---

### Post by pioni on 2009-08-04
I'm running Ubuntu Server 9.04 virtualized under VMWare Server 2.01, which runs inside yet another Ubuntu Server 9.04. The virtual server is a default fresh install (not an upgrade) plus XAMPP stack from apachefriends.org. For some reason, the ext4 filesystem has been corrupted twice. I don't have any idea how this happens, just that it happens without reboots nor crashes. The virtual server was rebooted two days ago and everything was running just fine, but today morning I noticed that Apache and MySQL weren't running anymore and the filesystem was readonly. I rebooted and the fsck failed saying that the disk is corrupted. I ran fsck manually and so far it *seems* that everything is still fine. Last time, about two weeks ago it did the same and two very important MySQL tables were corrupted beyond repair. 

So, my question is should I switch back to ext3, which is not that easily corrupted without any particular reason or is there something else wrong with the setup? Like I said, the host server nor the guest server were not rebooted nor crashed and there was no clues of anything going wrong until everything was wrong. I did not run out of disk space, both the host and the guest have plenty left. VMWare Server is running several other virtual servers also at the same time and there has been no problems with those, but none of those is using ext4. The problem should not be in hardware, because the server is virtualized and all other virtual servers are running just fine.

---

### Post by pioni on 2009-08-31
Seems to me that the problem is now solved even though no one bothered to reply anything. :( The ext4 corruption bug seems to be very old and it's very interesting that bugs as serious as this are still left in distribution marked stable. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389555]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389555")

After updating to latest kernel, I haven't seen any corruption problems so far. One more problem of this kind and ext4 is history for me, forever. Ext4 should not have been included to Ubuntu as stable, because it really is anything but stable!

---

### Post by moorewr on 2010-03-05
I found this after some Google searching.

I'm running vmware-server 2.0.2 on Ubuntu 9.10 64-bit.. kernel 2.6.31-19, and I can confirm this corruption still happens fairly frequently.. one-two times a week with one VM running, for example.

The logged symptom is a silent journal abort and a read-only remount.. accompanied by fs write error pop-ups from my vmware client.

I've given up and I'm converting the volume to ext3.

---

### Post by pioni on 2010-03-10
> **moorewr said:**
> I've given up and I'm converting the volume to ext3.

This is what I ended up doing. I simply could not get ext4 filesystem to stay uncorrupted, so I switched to ext3 everywhere. No problems ever since. The problem in ext4 (or Ubuntu, I don't know) still exists and I value my data too much to try ext4 again.

---

