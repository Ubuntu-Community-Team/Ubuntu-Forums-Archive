---
title: "Fix Error"
date: 2023-03-04
forum: Server Platforms
---

### Post by cyrusraziel on 2023-03-04
Hello 

I got this error

Timed out waiting for device /sys/subsystem/net/devices/wlx90de807a7257.

I think is the wi fi pendrive i used for set the pc but now is removed.

Can you help fix this issue?

Thanks

---

### Post by MAFoElffen on 2023-03-05
None of my hardware ever see a folder of '/sys/subsystem'(?) and I do not recognise a network device in formats of "wlxXXXXXXXXX"(???)

Please post the output of 
```

ls /sys/class/net
grep . /proc/net/dev

```

---

### Post by cyrusraziel on 2023-03-05
Sure

```
enp0s25  fake0  lo  nordlynx
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:  377836    5722    0    0    0     0          0         0   377836    5722    0    0    0     0       0          0
enp0s25: 6305157091 4639302    0    0    0     0          0        49 2331436081 2600442    0    0    0     0       0          0
 fake0:       0       0    0    0    0     0          0         0      126       3    0    0    0     0       0          0
nordlynx: 1694180524 1476879    0    0    0     0          0         0 323897804 1101310    0    0    0     0       0          0


```

---

### Post by MAFoElffen on 2023-03-06
Server with no desktop installed correct?

Please post the result of 
```

grep . /etc/netplan/*.yaml
grep . /etc/NetworkManager/NetworkManager.conf

```

---

### Post by cyrusraziel on 2023-03-06
Sure really thanks for your assistance

```
sudo grep . /etc/netplan/*.yaml
/etc/netplan/00-installer-config-wifi.yaml:# This is the network config written by 'subiquity'
/etc/netplan/00-installer-config-wifi.yaml:network:
/etc/netplan/00-installer-config-wifi.yaml:  version: 2
/etc/netplan/00-installer-config-wifi.yaml:  wifis:
/etc/netplan/00-installer-config-wifi.yaml:    wlx90de807a7257:
/etc/netplan/00-installer-config-wifi.yaml:      access-points:
/etc/netplan/00-installer-config-wifi.yaml:        Manu:
/etc/netplan/00-installer-config-wifi.yaml:          password: XXXX
/etc/netplan/00-installer-config-wifi.yaml:      dhcp4: true
/etc/netplan/00-installer-config.yaml:# This is the network config written by 'subiquity'
/etc/netplan/00-installer-config.yaml:network:
/etc/netplan/00-installer-config.yaml:  ethernets:
/etc/netplan/00-installer-config.yaml:    enp0s25:
/etc/netplan/00-installer-config.yaml:      dhcp4: true
/etc/netplan/00-installer-config.yaml:  version: 2

```

```
sudo grep . /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

```

---

### Post by MAFoElffen on 2023-03-06
Found your culprit...

Do this:
```

sudo mv /etc/netplan/00-installer-config-wifi.yaml ~/00-installer-config-wifi.yaml.bak
sudo reboot

```

---

### Post by cyrusraziel on 2023-03-07
It Worked! Thanks a lot!

---

### Post by ajgreeny on 2023-03-07
Brilliant!

Please now mark this thread as **SOLVED** from Thread Tools up top as it isa great help to others who sear h the forum

---

