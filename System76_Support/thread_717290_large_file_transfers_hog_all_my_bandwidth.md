---
title: "large file transfers hog *all* my bandwidth"
date: 2008-03-06
forum: System76 Support
---

### Post by novalis_dt on 2008-03-06
I'm transferring data from my ancient Gateway laptop to my new Serval using scp (or rsync over ssh).  The transfer is going fine, if a bit slow (about 35k/sec, over local wireless).

The problem is that all other network traffic on the Serval seems to be blocked by the transfer.  I try to ping the router, and get 100% packet loss.  I can ping the machine I am transferring to, but get some packet loss there too (maybe 10%).  I can't ping anything outside the local network.  Ctrl-z to pause the scp, wait 2 seconds, and the pings start working.  fg to restore it, and they stop again.  I repeated this test several times.  There is no problem for the Gateway or the other machine connected to the network, so it's not that the network itself is saturated.

The slowness is also a bit of a concern, but until I try (say) bittorrent, I won't know how much of that is attributable to the protocols or the extra wireless traffic.

---

### Post by theologian aaron on 2008-03-07
Sounds like a job for an external hdd.  I move around computers a fair bit,  and have found the expense of the gadget well worth the efficiency it provides.  I use a 160gb drive with grsync and can have everything from one computer to the next in no time at all.

---

### Post by thomasaaron on 2008-03-07
If both units are hooked to a WIRED connection, it might go faster too.

---

### Post by novalis_dt on 2008-03-07
Perhaps I was not clear: I'm not complaining that things are a bit slow -- that's a secondary issue.  I am patient.   

I am complaining that things are  *broken*.  In every system I have ever used, there is no way that one connection could utterly prevent all other networking.  It's not that other networking is slowed down -- that would be reasonable.  It's that it's *stopped*.  100% packet loss.  Broken.  

Sure I could use an external hard drive.  I could also ship my Serval back and buy something that works.  

In case it helps, my model is FL92, and my kernel is 
Linux ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

I'm using the plain old install of Ubuntu 7.10 which came with my Serval.  I've made no changes to the hardware or relevant software.

---

### Post by novalis_dt on 2008-03-07
Actually, I take that back.  I am complaining that things are slow, but it is an additional complaint.  I am downloading new kernel sources from kernel.org (to see if maybe this is fixed in a new version), and it's going at about 14 K/s.  So I tried the same thing on my other laptop -- same wireless connection to the same cable modem, two feet away.  I get about 450K/s.  

I tried upgrading the firmware to the latest, which gets me to about 23 K/s (don't know if it's actually related).

---

### Post by thomasaaron on 2008-03-07
Unfortunately, I don't really have a way to replicate that probem.

Still, I'd like to know if you have the same problem with a wired connection. If you DO NOT, that would eliminate your router's bandwith as a potential problem and point towards a possible bug in the 4965 driver for your wireless card.

---

### Post by novalis_dt on 2008-03-07
The wired network (same cable modem connection, same router, just via wires rather than wifi), works perfectly.  I get like 1.16 M/s from kernel.org, and scp connections do not block other traffic.

[edit] I gather from your icon that you work for System76.  Can't you just pick up a new Serval (new as in my shipment was delayed because some sort of minor update was coming in), and see if it has the same problem?  I don't know what kind of wireless I am using (a/b/g), but I think it is b, based on the age of the router.  Do you know how I can tell?

---

### Post by thomasaaron on 2008-03-07
The Intel 4965 card in your computer is running off of the iwl4965 driver instead of the ipw4965. There are a number of bugs with the ipw4965 that are being worked on, and the iwl driver is being used in the meantime.

I've heard that, as of Hardy's release in April, this will be fixed and it will revert back to the ipw driver.

EDIT:
Just to clarify, the iwl drivers have limitations. I don't know what all of them are, but I think you just ran into one of them. However, they don't cause freezing and other symptoms that were caused by the ipw driver.

---

### Post by novalis_dt on 2008-03-07
Have you in fact tested Hardy to see if it works?

---

### Post by thomasaaron on 2008-03-07
We have not begun testing Hardy yet. We will probably begin in a week or two.

---

