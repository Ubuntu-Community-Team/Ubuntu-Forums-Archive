---
title: "Quintum LTO 2 Problem on Ubuntu Server 10.04 LTS"
date: 2010-11-25
forum: Server Platforms
---

### Post by Bertus_Nel on 2010-11-25
Hi all

I have little problem that I cant get rid off, despite reading all posts and forums on the internet. I get a "/dev/tape: Inappropriate ioctl for device" when I run #mt status. I setup Bacula on the server to backup to a Quintum LTO 2 device.

Running lsscsi I get the following:
[0:0:1:0]    disk    ATA      ST3250820AS      3.AA  /dev/sda
[1:0:0:0]    disk    ATA      ST3250820AS      3.AA  /dev/sdb
[1:0:1:0]    disk    ATA      ST3250820AS      3.AA  /dev/sdc
[5:0:0:0]    disk    ATA      ST3200822A       3.01  /dev/sdd
[5:0:1:0]    disk    ATA      ST3200822A       3.01  /dev/sde
[7:0:6:0]    tape    CERTANCE ULTRIUM 2        1823  /dev/st0

So it listed my device, all configs in Bacula uses /dev/st0 - now the way I understand is that you need to stop the bacula damons before running the mt status, doesnt matter if it runs or not I still get this.

Ive been working on this for 2 days and my deadline is tomorrow and I still cant backup using the LTO

Did anyone out there in the digital world experiance something like this before? If so, what can be done to get it fixed? If I can get this fixed I can start working on my actual Config for bacula seeing that this doesnt run at the moment and I think the problem above is stopping me from running Bacula.

any help will be valued and highly appreciated.

Thanks

bertus

---

### Post by Bertus_Nel on 2010-11-26
Hi all

No worries, I got it to work. No need for any backup program - run it straight from terminal and write directly to the LTO. Superfast to write and restore..

Thanks anyway ;)

---

