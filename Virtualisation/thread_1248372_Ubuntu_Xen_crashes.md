---
title: "Ubuntu Xen crashes"
date: 2009-08-24
forum: Virtualisation
---

### Post by joel_ezekiel on 2009-08-24
Hello, i was hoping someone could help me with a small problem im having, here are all the details.

I've got:
Intel q6600
8GB RAM
P45-UD3P Gigabyte board
10 HDD's
8x1TB SATA 2x120 IDE
2.26.2-xen-amd64 kernel from Debian, Xen-3.3 Hypervisor from Jaunty repo
Jaunty 9.04
OpenSolaris snv118 DomU 8 SATA drives are passed through to form a ZFS raidz2
Windows XP HVM running of the second 120GB drive

Now I'm by far no expert, but ive managed to get everything working perfect, including sound and nvidia graphics acceleration but i have one problem. When sabnzbd+ downloads something from Usenet its set to automatically extract after downloading to the Solaris DomU and every time it would do this the whole server was crashing and became completely unresponsive, i decided i wold try to extract it on the system drive then copy it across, and this was working fine so i figured it must be something to do with unrar extracting across a network, untill today when it happened again while i was copying about 20GB from Dom0 to DomU. Now if anyone could please help me solve this last little problem as ive got everything else working exactly how i want it would be very much appreciated.

I have had some trouble with the jmicron controler screwing around but that was mainly when i was running just OpenSolaris which is why i now run it under a hypervisor so there are no driver issues. I know i havent posted any logs here, im not sure which logs to look at to be honest.

Anyway thanks for any help.

---

### Post by joel_ezekiel on 2009-08-24
I just thought i would like to add, ive managed to make it crash by copying alot of things back/forth, it didnt do it at first, then eventually it did do it. i checked every log ive got and there is nothing noted in that period of time between booting it up after the crash and well before the crash. So i dont know what else i can do to find out why its doing it :(

im thinking maybe solaris is causing it somehow

---

