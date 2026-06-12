---
title: "Ubuntu Server 14.04.4 Server 64-bit - VirtualBox, Windows 10 host"
date: 2016-08-04
forum: Virtualisation
---

### Post by gkred2016 on 2016-08-04
Hi,
I have run into trouble after installing an Ubuntu guest on my Windows 10 host.


My laptop: Dell Inspiron 15, 5000 Series
Host: Windows 10 64-bit
Guest: Ubuntu 14.04
VirtualBox: 5.1.2


The installation of Ubuntu went fine, and I was able to play around a bit, but now I can't boot into Windows or Ubuntu. When I power on my machine, I see the Dell logo, and then a black screen with this message: 


**No bootable devices found.**
**Press F1 key to retry boot.**
**Press F2 key for setup utility.**
**Press F5 Key to run onboard diagnostics**


I ran the onboard diagnostics, and it says it passed all the tests.


Any help would be appreciated!
Thanks!

---

### Post by mastablasta on 2016-08-04
we don't know what kind of game you played with the operating systems, however virtualbox is a software and by default everything that is done inside virtualbox stays in virtual box. it can't affect your boot or on anything else on the host system.

you can dedicate a folder in the host and deliberatelly transfer malicious files there, while simultaneously disabled any virus scanner & firewall and then ran such a file on windows. but i doubt you did that. i am afraid youi might not find the answer on these forums as the issue doesn't have anything to do with Ubuntu.

---

### Post by mook765 on 2016-08-06
Try to boot from bootable CD/DVD or USB-pendrive.
If you don't have it, you can download an ISO here
> [http://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](http://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
It's worth a try...

---

### Post by howefield on 2016-08-06
Thread moved to the "*Virtualisation*" forum.

---

