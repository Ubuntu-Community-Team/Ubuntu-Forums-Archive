---
title: "msi-7104 built in ethernet port is extremely slow?"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-28
the mb ethernet port is extremely slow.

2.0mb/sec, so it can barely work.

The line is good, it connects a gb speeds with another pc.

This is a new trusty install. 

Any utils to test?
I have a pci gigabit netgear card, but put that in the pc, and it will not even power on. That card works fine in another pc.

---

### Post by varunendra on 2014-03-03
Have you confirmed that it is not a samba share issue and is consistently the same across all kind of network traffic?

By the way, 2MB/s = 8 x 2Mb/s (not that it is satisfactory though)

I would take a look at these :
```
ifconfig *[COLOR="#800000"]# dropped packets? lots of frame errors etc.?[/COLOR]*
ping <any local device> *[COLOR="#800000"]# too much delay time?[/COLOR]*
sudo ethtool eth0 *[COLOR="#800000"]# to view current settings of the interface eth0[/COLOR]*
```

I would try these -

* Change the MTU value from default (1500) to 1492 or 1392.
* Change the link speed to 100 Mbps/Full-Duplex with the following -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

Neither is very promising, but sometimes they help.

---

