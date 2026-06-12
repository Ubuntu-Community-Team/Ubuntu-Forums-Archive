---
title: "Last gasp attempt at resolving RAID 5 / SAMBA hang"
date: 2008-06-21
forum: Server Platforms
---

### Post by BadAstronaut on 2008-06-21
I installed Gutsy (without GUI) on a Dell PowerEdge 300 back in March, and upgraded to Hardy when it was released.  I have mirrored 20GB IDE drives for my root volume, and three 500GB SATA drives off a Promise TX4 card running software RAID 5 + LVM for data.

Since day one, I have been **unable to copy** large (>4GB) files from my XP machine to a target volume on the server via SAMBA without the server **hanging hard**.  I initially attempted to troubleshoot this as a SAMBA problem.  Or maybe a kernal bug.  Then I got the notion that it could be an issue with the destination being an XFS partition on a RAID 5 volume.  (There are plenty of threads here describing similar problems -- none, unfortunately, that provides a reliable solution.)

In any case, I've come up empty-handed time & time again.  So I ask:  Anything else I should look into before I blow the whole installation away, rebuild from scratch, and hope that the unknown cause is eradicated as a result?

([My prior posts about this problem, for anyone who is interested in the blow-by-blow account.]("http://ubuntuforums.org/search.php?do=process&showposts=0&starteronly=1&exactname=1&searchuser=BadAstronaut"))

---

### Post by fjgaude on 2008-06-23
I can't say for sure about anything... you might consider what this review points to:

[http://www.pchardware.ro/Reviews/review.php?id=131](http://www.pchardware.ro/Reviews/review.php?id=131)

So many things could be an issue... I have had no problems with Samba and big file transfers but my system is totally different from yours. I use mdadm software raid5 and PCI-E X1 controllers for the six SATA drives I use.

Good luck with finding the cause of your problem, likely a hardware issue.

---

### Post by olivero on 2008-06-23
Hi,

I assume with your server 'hangs hard', you actually say that the machine is frozen and you have to reset it by pulling the plug. If so, it's very likely a driver and/or hardware issue because it's close to impossible to lock a system up whilst running a process in user space.

I'd check if you can get an upated driver for your raid controller. You could also try to check the SMART data from your disks. IO errors usually show up quite nicely.

To me it really sounds like the driver/card is the likely root cause. I had one drive on a failling SATA card once that used to freeze the system during long transfers. In the SMART data I found many seek errors because the card issued bogus commands to the disk.

Oliver

---

