---
title: "Help Installing Kernel Module"
date: 2012-01-22
forum: Server Platforms
---

### Post by RLovelett on 2012-01-22
I am trying to make my ethernet controller work.

My server is running 10.04.3 x64.

```

lspci | grep Eth
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)

```

I have found this kernel module: [http://manpages.ubuntu.com/manpages/lucid/man4/msk.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/msk.4freebsd.html)

Supposedly it will work with my ethernet card but I don't know how to install/enable it. There is no loader.conf on my system so I cannot follow the steps listed on that man page.

```

sudo modprobe msk
FATAL: Module msk not found.

```

Help please. :confused:

---

### Post by rubylaser on 2012-01-23
> **RLovelett said:**
> I am trying to make my ethernet controller work.

My server is running 10.04.3 x64.

```

lspci | grep Eth
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)

```

I have found this kernel module: [http://manpages.ubuntu.com/manpages/lucid/man4/msk.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/msk.4freebsd.html)

Supposedly it will work with my ethernet card but I don't know how to install/enable it. There is no loader.conf on my system so I cannot follow the steps listed on that man page.

```

sudo modprobe msk
FATAL: Module msk not found.

```

Help please. :confused:

I'm confused, based on your lspci your device is recognized.  This is a second NIC in your machine, so have you added a line to /etc/network/interfaces for the device?

---

### Post by RLovelett on 2012-01-23
Spoke too soon! It's not working!

---

### Post by RLovelett on 2012-01-23
The ethernet adapter is the only adapter I have in the machine. When I type in ifconfig I get both eth0 and lo. And eth0 is getting an inet addr:192.168.1.100 so DHCP seems to be working.

---

### Post by rubylaser on 2012-01-24
So, are you saying networking is functioning like it should be now since DHCP is working?

---

