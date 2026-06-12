---
title: "[virtualbox guest] auto detect nic changes"
date: 2011-03-28
forum: Virtualisation
---

### Post by beijing5pm on 2011-03-28
Hi all, the situation is I installed a ubuntu 10.04 server as virtualbox guest. And i use NAT networking in that guest. Later I copied the vdi files and use it to create a new virtual machine and of course the mac address is changed during the creation. When I started the new machine the `ifconfig` gave me `eth1` with the new mac address and I need to edit /etc/network/interfaces to add new `eth1` entry and type `dhclient` manually or reboot the machine to get the ip address.
I'm curious is there any way to do this automatically. I mean when i start the new machine the OS can automatically set the new NIC to `eth0` and assign the ip address to `eth0` so I don't need to change the interfaces file and no need to execute dhclient or reboot?

Hope someone can help, thanks in advance.

---

### Post by CharlesA on 2011-03-29
If you export the VM and then inport it to another machine the MAC should stay the same.

If the MAC changes, you can edit the file located here:

```
/etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by beijing5pm on 2011-03-29
Thanks Charles. 
When I say "automatically"  I mean no manually editing needed. And I found my own way: remove the /etc/udev/rules.d/70-persistent-net.rules before copy the vdi file and create the new machine. This way the newly created NIC will be assigined the name `eth0` and it can obtain ip address automatically after VM startup.

---

