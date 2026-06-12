---
title: "Installing Ubuntu on a RAID5 server?"
date: 2008-01-25
forum: Server Platforms
---

### Post by Krunk_Kracker on 2008-01-25
I got a request for a Linux file server to be integrated into a Windows network with Active Drectory..

I have never done this, but I have a little experience with Linux and Ubuntu..I have a Linux Mint laptop that I like a lot, but I'm not a guru or anything.

How would I about installing Ubuntu on a RAID5 array?

---

### Post by Krunk_Kracker on 2008-01-25
No input from anyone??

---

### Post by fozy on 2008-01-26
Setting up a software RAID 5 server can be a fairly simple procedure; there are a few well written howto's on the subject of RAIDs and Ubuntu.  I ran into one snag trying to setup a RAID 5 in that there was a small bug (or large bug by some standards) where your system will no boot if the first drive fails.  I'm not sure if it has been addressed yet.  Anyways, the basic setup you need for a software RAID 5 is a RAID 1 for the boot partition and RAID 5 for the remaining paritions (root and swap at least).

Hardware RAIDs in linux are a completely different beast.

---

### Post by gordyt on 2008-01-26
Krunk I followed the instructions on this website for setting up my system with with RAID 1.

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

They are great instructions and I wonder if they might be adapted to doing a RAID 5 installation?

--gordy

P.S. - The coolest thing about these instructions was they they showed how to upgrade an existing system.

---

