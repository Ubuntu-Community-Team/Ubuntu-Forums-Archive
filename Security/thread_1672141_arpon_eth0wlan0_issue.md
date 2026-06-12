---
title: "arpon eth0/wlan0 issue"
date: 2011-01-20
forum: Security
---

### Post by d3v1150m471c on 2011-01-20
I've been trying to setup arpon, on this machine but i keep getting this error message:
```

d3v11@laptop:~$ sudo service arpon stop
 * Stopping anti ARP poisoning daemon arpon                                                       [ OK ] 
d3v11@laptop:~$ sudo arpon -i wlan0

  ArpON "Arp handler inspection" version 1.90 (http://arpon.sourceforge.net)

  [00/20/2011 - 15:37:27 CST] Device: (wlan0) MAC: 0:24:2b:28:4:e6 Inet4: 192.168.1.104 Netmask: 255.255.255.0

d3v11@laptop:~$ sudo arpon -y

  ArpON "Arp handler inspection" version 1.90 (http://arpon.sourceforge.net)

  ERROR: arpon.c:685 @ eth0: no IPv4 address assigned.


d3v11@laptop:~$ sudo arpon -i wlano && sudo service arpon start

  ArpON "Arp handler inspection" version 1.90 (http://arpon.sourceforge.net)

  ERROR: (null) device not found!

```

everytime i try to use wlan0 as the device it fails. any suggestions?

---

