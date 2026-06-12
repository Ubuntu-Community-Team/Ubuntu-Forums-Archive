---
title: "Dhcp"
date: 2008-06-25
forum: Server Platforms
---

### Post by r557 on 2008-06-25
Seem to be having an issue with DHCP on my Ubuntu Server running as a Guest host via Virtual Box.

when i attempt to restart networking sudo /etc/init.d/networking restart, i get the following messages.

SIOCSIFADDR: No Such Device
eth0: ERROR while getting interflace flags: No such device
eth0: ERROR while getting interflace flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0

at one point when i ran sudo dhclient, it connected on eth4 but doesn't seem to want to be doing this anymore.  I basically just need the server to obtain an IP address through DHCP.  It's just a sandbox area i use so i'm not overally concerned with configuring DNS etc.

---

### Post by rickyjones on 2008-06-25
> **r557 said:**
> Seem to be having an issue with DHCP on my Ubuntu Server running as a Guest host via Virtual Box.

when i attempt to restart networking sudo /etc/init.d/networking restart, i get the following messages.

SIOCSIFADDR: No Such Device
eth0: ERROR while getting interflace flags: No such device
eth0: ERROR while getting interflace flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0

at one point when i ran sudo dhclient, it connected on eth4 but doesn't seem to want to be doing this anymore.  I basically just need the server to obtain an IP address through DHCP.  It's just a sandbox area i use so i'm not overally concerned with configuring DNS etc.

It does not sound like a DHCP issue but a hardware issue. According to that error message there is no eth0 on your system. Your /etc/network/interfaces file is most likely referencing eth0.

Did you recently copy/move your virtual machine files elsewhere and then start it up?

It could be a udev issue where it found new hardware but it did not reconfigure the network interface file. 

Sincerely,
Richard

---

### Post by r557 on 2008-06-26
I did move my virtual machine from one PC to another.  

How can i reinstall eth0 on the Ubuntu Server guest?  I'm thinking this may be the solution.

I use the same Host Interface for a few different machines that are running (not at the same time) so i know i can get connectivity through that host interface.

---

### Post by rickyjones on 2008-06-26
> **r557 said:**
> I did move my virtual machine from one PC to another.  

How can i reinstall eth0 on the Ubuntu Server guest?  I'm thinking this may be the solution.

I use the same Host Interface for a few different machines that are running (not at the same time) so i know i can get connectivity through that host interface.

Log into your server using the VMWare Console.
cd /etc/udev/rules.d/
vim 70-persistent-net.rules

At the end of the file you probably have two lines. One with a "name" at the end of eth0 and the other eth1. 

Comment out the second to last entry in this file. Then change the "ethX" name for the last entry to reflect the "ethX" assignment that you wish for it to have.

This is similar to what you might have at the end of your file:
```

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:40:ec:f9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:40:ec:e9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

Modify it so that it looks like:
```

# PCI device 0x1022:0x2000 (pcnet32)
**#**SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", #ATTR{address}=="00:0c:29:40:ec:f9", ATTR{type}=="1", #KERNEL=="eth*", NAME="eth0"
# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:29:40:ec:e9", ATTR{type}=="1", KERNEL=="eth*", NAME="**eth0**"

```

My changes are in **bold**.

Hope this helps!

Sincerely,
Richard

---

### Post by Master Chief on 2008-06-27
> **rickyjones said:**
> Log into your server using the VMWare Console.
cd /etc/udev/rules.d/
vim 70-persistent-net.rules

../..

Sincerely,
Richard

Ever looked at: /usr/lib/udev/fix-persistent-net.pl
That should do the trick, right?

---

### Post by rickyjones on 2008-06-27
> **Master Chief said:**
> Ever looked at: /usr/lib/udev/fix-persistent-net.pl
That should do the trick, right?

I've never heard of that file. Does that accomplish the same task?

Thanks,
Richard

---

