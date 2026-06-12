---
title: "Virtual Interfaces not coming up"
date: 2011-11-18
forum: Server Platforms
---

### Post by Sock! on 2011-11-18
Hey Guys,
I have a strange problem. I have done Virtual Interfaces before but for some reason it is not working this time. 

With this config:
```

auto lo
iface lo inet loopback


auto eth0
auto eth0:0
auto vlan450

iface eth0 inet static
        address 192.168.0.254
        netmask 255.255.255.0
        network 192.168.0.0
        gateway 192.168.0.1

iface eth0:0 inet static
        address 192.168.0.240
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

iface vlan450 inet static
        address 10.0.1.1
        netmask 255.255.255.0
        network 10.0.1.0
        broadcast 10.0.1.255
        vlan_raw_device eth0


```

I get this response when trying to get eth0:0 up.
```
root@ubuntu:~# ifup eth0:0
RTNETLINK answers: File exists
Failed to bring up eth0:0.

```

Any Help would greatly be appreciated :P

---

### Post by SeijiSensei on 2011-11-19
We just had a [thread]("http://ubuntuforums.org/showthread.php?t=1870364") about this problem the other day.  It seems to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829") in 11.10.

If you going to run a server, you should be using 10.04 LTS.  Servers and cutting-edge releases usually don't mix.

---

