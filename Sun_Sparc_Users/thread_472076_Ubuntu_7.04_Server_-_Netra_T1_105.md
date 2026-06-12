---
title: "Ubuntu 7.04 Server - Netra T1 105"
date: 2007-06-12
forum: Sun Sparc Users
---

### Post by EddieTD on 2007-06-12
[SIZE="4"]hello,
I have a problem with the installation of ubuntu in a NETRA T1 105. at the moment that the installation detects them disc, it shows a message “no disks detected”. and it requests to select to me some to driver of a list.:(:(
Somebody can say the procedure to me to install ubunto in a Netra T1 105.

Thank you very much [/SIZE];)

---

### Post by prince_of_hackers on 2007-09-14
I have a Netra T1 105 running Ubuntu 6.06. The first time I ran the installation, the installer crashed right after disk detection, apparently, the disks were formatted in a non-Sun format that couldn't be read properly. As I recall, I booted the rescue mode to erase the disks, then the installation worked fine.

Don't know if it will help, but on my T1 105, Ubuntu is using the sym53c8xx SCSI driver for the hard disks, and the cmd64x IDE driver for the CD-ROM.

---

