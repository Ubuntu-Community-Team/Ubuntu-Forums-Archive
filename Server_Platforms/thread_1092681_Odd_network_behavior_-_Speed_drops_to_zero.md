---
title: "Odd network behavior - Speed drops to zero"
date: 2009-03-10
forum: Server Platforms
---

### Post by pjman on 2009-03-10
I'm getting slow network speeds on transfers. Using bwm-ng I see that the network speed is alternating between zero and normal speeds. My other servers do not do this.

Here's an example.

When I open bwm-ng I get:

```

  bwm-ng v0.6 (probing every 0.500s), press 'h' for help
  input: /proc/net/dev type: rate
  /         iface                   Rx                   Tx                Total
  ==============================================================================
               lo:           0.00 KB/s            0.00 KB/s            0.00 KB/s
             **eth0:           0.50 KB/s            0.68 KB/s            1.18 KB/s**
  ------------------------------------------------------------------------------
            total:           0.50 KB/s            0.68 KB/s            1.18 KB/s
```

But then it drops to zero:

```
  bwm-ng v0.6 (probing every 0.500s), press 'h' for help
  input: /proc/net/dev type: rate
  -         iface                   Rx                   Tx                Total
  ==============================================================================
               lo:           0.00 KB/s            0.00 KB/s            0.00 KB/s
             **eth0:           0.00 KB/s            0.00 KB/s            0.00 KB/s**
  ------------------------------------------------------------------------------
            total:           0.00 KB/s            0.00 KB/s            0.00 KB/s
```

Goes back up again:

```
  bwm-ng v0.6 (probing every 0.500s), press 'h' for help
  input: /proc/net/dev type: rate
  |         iface                   Rx                   Tx                Total
  ==============================================================================
               lo:           0.00 KB/s            0.00 KB/s            0.00 KB/s
             **eth0:           1.41 KB/s            0.68 KB/s            2.10 KB/s**
  ------------------------------------------------------------------------------
            total:           1.41 KB/s            0.68 KB/s            2.10 KB/s
```

And drops to zero:

```
  bwm-ng v0.6 (probing every 0.500s), press 'h' for help
  input: /proc/net/dev type: rate
  -         iface                   Rx                   Tx                Total
  ==============================================================================
               lo:           0.00 KB/s            0.00 KB/s            0.00 KB/s
             **eth0:           0.00 KB/s            0.00 KB/s            0.00 KB/s**
  ------------------------------------------------------------------------------
            total:           0.00 KB/s            0.00 KB/s            0.00 KB/s
```

It consistently alternates between the two very quickly.

Here is the contents of /etc/network/interfaces. I'm using ethtool to force 100/Full speeds.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.110
        netmask 255.255.255.0
        gateway 192.168.1.1
        pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off

```

Output of ethtool:

```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
[B]        Speed: 100Mb/s
        Duplex: Full[/B]
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes
```

Any idea why my network is doing this?

---

### Post by smeerbartje on 2009-03-11
Not sure if this fits your infrastructure, but a few years ago I had the same problems, especially when copying large files. Cause: bad switch. After installing a new switch the problem was solved.

---

### Post by pjman on 2009-03-17
After looking through logs I found the following in kern.log and messages:

> device eth0 entered promiscuous mode
bridge-eth0: enabled promiscuous mode
device eth0 left promiscuous mode
bridge-eth0: disabled promiscuous mode

This keeps repeating itself. After a quick [search]("http://forums.fedoraforum.org/archive/index.php/t-74529.html") I found that promiscuous mode is normal when running a Vmware guest with a network device in bridged mode (which I am).

Is it normal for the network device to keep entering and leaving promiscuous mode?

---

### Post by Vegan on 2009-03-17
You should not have the NIC in promiscious mode, that is for special debugging only and requires specialized software to use it properly.

Better to plink down some cash and get some new Gogabit adapters and be done with it. They are cheap.

---

