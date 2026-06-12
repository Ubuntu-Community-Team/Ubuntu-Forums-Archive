---
title: "Home made storage server"
date: 2008-06-10
forum: Server Platforms
---

### Post by sambarluc on 2008-06-10
Hi everybody, this is somehow a beginner question, but I thought it would have been more appropriate to post it here.
I would like to set up a storage server at home, using an old (P3) IBM and some new hard disks. I know that freeNas is having some success, but I do not know if it is safe (for data integrity in particular), and I fear I may have some trouble using a pci sata controller. What I would like to do is to set up a server with 3 hard disks in RAID5, accessible both from Ubuntu and windows machines through a switch. Since I really do not have an experience in "networking", could you please give me some hints, or suggest me a place where to start from? I think ubuntu server has all the stuff I need, but I do not know where to start.
Thanks!

---

### Post by hyper_ch on 2008-06-10
Well, a storage server is very simply made...

(however I'd use debian than Ubuntu but that's personal taste).

So, you want to have a basic file server? If so just setup this:
- install base system
- install openssh-server
- assign static ip (tweak the router accordingly)
- install samba and configure the share
- add system-users and then add them to samba

if you want a more complex setup:  [http://www.howtoforge.com/fileserver_with_sme_server7.1](http://www.howtoforge.com/fileserver_with_sme_server7.1)

---

### Post by sambarluc on 2008-06-11
Maybe anyone knows an howto somewhere? I couldn't find any...

---

### Post by m.rankovic on 2008-06-12
[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by andguent on 2008-06-12
Ubuntu definitely has all of the compents you are looking for, but keep in mind it will probably be a time-consuming learning experience. It is all very worth it though.

One quick pitfall to mention: If using software raid, you cannot boot to raid 5. You can however boot to raid 1.

The installer right on the CD will let you setup software raid. The key is to make partition spaces that are of type RAIDautodetect, assemble the raid, and then create an ext3 partition within that raid space.

Also note that while you should have at least one swap partition, it does NOT need to be in a raid. If a swap partition were to fail, the server will still boot.

Google terms to search for:
mdadm raid grub (mdadm is the raid tool if you have to do manual adjustments)
samba home server (file sharing aspect)
ebox (web based config tool, may make setting up samba a bit easier)

---

### Post by sambarluc on 2008-06-13
Thanks! It seems to me that I have a starting point, at least.
By the way, my idea is to install ubuntu on a separate disk, not on the raid, and I hope this would be an easier task.

---

