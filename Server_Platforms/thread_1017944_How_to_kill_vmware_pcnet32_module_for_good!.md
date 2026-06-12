---
title: "How to kill vmware pcnet32 module for good!"
date: 2008-12-21
forum: Server Platforms
---

### Post by dragmore on 2008-12-21
Hi. Ive just installed Ubuntu 8.0.4.1-Server 32bit as a guest on my vmware 6.5.1 Workstation
Ive installed ubuntu, apt-get update/upgrade, installed vmware tools and everything is fine and dandy..
Its using the pcnet32 nic driver and i can remove it and insmod vmxnet module..
The problem is that each time i reboot i allways get the pcnet32 driver back, even if i blacklist the module, or put alias eth0 vmxnet.. Anyone know what to do to get vmxnet module to autoload on ubuntu ?

best regards TE

---

### Post by beno1990 on 2008-12-22
open /etc/modules as root

```

sudo gedit /etc/modules

```

in the GUI or

```

sudo nano /etc/modules

```

in the terminal.

Then find whether the module you want to remove is on the list. If it is, delete the line, and add a line with the name of the new module.

Let me know if this works for you.

---

### Post by windependence on 2008-12-22
Excuse me for asking but why do you want to do this?

-Tim

---

### Post by dragmore on 2008-12-22
Hi. Thx for the posts. 
First of all, i put vmxnet in the /etc/modules and it loads, i can see that when i do lsmod, BUT pcnet32 also loads and its used as the primary eth0 driver, at least when i do lspci i can see it as the nic driver..

The reason for me wanting to only use the vmxnet driver is that vmware says that its much better and faster as a virtual nic driver.. Or have i missunderstood something?

best regards TE

---

