---
title: "[SOLVED] eth1 not running at 1000Mb/s (ethtool)"
date: 2007-09-27
forum: Server Platforms
---

### Post by AndyW on 2007-09-27
Using ethtool it tells me that eth1 is at 100Mb/s and i try to run 
sudo ethtool -s eth1 speed 1000 and it does nothing.

Is there a different way to do this?

I know that this card works in 1000Mb/s because I did it in debian. The card seems a little flaky though, so that could be the proble,.

---

### Post by eph1973 on 2007-09-27
You have access to a backbone or something?  Something with gigantic bandwidth like say a T3?  Because you'd never even approach 100Mb/sec over a cable Internet connection, or other standard broadband methods.

---

### Post by AndyW on 2007-09-27
Nope, just access to a gigabit network. Speed :)
here is the output of ethtool eth1:
```
Settings for eth1:
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
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

---

### Post by eph1973 on 2007-09-27
And
```

sudo ethtool -s speed 1000 eth1
```
Doesn't change it for you?

---

### Post by AndyW on 2007-09-27
Well I did a lot of things at once (change cable, change settings) and it seems to work now. :KS

---

