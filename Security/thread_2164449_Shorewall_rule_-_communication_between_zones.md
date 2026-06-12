---
title: "Shorewall rule - communication between zones"
date: 2013-07-31
forum: Security
---

### Post by SeaKing on 2013-07-31
Hey guys,

I've currently set up my shorewall firewall on my router.

configs:
```

eth0 -> connected to the inet
eth1-> 192.168.1.0/24 (vlan1 | zone sw)
vlan50 -> 192.168.50.0/24 (@eth1 | vlan50 | zone v50)
...
-----------------------------------------------------
/etc/shorewall/interfaces
inet    eth0            detect          dhcp
sw      eth1            detect          dhcp
v50     vlan50          detect          dhcp
-----------------------------------------------------
/etc/shorewall/zones

###Firewall itself
fw      firewall
###vlan1 - switch config lan
sw      ipv4
###eth0 - internet
inet    ipv4
###vlan50 - private
v50     ipv4
-----------------------------------------------------
/etc/shorewall/policy

inet    all     DROP            debug
sw      all     DROP            debug
v50     all     DROP            debug
v60     all     DROP            debug
all     all     REJECT          debug

-----------------------------------------------------
/etc/shorewall/masq

eth0                    vlan50
eth0                    vlan60
-----------------------------------------------------
/etc/shorewall/rules
#rules relating sw/$FW/vlan50 communication
#vlan1 -> $FW
ACCEPT  sw      $FW     tcp 53,67,68
ACCEPT  sw      $FW     udp 53,67,68

#FW -> vlan50
ACCEPT  $FW     v50     tcp 22,80,443


```

The problem is, I get no connection between v50 and sw and no DROP messages in the logs. I also tried 
```
ACCEPT  $FW     v50:<IP>     tcp 22,80,443
``` but it didn't work either and I don't want only to reach this specific address on the other lan but all hosts there on the listed ports.

---

