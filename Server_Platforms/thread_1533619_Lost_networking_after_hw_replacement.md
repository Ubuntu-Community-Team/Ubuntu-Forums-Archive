---
title: "Lost networking after hw replacement"
date: 2010-07-18
forum: Server Platforms
---

### Post by richardeng2005 on 2010-07-18
HELP! I'm in a serious pickle...

My Dell PowerEdge R200 server just died. Dell had to replace the motherboard, but now networking doesn't work. I'm running Ubuntu Linux Server 7.04 which is a very old version. I think maybe the kernel driver doesn't support the newer revision of the Broadcom adapter on the motherboard. When I try to restart networking, I get the following error:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: no such device

How do I restore networking? Do I require a kernel update? Which kernel version? How do I get this kernel since I don't have network access (so forget apt-get)?

Is there an easier way to resolve this problem?

Do I have to resort to the worst-case scenario of reinstalling *everything* from scratch -- latest Ubuntu version, LAMP, my server application? Dear God!

Here's what the bios tells me:

Embedded Gb NIC1... Enabled without PXE
Embedded Gb NIC2... Enabled without PXE

Further, in the IRQ section:

NIC1... IRQ 15
NIC2... IRQ 14

I did a 'dmesg | less' and scanned for any references to networking. I found that eth0 and eth1 are associated with 'Tigon3'.

Doing a Google search, I found that Tigon3 refers to the Broadcom adapter. So apparently the system is able to recognize the NIC. And Tigon3 is supported in all kernels from 2.6.0 and up.

Thanks.

---

### Post by ian dobson on 2010-07-18
Hi,

I'd imagine that linux (or better said udev) is seeing your network cards as new devices (mac address change), so delete the udev definition for your old networks cards from  /etc/udev/rules.d/70-persistent-net.rules then reboot.

Udev will then see your new network cards as eth0 and eth1 and set them up correctly.

Heres a dump of my 70-persistent-net.rules 

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:10:4b:07:09:33", ATTR{type}=="1", NAME="eth0"


# PCI device 0x1969:0x1048 (atl1)
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:1a:92:bd:06:b1", ATTR{type}=="1", NAME="eth1"

# PCI device 0x10de:0x0057 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:ea:c5:d0:fc", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:8c:36:b1:34", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x8086:0x107c (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:2e:17:42", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"

# USB device 0x:0x (pegasus)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:50:bf:e1:dd:4b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth5"

# PCI device 0x10b7:0x9055 (3c59x)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:50:da:de:be:89", ATTR{type}=="1", KERNEL=="eth*", NAME="eth6"
```

Regards
Ian Dobson

---

### Post by richardeng2005 on 2010-07-18
Unfortunately, I don't have a 70-persistent-net.rules file. For example, I see:

40-permissions.rules
60-symlinks.rules
65-persistent-input.rules
65-persistent-storage.rules
80-programs.rules
85-alsa.rules

and so on, but nothing that looks like 'net' or network.

---

### Post by ian dobson on 2010-07-18
Hi,

Then just do a grep eth /etc/udev/rules.d/*

That should list where udev is hiding the network definitions.

Regards
Ian Dobson

---

### Post by Iowan on 2010-07-19
I presume **sudo lshw -C network** reveals nothing useful?

---

### Post by trundlenut on 2010-07-20
When I changed the motherboard in my laptop which had an embedded network controller eth0 no longer worked and the new embedded controller became eth1, presumably because the MAC address is different.  There were still references to eth0 though.

As Iowan said what does "sudo lshw -C network" produce?

---

