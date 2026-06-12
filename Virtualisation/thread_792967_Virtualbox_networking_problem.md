---
title: "Virtualbox networking problem"
date: 2008-05-13
forum: Virtualisation
---

### Post by adambot on 2008-05-13
Greetings,

I am trying to setup host interface networking for Virtualbox.  I have looked around and found a bunch of guides and have put a script together that should setup the networking (and on the linux side it does) however I have 2 problems:

1) in my VM, no traffic ever comes through (all send no receive - all firewalls have been disabled)
2) when i reboot udev is ignoring the rules that i put in 20-names.rules for tun

Here is my script:
```

sudo tunctl -t tap0 -u user1
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo ifconfig br0 192.168.1.100 netmask 255.255.255.0 up
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.101 netmask 255.255.255.0 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.1.101 dev tap0
sudo arp -Ds 192.168.1.101 eth0 pub

```

---

