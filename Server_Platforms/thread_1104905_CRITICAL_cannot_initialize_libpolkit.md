---
title: "CRITICAL: cannot initialize libpolkit"
date: 2009-03-24
forum: Server Platforms
---

### Post by madman_lxl on 2009-03-24
I've had a fantastic day to finish it off i needed to reboot a DNS/DHCP server on ESX. (ESX Host needed to get some more RAM). 
Well just my luck reboot with a Halt in it. startup process stops at console kit and fails to boot the remaining services. 

the error is blah blah 'CRITICAL: cannot initialize libpolkit'

Bug is listed here; [https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/275432]("https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/275432")

the way to fix it is to install policykit with apt. Great but no network and you can't start the networking service. GREAT just GREAT!. 

anyone with any ideas on how to start the network cards when the dependent services aren't started please help. 

this is a production server BTW and i'm currently on backup dns and dhcp. :( hope the backup doesn't have the same issue :? i should be upgrading that box as well, not going to now....at least until this is fixed. 

thanks in advance if anyone can help.

---

### Post by MaindotC on 2009-03-24
Just boot from a live cd and install the packages onto the hard drive.  Can you boot into a recovery console?

---

### Post by madman_lxl on 2009-03-24
Ok, Thanks strAlan. Installed Policykit, but....

It's killed the network card. re-ran the vmtools config to see if that helps. no go. 

To fix issue.
removed and added the network card back as vmxnet not e1000. works fine. performed all upgrades to the box. then removed and added the original back with MAC. working fine.

this fix was done with 8.10 x64 and ESX3.5 update 3. (the vmxnet thing only came in on update 3...i think)
 

what an annoying and silly issue. they should fix this bug !

---

### Post by MaindotC on 2009-03-24
Glad it's taken care of and glad you figured it out yourself.

---

