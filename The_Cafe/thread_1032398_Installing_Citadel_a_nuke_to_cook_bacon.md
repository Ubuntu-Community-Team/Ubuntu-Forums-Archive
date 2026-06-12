---
title: "Installing Citadel: a nuke to cook bacon"
date: 2009-01-06
forum: The Cafe
---

### Post by Locke2053 on 2009-01-06
I'm using Ubuntu Intrepid Ibex 8.10 as a fileserver (with software RAID and Samba). Setup was fine, EXCEPT that installing mdadm (for the RAID) also installed a "groupware" server called Citadel.

As a result, my server ended up with a slew of open ports and services (IMAP, POP3, etc.) when all I wanted was a working RAID. This is like using a nuke to cook bacon (mmm.... bacon!).

The vast majority of Ubuntu users don't want the overhead and security risk exposure that comes with running a "groupware" server. The default MTA should be changed to something extremely lightweight, and installing an MTA for packages like mdadm should be optional, not recommended.

Cut the bloat and security problems. K.I.S.S.!

---

### Post by farse on 2009-01-07
Hi, I'm fumbling my way thru this trying to setup an array (with no idea what I'm doing), and just got confused by the citadel install. 

I hit OK then tried to cancel it, but it seemed to put me back into its install. 

How do I remove it and close the ports?

thanks in advance for any assistance,
far

---

### Post by Locke2053 on 2009-01-08
Farse, I just did "apt-get remove citadel-server" or something along those lines. You could also search for citadel in synaptic and uncheck everything which is listed as installed.

---

### Post by FuturePilot on 2009-01-08
I think you hit a side effect of this bug.
[https://bugs.launchpad.net/debian/+source/synaptic/+bug/154349]("https://bugs.launchpad.net/debian/+source/synaptic/+bug/154349")
All the Citadel stuff seems to be marked as "Recommended" to mdadm.

---

### Post by Bachstelze on 2009-01-08
It was about time someone spoke up about this. :D

Agreed 100%.

---

### Post by Bachstelze on 2009-01-08
It was about time someone spoke up about this. :D

Agreed 100%.

---

