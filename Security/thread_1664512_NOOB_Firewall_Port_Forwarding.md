---
title: "NOOB Firewall Port Forwarding"
date: 2011-01-11
forum: Security
---

### Post by mclimber43 on 2011-01-11
I recently set up a server machine (samba, ftp, apache) in my lab and use webmin for administration and VMware server.  I want to forward ports from my router to my machine so I can access webmin, Samba (by tunneling through ssh) and the virtual machine (through something like remote desktop or VNC) from outside the local network.  All users have fairly strong passwords.  Are there serious security risks with doing this?  I seem to be finding conflicting information.

I am new to the network administrator role, so even seemingly obvious answers are appreciated!

---

### Post by sj1410 on 2011-01-11
port forwarding is not a bad idea. only forward the required ports and use strong password.

---

### Post by bodhi.zazen on 2011-01-11
> **mclimber43 said:**
> I recently set up a server machine (samba, ftp, apache) in my lab and use webmin for administration and VMware server.  I want to forward ports from my router to my machine so I can access webmin, Samba (by tunneling through ssh) and the virtual machine (through something like remote desktop or VNC) from outside the local network.  All users have fairly strong passwords.  Are there serious security risks with doing this?  I seem to be finding conflicting information.

I am new to the network administrator role, so even seemingly obvious answers are appreciated!

As indicated, port forwarding itself is not bad, but you need to secure those servers.

I highly advise you NOT port forward samba or VNC, I seriously doubt you need either.

I suggest you learn ssh and use scp, sftp, ssh -X etc.

Just be sure to secure the ssh server, ie use keys and disable passwords.

---

### Post by cariboo on 2011-01-11
To check if you have  setup port forwarding properly you go to [canyouseeme]("http://canyouseeme.org"), to see if the ports you forwarded are open to the whole world.

---

### Post by sj1410 on 2011-01-11
> **cariboo907 said:**
> To check if you have  setup port forwarding properly you go to [canyouseeme]("http://canyoseeme.org"), to see if the ports you forwarded are open to the whole world.


please correct its [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by cariboo on 2011-01-12
Thanks for catching my spelling error. Fixed

---

