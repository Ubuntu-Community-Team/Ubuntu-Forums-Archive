---
title: "Multiple NICs, single IP"
date: 2010-01-31
forum: Server Platforms
---

### Post by ISagalaev on 2010-01-31
Hello!

I'm setting up a headless home server. It has to network cards: Ethernet and WiFi. Both are working fine by themselves. What I want is to have them working on a single IP address depending on which one is connected:

- most of the time the server is not connected to a cable and should communicate over WiFi
- whenever the cable is connected it should prefer Ethernet to WiFi

Basically I want something similar to what NetworkManager does for desktop Ubuntu.

Right now I'm just doing "ifup wlan0; ifdown eth0" remotely but it's kind of boring, doesn't detect the right connection on boot and prone to errors: if I do ifdown before ifup I'm loosing connection and have to get up my *** off my chair and go to the server to reboot it :-)

---

### Post by vpadro on 2010-02-02
AFAIK you can't use a single IP for 2 network adapters connected at the sametime, the only thing that comes in mind is to configure a bridge so you can use it as a single network interface, or configure a load balacing connection...there are several tutorials out there if you google them...

---

### Post by KiLaHuRtZ on 2010-02-02
Install 'ifenslave'...

```
sudo apt-get install ifenslave
```

Then, add this line to '/etc/modules'...

```
bonding mode=active-backup miimon=100 primary=eth0
```

Now edit '/etc/network/interfaces' like this...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address [IP ADDRESS]
netmask [SUBNET MASK]
gateway [DEFAULT ROUTER]
network [NETWORK ADDRESS]
broadcast [BROADCAST ADDRESS]
post-up ifenslave bond0 eth0 wlan0
pre-down ifenslave -d bond0 eth0 wlan0
```

Reboot, and you should be all set!

Oh, and I might add, eth0 and wlan0 become slaves to bond0.  This also allows eth0 to preempt wlan0.  You can see the status of it here...

```
cat /proc/net/bonding/bond0
```

---

### Post by tlsarles on 2010-02-02
That looks pretty sweet, so it will load balance when both lines are connected, and fail over to whichever stays connected when one goes down? That's awesome..... committing to memory... I hope

---

### Post by KiLaHuRtZ on 2010-02-02
Well, there are different modes.  This particular mode does an active/standby, no load balancing.  For load balancing, the switch has to support 802.3ad.

---

### Post by ISagalaev on 2010-02-03
KiLaHuRtZ, ifenslave looks like the solution. Will try it when time allows. Thanks in advance!

---

