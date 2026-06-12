---
title: "Any concerns over keeping both a hardware and a VM version of the same host?"
date: 2015-04-17
forum: Virtualisation
---

### Post by fr33z0n3r on 2015-04-17
So,  I've just celebrated getting my p2v instance of my Ubuntu 14.04.2 desktop converted to a VM using ESXi/hypervisor 6, and the 5.5 Converter.  :)  I have an encrypted home drive (the non FDE option).

But before I consider the final switch to the VM, I want to know if anyone is aaware of any concerns with using BOTH simultaneously?  

**Known concerns:**

[LIST]
[*]Networking concerns - IP address and MAC address need to be unique.  Addressed 
[*]Secrets not unique - Any secrets are no longer unique and therefore pose a security risk.  Change passwords and any keys.  Found this to help ([http://www.cyberciti.biz/faq/redhat-rhel-centos-fedora-linux-sys-unconfig-command/](http://www.cyberciti.biz/faq/redhat-rhel-centos-fedora-linux-sys-unconfig-command/)) 
[/LIST]
 

But is there anything in particular with Ubuntu that should concern me?  (like duplicate SIDs are a Windows concern)

Does any OS component have any concern with this duplicatation of the host?

---

### Post by TheFu on 2015-04-20
Any encryption keys will be duplicated unless you re-create them.  That applies to server and personal keys. Looks like you've found all the other stuff - IP/hostname.  The philosophy of UNIX says to use plain text identifiers, unless there isn't any other choice, so you should be good.

Cloning OS installs is fine - it is a way of life for Linux people.

---

