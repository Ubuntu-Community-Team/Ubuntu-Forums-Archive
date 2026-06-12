---
title: "iptables connmark problems"
date: 2007-08-13
forum: Server Platforms
---

### Post by stromgren on 2007-08-13
Hi!

I have a Ubuntu-based server running as my home netwok firewall/router. Recently I received a secondary internet connection wich i thought I'd use to load balace with my current connection. 

To accomplice this I use a multipath route with equalize. This is working great accept for active connections, e.g. radio and online games, wich have a fifty percent change of disconnecting every time the router flushes the route cache. 

I've read that to prevent this to happen you should use the connmark chain in iptables. Now to the point. Connmark doesn't work. According to [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/112611](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/112611) there's a bug in ubuntu making connmark not to work as intended, or as in my case, not at all. I've tried modprobe and all that.

It there any solution to this problem? Has this bug been solved?

Thanks in advance!

---

### Post by saresca on 2007-08-15
This just work for my server.

Ubuntu Feisty server.
Ubuntu 2.6.20-16.29-server

**WARNING:** Building and using a custom kernel will make it very difficult to get support for your system.  You will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without explanation).

While Ubuntu Kernel Developers add CONNMARK as kernel module you can do:

Using this HOW-TO. [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
do.

Install developer tools
```
sudo apt-get install linux-kernel-devel fakeroot build-essenital
```

Download ubuntu kernel source
```
sudo apt-get install linux-source-2.6.20
```

Untar it.
```

cd /usr/src/
tar jxvf linux-2.6.20.3.tar.bz2
```

```

cd linux-2.6.20.3
make oldconfig
```

Modify .config file

```

# CONFIG_NETFILTER_XT_TARGET_CONNMARK is not set
# CONFIG_NETFILTER_XT_TARGET_NOTRACK is not set
```

Set to:

```

CONFIG_NETFILTER_XT_TARGET_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
```

Then recompile the kernel:
```

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

And finally install it:

```
sudo dpkg -i linux-image-2.6.20-16-custom.deb
```

Then just try:

```
iptables -t mangle -I PREROUTING -j CONNMARK --restore-mark
```

---

### Post by stromgren on 2007-08-16
Thanks, that worked great. Now to another problem. I've managed to load balance my two connections and all works great ecept for that it's really slow. If I turn of the marking of all outgoing packages the speeds up to normal but with the marking on, wich is very important for the overall function, the speed is poor. I can't see any load on the cpu, so it must be related to something other. 

EDIT: It's not the bandwidth that's low, it's the responses. Ping and nslookup give nice latencies so it have to be something else.

I really appriciate anwers and ideas!

---

### Post by saresca on 2007-08-16
Post your:

```
ip route
```
```
ip rule
```
```
iptables -t mangle -L -nv
```
```
ip add
```

Don't forget to remove personal information.

---

### Post by stromgren on 2007-08-17
ip route
```

83.227.160.xxx/xx dev eth1  proto kernel  scope link  src 83.227.160.xxx 
192.168.10.0/24 dev eth0  proto kernel  scope link  src 192.168.10.1 
11.3.0.0/24 dev eth2  proto kernel  scope link  src 11.3.0.184 
10.0.0.0/8 via 11.3.0.1 dev eth2 
default equalize 
        nexthop via 83.227.160.xxx  dev eth1 weight 1
        nexthop via 11.3.0.1  dev eth2 weight 1

```

ip rule
```

0:      from all lookup 255 
32760:  from all fwmark 0xca lookup Pref2 
32761:  from all fwmark 0xc8 lookup Equalize 
32762:  from all fwmark 0xc9 lookup Pref1 
32763:  from all fwmark 0x66 lookup Eth2 
32764:  from all fwmark 0x65 lookup Eth1 
32765:  from all fwmark 0x64 lookup Eth0 
32766:  from all lookup main 
32767:  from all lookup default 

```

iptables -t mangle -L -nv
```

Chain PREROUTING (policy ACCEPT 6392K packets, 5816M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 CONNMARK   0    --  eth0   *       0.0.0.0/0            0.0.0.0/0           CONNMARK restore 
    0     0 MARK       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 MARK match 0x0 MARK set 0xc8 

Chain INPUT (policy ACCEPT 28756 packets, 2877K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 6362K packets, 5813M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 26086 packets, 13M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 6388K packets, 5826M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 MARK       0    --  *      eth2    0.0.0.0/0            0.0.0.0/0           MARK match 0xc8 MARK set 0xca 
    0     0 MARK       0    --  *      eth1    0.0.0.0/0            0.0.0.0/0           MARK match 0xc8 MARK set 0xc9 
    6   744 CONNMARK   0    --  *      *       0.0.0.0/0            0.0.0.0/0           CONNMARK save  

```

ip add
```

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0a:5e:24:37:aa brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.1/24 brd 192.168.10.255 scope global eth0
    inet6 fe80::20a:5eff:fe24:37aa/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:02:b3:15:b1:4e brd ff:ff:ff:ff:ff:ff
    inet 83.227.160.xxx/xx brd 83.227.160.255 scope global eth1
    inet6 fe80::202:b3ff:fe15:b14e/64 scope link 
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:20:ab:19:74 brd ff:ff:ff:ff:ff:ff
    inet 11.3.0.184/24 brd 11.3.0.255 scope global eth2
    inet6 fe80::213:20ff:feab:1974/64 scope link 
       valid_lft forever preferred_lft forever

```

EDIT: I've been testing a bit and come to the conclution that it's not the marking itself thats slow, its the connmark --save-mark that's slow.
EDIT2: After some further testing I've concluded that it's actually the --restore-mark that's slow. But it's only slow when there's marks.
EDIT3. May it be the interface queue legth?

---

### Post by stromgren on 2007-08-29
Now I've tested to change network cards to Intel cards but whit no result. I've also tested to set the txqueuelength to 1000 on all cards buw with no result. 

This whole problem is very strange...

---

