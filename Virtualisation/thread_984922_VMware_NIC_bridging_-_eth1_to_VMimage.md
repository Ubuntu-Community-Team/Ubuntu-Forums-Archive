---
title: "VMware NIC bridging - eth1 to VMimage"
date: 2008-11-17
forum: Virtualisation
---

### Post by Damester234 on 2008-11-17
Newbieish
I'd like to bind my eth1 to a VMimage so that image can be in a DMZ network for becoming a Web server
I have read a few forums on how to bridge a network card to a particular VMimage.
What I can't understand is which is the simplest for my needs, as there are several ways of achieveing it.
This thread covered it: 
[http://ubuntuforums.org/showthread.php?t=909212](http://ubuntuforums.org/showthread.php?t=909212)
It explains how to: "sure, attach it to a bridge, attach a tap to that bridge, and give the tap to the VM"
Seems complicated compared to this post:
[http://ph.ubuntuforums.com/showthread.php?t=722597](http://ph.ubuntuforums.com/showthread.php?t=722597)
Which explained how to use vmware-config.pl and configure vmnet2 to eth2. This seems a simple solution which I have applied vmnet2 to eth1
Does this work for my scenario?
When configuring the VMimage within the VMware console should'nt VMnet2 have in brackets what eth it's attached to?
Other than running the config.pl is there a way of confirming the nic is bound to this vmnet?

---

