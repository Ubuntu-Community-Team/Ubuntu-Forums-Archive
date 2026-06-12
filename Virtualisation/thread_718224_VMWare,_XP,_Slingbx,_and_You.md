---
title: "VMWare, XP, Slingbx, and You"
date: 2008-03-07
forum: Virtualisation
---

### Post by Radioman991 on 2008-03-07
Hello

This has to be a setting somewhere I am missing....

Ubuntu Gutsy, running VMWare Server with an XP virtual machine.   Installed my Sling Player on XP, and got it working on the LAN.  However, sling says it can't be located via the Internet.  I have the correct finder ID and everything is correct in my router.

I am sure it is something in the way the network is set up between the VM and Ubuntu.    If I can solve this one small issue, I am 100% rocking!  I'll try any ideas anyone has.

FWIW, the first time I tried Ubuntu, I went the Wine route to try to get Sling Player running without success.  Being able to watch Sling on the LAN in the house is a great start...further than I made it before.

PK

---

### Post by gstanden on 2009-01-12
When connecting to slingbox via internet, switch your vmware virtual ethernet NIC to "NAT".  Use "bridged" when you are on you home LAN.  Works great for me.  You don't have to restart the vm to do this: if you switch from bridged to NAT or vice versa, just open a cmd window in the vm after switching and do an "ipconfig /release" followed by "ipconfig /renew" and then run "ipconfig" to make sure your ip address has been updated.

---

