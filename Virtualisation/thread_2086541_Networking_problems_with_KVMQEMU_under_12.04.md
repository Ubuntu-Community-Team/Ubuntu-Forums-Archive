---
title: "Networking problems with KVM/QEMU under 12.04"
date: 2012-11-21
forum: Virtualisation
---

### Post by The Foz on 2012-11-21
I have just installed a fresh Ubuntu 12.04 on my server. Previously I was using 10.04 (which worked fine), but had a disk crash (on the Root/OS disk), and had ni usable backup.

I have installed KVM, and have been trying to get my virtual machines to work. I mainly use 2 VMs: one running Ubuntu 9.04, for web, database, and LDAP services, and one running Windows-XP (for MS-Office).

The VMs will both start, but network access is not working. Neither VM is getting an IP address assigned via DHCP from my Internet modem. Assigning static IP addresses doesn't help much; I can't reach any network resource beyond the host, and port forwarding (set up on the Internet modem) is not working.

I am using bridged networking for my VMs, so that they can be accessed by external systems. I created a bridge (br0). The host gets an IP address via DHCP, and has working network access. This is the output from the 'brctl show br0' command:

```

bridge name	bridge id		STP enabled	interfaces
br0		8000.0019b91573b5	no		eth0
							tap0
							tap1
```
In this output, tap0 is the Ubuntu 9.04 VM, and tap1 is the XP VM.

This is my host's interfaces file, which was fine with Ubuntu 10.04:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        network 192.168.0.0
        netmask 255.255.255.0 
        broadcast 192.168.0.255 
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

This is the output from the 'route' command on the host:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    100    0        0 br0
link-local      *               255.255.0.0     U     1000   0        0 br0
192.168.0.0     *               255.255.255.0   U     0      0        0 br0

```

---

### Post by The Foz on 2012-11-21
Finally (after 2 days) solved it. Thought I would post the answer, for other forum users.

I use the Firestarter firewall. In the Firestarter preferences, I set the Internet Connection Sharing to on (pretty sure that I didn't have this set on the 10.04 system), and suddenly everything works OK.

---

