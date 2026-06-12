---
title: "[SOLVED] microsoft virus scanner to run while in ubuntu"
date: 2008-05-24
forum: Security
---

### Post by rbprogrammer on 2008-05-24
Ok, so here is the problem.  My little sister had many problems with her windows computer.  So I reinstalled the operating system for her and everything seemed fine for about a day, until it started up again.  So I showed her how to use the re-installation CD so that she can do it when I am away from school.  But after the second re-installation, the virus started up again.  I know the virus is not on the disc because we used it a long time ago and it was fine.  So I deduced that the CD is fine and there is no way a virus can withstand a hard drive reformat.  That only leaves her flash drive.

I think the virus is on the flash drive.  So I installed gparted on my computer so I can backup her data, then reformat the flash drive in a controlled environment.  But, if someone took the trouble to make a virus that will save itself to an external drive, there is no stopping him from making the virus so it attaches itself to a file.

So basically what I am looking for is an anti-virus program that I can run in Ubuntu but will search for windows viruses.  The only thing that I can think of is get a free anti-virus software and run it under Wine in Ubuntu.  But I was wondering if someone has a more elegant solution.

Any help is appreciated, thanks.

---

### Post by luisromangz on 2008-05-25
Try AVG, the have a free version for Linux (and Windows) 

[http://free.grisoft.com/ww.download?prd=afl](http://free.grisoft.com/ww.download?prd=afl)

---

### Post by Tomatz on 2008-05-25
> **rbprogrammer said:**
> Ok, so here is the problem.  My little sister had many problems with her windows computer.  So I reinstalled the operating system for her and everything seemed fine for about a day, until it started up again.  So I showed her how to use the re-installation CD so that she can do it when I am away from school.  But after the second re-installation, the virus started up again.  I know the virus is not on the disc because we used it a long time ago and it was fine.  So I deduced that the CD is fine and there is no way a virus can withstand a hard drive reformat.  That only leaves her flash drive.

I think the virus is on the flash drive.  So I installed gparted on my computer so I can backup her data, then reformat the flash drive in a controlled environment.  But, if someone took the trouble to make a virus that will save itself to an external drive, there is no stopping him from making the virus so it attaches itself to a file.

So basically what I am looking for is an anti-virus program that I can run in Ubuntu but will search for windows viruses.  The only thing that I can think of is get a free anti-virus software and run it under Wine in Ubuntu.  But I was wondering if someone has a more elegant solution.

Any help is appreciated, thanks.


The virus needs to first be executed so if it were on the flash drive it would be "benign" until it were executed.

Some variants of the Trojan dropper can save themselves in ram and reactivate on boot so before you reinstall completely unplug your box for 2 minutes to clear out the ram as your computer stays on standby while plugged in.

My advise is to reinstall and dont put anything you had on there before back on.

---

### Post by pietjanjaap on 2008-05-25
If you only formatted the drive then a virus can stil be on the mbr.
start up with windows cd, press R goto recover console, then fixmbr(or mbr fix), then the virus is gone.

Download all software fresh in ubuntu, disconnect from internet wen installing.

---

### Post by rbprogrammer on 2008-05-25
All make really good sense, and that is noted for next time.  But a closer examination of the flash drive yields quite a simple solution.

In the root part of the directory tree, there was on of those windows autorun text files, which called the program "start.exe".  Deleting them both fixed the problem.

It's always the simplest of solutions that I get hung up on. :lolflag:

---

### Post by Tomatz on 2008-05-25
> It's always the simplest of solutions that I get hung up on.


Its not just you ;)


:lolflag:

---

