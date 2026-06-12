---
title: "UFW with VirtualBox host networking"
date: 2009-01-06
forum: Virtualisation
---

### Post by lykwydchykyn on 2009-01-06
I am using Virtualbox with bridged host networking.  It's all working fine until I enabled ufw, and now ufw is blocking packets to the virtual interfaces.

How do I tell ufw to allow forwarding?

---

### Post by bradleee on 2009-01-15
Any luck with this?  We are doing the same thing with vmware server and bridged networking.

---

### Post by lykwydchykyn on 2009-01-15
Nope, can't find an answer anywhere.  I just dumped ufw and used other methods to configure the firewall.  

ufw also messed up fail2ban, so that was two strikes against it.

---

### Post by bodhi.zazen on 2009-01-15
See if this thread helps :

[http://ubuntuforums.org/showthread.php?t=893489](http://ubuntuforums.org/showthread.php?t=893489)

---

