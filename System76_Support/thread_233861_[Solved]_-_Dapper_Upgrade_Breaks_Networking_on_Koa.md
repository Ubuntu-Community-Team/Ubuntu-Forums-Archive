---
title: "[Solved] - Dapper Upgrade Breaks Networking on Koala Mini"
date: 2006-08-10
forum: System76 Support
---

### Post by mistermix on 2006-08-10
I have a Koala mini that I'm using as a server.  It worked fine with Breezy.  I just dist-upgraded to Dapper and installed a new kernel (2.6.15-26-686).  Now eth0 doesn't come up.  I tried
```
modprobe r8169
ifup eth0 
```
and that didn't work.  Also tried adding
```
alias eth0 r8169 
```
to /etc/modprobe.d/i386  and rebooting.  That also didn't work.

I wonder if anyone else has seen this and has a solution.  In the meantime, I've dropped back to the 2.6.12-10-686.

Thanks.

---

### Post by crichell on 2006-08-10
do you have wireless in your Koala?

I have heard of this once with a Gazelle Value.  We went into the working kernel and installed network-manager-gnome.  We could then go back into the newest kernel and connect to both wired and wireless via the new network-manager applet next to the clock.

```
sudo apt-get install network-manager-gnome
```

This doesn't necesarrily answer what's going on but since the Dapper release we've moved to network-manager-gnome anyway and it's a much better method to connect to networks.

---

### Post by mistermix on 2006-08-10
Thanks for the reply.  No, I don't have wireless in this Koala.  Actually, I'm using it as a low power consumption small footprint server on our network.  I removed all of the X packages from it, so gnome-network-manager won't help.  

I'll keep looking into it and post to this thread if I figure it out.

---

### Post by crichell on 2006-08-10
Some people have reported that adding irqpoll to the end of the grub kernel parameters fixed the issue.

This thread may be helpfull:

[http://ubuntuforums.org/showthread.php?t=187316&page=3](http://ubuntuforums.org/showthread.php?t=187316&page=3)

---

### Post by mistermix on 2006-08-11
irqpoll doesn't work either. 

I assume that you're sending out Koalas with 2.6.15-26 on them and they work.  Has there been a bios flash that I might have missed?

---

### Post by crichell on 2006-08-11
The dapper upgrade probably changed the eth designation from eth0 to eth1 or 2.  Do an ifconfig and check what eth card is listed.

/etc/network/interfaces may need to be updated - especially if you're using static addresses

---

### Post by mistermix on 2006-08-11
There's no interface other than lo listed by ifconfig.

I think what's happening is that the 2.6.15 r8169 module is hanging the first time it is accessed.  After booting 2.6.15, lsmod shows the r8169 module loaded.  If I run "ethtool eth0", I just get "no such device" errors.  If I remove r8169, and run ethtool eth0, I get this output:

```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000033 (51)
        Link detected: yes

```

If I run "ethtool eth0" again, I just get errors.  So just trying to talk to the card breaks stuff.

So, my question:  do you have any Koala Mini's running 6.06 LTS?

Thanks...

---

### Post by crichell on 2006-08-11
> do you have any Koala Mini's running 6.06 LTS?

Yes - but we're of course not upgrading from Breezy (although we didn't have troubles there either - and another customer in this forum upgraded from Breezy to Dapper without trouble)

can you post your /etc/network/interfaces file?

---

### Post by mistermix on 2006-08-11
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#auto eth1

# The primary network interface
#iface eth1 inet dhcp

iface eth0 inet dhcp

auto eth0

```

---

### Post by crichell on 2006-08-11
From the new kernel:

```
lshal |grep eth
```

look for an entry such as: net.interface = 'ethX'

ethX is the kernel designation given to the ethernet card.  /etc/network/interfaces needs to be adjusted to ethX if it is different than eth0.

---

### Post by mistermix on 2006-08-14
That was it - it was on eth2.  I didn't have lshal, but 

```
lshw | grep eth 
```

works also.

The underlying reason for the problem was that there were MAC addresses defined for eth0 and eth1 in /etc/iftab. I don't know where those MACs came from, but neither corresponded to the built-in networking in the box.  

For some reason, the 2.6.12 kernel ignored /etc/iftab, but 2.6.15 didn't, and therefore it assigned eth2 to the built-in network.

Thanks for your help!

---

