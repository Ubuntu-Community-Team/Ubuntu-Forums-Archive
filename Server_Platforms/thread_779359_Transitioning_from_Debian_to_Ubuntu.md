---
title: "Transitioning from Debian to Ubuntu"
date: 2008-05-02
forum: Server Platforms
---

### Post by rev0lv3r on 2008-05-02
Hello

I just created a server and have configured it much in a VMWare image running on a WinXP Box

It is basically a LAMP stack with Cacti monitoring working, Webmin working. Also some special cron jobs to do backup.

Is it difficult to move to Ubuntu Server?
Is there an easy method to transition all my stuff to Ubuntu Server?

I would like to move from the VM onto a full blown physical machine.
I figure I would have to start from scratch anyways, unless someone knows if I can deploy a VM onto the physical hardware.

After reading about some of these Windows issues, I want to move away from Windows. I used to run Apache2Triad on Windows XP.

BTW: It's small data, maybe a 100mb mysql db. About 20mb worth of php files. The entire VMWare image is 7.5gb.

---

### Post by depele on 2008-05-03
I believe it is possible. 
But you need a special edition of Vm Ware.

you can find a pdf document [here]("http://www.vmware.com/support/v2p/doc/V2P_TechNote.pdf")
check it out.

good luck

---

### Post by andguent on 2008-05-03
It is defintely possible. Linux Journal as an article called "Virtualize a Server with Minimal Downtime". While the article suggests doing the reverse of what you want, it is close enough. The key is to Knoppix/LiveCD your destination box, prep the partitions, and open up ssh. If you know how to rebuild grub from knoppix, then the rest should be easy.

[http://www.linuxjournal.com/article/9942](http://www.linuxjournal.com/article/9942)

If you are doing any RAID with the destination box it makes it slightly more complicated to get there, but very doable and very worth it. See these:

[http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt](http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt)
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)
[https://alioth.debian.org/projects/rootraiddoc/](https://alioth.debian.org/projects/rootraiddoc/)

---

