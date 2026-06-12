---
title: "LAN access but no internet access"
date: 2019-01-04
forum: Virtualisation
---

### Post by claymca on 2019-01-04
Ubuntu 18.04 VM on Hyper-V Windows 2016. No internet access. Can ping other clients on my network but cannot ping my router/Gateway. The router is performing the DHCP services. DNS is set to 8.8.8.8. 

ping xxx.xxx.xxx.xxx
31 packets transmitted, 0 revived, 100% packet loss, time 3069ms

I have tried 100 different solutions and no luck. Also running Nextcloud and I think thsi is why I cannot get my CIFS shares to work correctly.

Any ideas?

---

### Post by TheFu on 2019-01-06
nextcloud has NOTHING, ZERO, to do with networking or CIFS.

I don't use hyper-v, but is the networking configured in NAT or bridge mode?
Don't know if this is an option, but you'll find much more help if you ran VirtualBox instead of hyper-v.  Virtualbox is much more popular as a Windows hypervisor among Linux people.  If your hostOS was Linux, then KVM would be the suggested hypervisor.

Gathering some information is the 2nd step, assuming the system is setup for bridged networking to guest virtual machines.
```

$ ip addr
$ ip route
```

will get us started.  Please post the commands and output using "code tags", as I've done.

---

### Post by claymca on 2019-01-06
NAT or bridge mode is not configured. I had it working before. But I  needed to reserve the static IP on the router as the IP was issued to my  wife's Apple watch. Once I reserves the new static IP is when I lost  the Internet access on the Ubuntu VM. Doesn't make sense I know. 

Host OS is windows 2016

$ ip addr
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:15:5d:10:04:0c brd ff:ff:ff:ff:ff:ff
    inet 192.168.16.105/24 brd 192.168.16.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::215:5dff:fe10:40c/64 scope link
       valid_lft forever preferred_lft forever

```

$ ip route
```
default via 192.168.16.2 dev eth0 proto static
192.168.16.0/24 dev eth0 proto kernel scope link src 192.168.16.105

```

---

