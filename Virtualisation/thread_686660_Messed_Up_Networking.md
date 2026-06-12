---
title: "Messed Up Networking"
date: 2008-02-03
forum: Virtualisation
---

### Post by firebadger on 2008-02-03
Hi,

I've just installed vmware-server and am using bridged networking following this guide - [http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

I then installed a ubuntu-server as a VM and all was well until I decided to switch to a static IP for both host and VM.  I initially did this for the VM by just editing /etc/networking/interfaces

```
eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1
```

This worked OK, but after I did the same to the host it all got messed up.  I can only see the loopback interface in the VM even after I changed everything back to the way it is.

I'm now quite confused.  Any help much appreciated.

---

### Post by fjgaude on 2008-02-03
I guess you have used the command ifconfig on each of the systems to see just what IP they have, eh?

---

### Post by firebadger on 2008-02-03
Actually, I've got the problem partially resolved.  Somehow eth0 turned into eth1 on the VM.

---

