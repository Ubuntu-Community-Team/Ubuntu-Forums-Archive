---
title: "Cripple functionality?"
date: 2008-08-30
forum: Security
---

### Post by eeezzzeee on 2008-08-30
Is there a way to completely lock down a system (basically almost cripple it) so that no changes can be made to the system? I was thinking about making a partition and putting a small distro on it for pretty much only web surfing. I was wondering if there was a way to lock it down or modify it so that the only thing the system could be used for would be to run firefox. Nothing could be updated or changed, nothing could be written to the hard drive, kind of like running a live cd, but without having the cd. I was wondering because with all the browswer, flash, and javascript vulnerabilities that seem to pop up weekly now in my head I thought it would be interesting to find a way to make basically a browser distro that can't be modified in any way by any processes. I know it wouldn't make for a good daily desktop, but it would be great for just general web tasks. My first thought was just to run slitaz off of a cd, but it could still be modified since the whole thing is running in RAM, Then started wondering about making it unwritable in RAM as well, possibly changing all permissions?
Any thoughts?

---

### Post by Oldsoldier2003 on 2008-08-31
try kde kiosk mode. there are other ways to lock down settings, but the kde kiosk mode was specifically designed for this type of scenario

---

### Post by insane_alien on 2008-08-31
you could have the computer boot over the network from an image file. the node would be diskless so nothing could be saved and it will revert back to the origional configuration when done. the absolute worst that could happen is that you need to reboot the node if someone runs sudo rm -rf / although why they would have sudo access in the first place is a conundrum unto itself.

---

