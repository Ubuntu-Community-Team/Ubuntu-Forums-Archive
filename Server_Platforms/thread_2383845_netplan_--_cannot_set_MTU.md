---
title: "netplan -- cannot set MTU"
date: 2018-01-30
forum: Server Platforms
---

### Post by 0x19xx on 2018-01-30
Hello everyone,

I have an Ubuntu Server 17.10 that Im trying to configure a MTU of 9000. The problem is that whatever I specify in the netplan config file (well, I mean the MTU), it does not get picked up by netplan apply.

Here is my config:

```
network:  version: 2
  renderer: networkd
  ethernets:
    eth0:
      mtu: 9000
      match: 
        macaddress: xx:xx:xx:xx:xx:xx
    eth1:
      mtu: 9000
      match: 
        macaddress: xx:xx:xx:xx:xx:xx 
  bond0:
[etc]

```

I checked the manual and the way I define the value should work.


Anyone have experience with this?

---

### Post by wildmanne39 on 2018-01-30
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by bbouwens on 2018-06-19
I experience the same problem on 18.04 LTS.
Googled around a bit and it found reports that this issue was seen long ago and fixed.
See also [https://ubuntuforums.org/showthread.php?t=2380766](https://ubuntuforums.org/showthread.php?t=2380766)
and [https://bugs.launchpad.net/ubuntu/+source/nplan/+bug/1668693](https://bugs.launchpad.net/ubuntu/+source/nplan/+bug/1668693)

---

