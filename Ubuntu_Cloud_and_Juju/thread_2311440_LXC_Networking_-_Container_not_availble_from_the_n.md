---
title: "LXC Networking - Container not availble from the network."
date: 2016-01-27
forum: Ubuntu Cloud and Juju
---

### Post by mcparty2 on 2016-01-27
Hi folks,

I have an issue with trying to get the networking right on my Host & Containers.
I can assign a static IP address to the Host & the Container (on the same network) though I am unable to reach the container from another host on the same network.

This is how I have set up the networking...

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
bridge_ports eth0
bridge_stp off
bridge_fd 0
address 1.1.1.1
netmask 255.255.255.0
gatewey 1.1.1.254
dns-nameservers 8.8.8.8 8.8.4.4

```


```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:0c:29:9a:bb:4c brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 00:0c:29:9a:bb:4c brd ff:ff:ff:ff:ff:ff
    inet 1.1.1.1/24 brd 1.1.1.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::20c:29ff:fe9a:bb4c/64 scope link 
       valid_lft forever preferred_lft forever
9: veth5OH9WU: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
    link/ether fe:54:23:96:0a:ba brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:23ff:fe96:aba/64 scope link 
       valid_lft forever preferred_lft forever

```

The network is configured in /var/lib/lxc/container1/rootfs/etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 1.1.1.10
netmask 255.255.255.0
gateway 1.1.1.254

```


```

root@host-a:/home/adam# lxc-ls -f
NAME              STATE    IPV4          IPV6  AUTOSTART  
--------------------------------------------------------
container1      RUNNING  1.1.1.10 -     NO         

```


I can ssh from Host A to container1 with out an issue. 
From my laptop on the same network, I can reach Host A but not container1
Anyone with any ideas on what I am missing?

Thank you

---

### Post by mcparty2 on 2016-02-01
A few people as stumped as me I see...
I imagine it's a routing issue, however I do want to preferabbly avoid adding static routes on my network.
I shall continue to persevere but any input would be most welcome.
I'll post back any findings I make.

Thanks again

---

