---
title: "eth0 morphs into eth1"
date: 2006-07-14
forum: Sun Sparc Users
---

### Post by allnameswereout on 2006-07-14
Hi. I have a Sun Ultra 5. The machine has currently only one NIC (the onboard one). I can't seem to unload the driver for this NIC as it is not a module in this (official) Ubuntu kernel (2.5.15-26). Sucks, but not the issue here.

During boot, i get
*[    0.083465] eth0: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet 08:00:xx:xx:xx:xx*
which is fine, but later
*[    8.781921] eth1: Link is up using internal transceiver at 100Mb/s, Full Duplex.*

My /etc/network/interfaces contains
[i]# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp[/i]
I added the latter because else i'd have no networking.

When i do /sbin/ifconfig eth0 i get
*eth0: error fetching interface information: Device not found*
When i do /sbin/ifconfig eth1 i get all normal info on my 1st, onboard NIC.

I want to have my eth1 as my eth0. How do i achieve this? Also, this machine ran Debian before where this worked fine out of the box. Though it had more NICs, my onboard one was eth0.

---

### Post by hw-tph on 2006-07-16
I haven't used Ubuntu/SPARC on my Ultra10 (yet) so I cannot verify it works, but /etc/iftab should be of help. On one line, write the MAC address of the device and the interface name you want to assign to the device. This should make sure different devices always have the correct name.

Read iftab(5) for more information.



Håkan

---

### Post by allnameswereout on 2006-07-16
Thank you so much! I see this is Ubuntu-specific which explains why I never heard of this file and why I actually had the problem on a Ubuntu/x86 machine as well after having replaced a NIC in it.

I just deleted the line which was in that file which defined a MAC address for eth0 and some other thingies. The entry obviously didn't function. And, I don't remember I ever asked for this kind of behaviour. I wonder how come this entry was even there in the first place?

---

