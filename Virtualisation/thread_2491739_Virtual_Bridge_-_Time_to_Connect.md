---
title: "Virtual Bridge - Time to Connect"
date: 2023-10-19
forum: Virtualisation
---

### Post by Quarkrad on 2023-10-19
Prior to my recent change to having bridge networking, rather than NAT, for my host/VMs I have, for years, been impressed that as soon as my Desktop launched I could fire-up a browser and surf the net (almost an instant connection).  Having set up a virtual bridge it takes a long time - I haven't timed it but it must be in the region of 10 seconds.  Is this the norm?

---

### Post by MAFoElffen on 2023-10-19
You never gave us details... What is your virtual host system and how do you have your virtual bridge connection configured? What is the OS of the VM Guests? 

It hints like KVM, but I don't want to assume...

---

### Post by Quarkrad on 2023-10-19
Apologies - after all this time (been on here since 8.04) I forgot the obvious.  I'm running Mate 22.04 and qemu/kvm.  I'm not sure what info you need but here is some data:

```
dad@dadubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master nm-bridge state UP group default qlen 1000
    link/ether 2c:f0:5d:92:6d:9e brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:bf:a1:f7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: nm-bridge: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 4e:fc:b1:5b:4c:70 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.9/24 brd 192.168.1.255 scope global noprefixroute nm-bridge
       valid_lft forever preferred_lft forever

```

```
dad@dadubuntu:~$ brctl show
bridge name	bridge id		STP enabled	interfaces
nm-bridge		8000.4efcb15b4c70	yes		eno1
virbr0		8000.525400bfa1f7	yes
```

I followed this video [https://www.youtube.com/watch?v=DYpaX4BnNlg](https://www.youtube.com/watch?v=DYpaX4BnNlg).  At about 10.08 he talks about giving the bridge 10 - 15 secs for the bridge to get connected.  I assumed this was a one off - perhaps this 10-15 seconds is needed every boot; which is probably what I am seeing.   If this is right I now have the same ip range for my host (ubuntu 22.04) and kvm guest (at the moment also ubuntu 22.04) for the cost of a slower connection speed to my router.

---

### Post by DuckHook on 2023-10-19
This happens to me too.

Possibly just your router going "whaa-aat?" from having to assign separate IP addresses to the same physical endpoint. Depending on your router, it may just take that long for it get over the schizophrenia and make the assignment.

Another culprit could be network manager. I've found that it's not very clever and sometimes gets confused with non-default configs.

---

### Post by Quarkrad on 2023-10-20
I sort of see what you are suggesting (thank you) but not sure of the detail(s) of what I should change.

---

### Post by aljames2 on 2023-10-20
It could be a NetworkManager thing. Mine used to be a little slow to bring up the internet in my VMs, but not quite 10 seconds slow.  On my kvm host (Xubuntu), I eventually switched my networking to systemd-networkd & use a netplan file to configure everything including the bridge (br0), and I removed NetworkManager.  This works better for me, but certainly not for everyone; especially if you want to use the GUI for networking, and if you allow wireless guest connections, also some DE's depend on NetworkManager for some things.  Everything on my network has a static IP address.  NetworkManager did work fine for me but I just prefer the server style networking like I do in Ubuntu Server.

---

### Post by MAFoElffen on 2023-10-21
I use networkd, and a separate NIC for my bridge. No delays at all...

This is the on-board NIC and another two port SR-IOV NIC, that I have one as my bridge, and the other split out to 7 virtual ports:
```

mafoelffen@msi-ubuntu:~$ sudo grep . /etc/netplan/00-installer-config.yaml
# This is the custom network config written by MAFoElffen
network:
  version: 2
  renderer: networkd
  ethernets:
    enp6s0:
      dhcp4: false
      dhcp6: false
      addresses:
          - 10.0.0.5/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      routes:
          - to: default
            via: 10.0.0.1
            metric: 100
            on-link: true
      mtu: 1500
## Begin SR-IOV on enp7s0f0 
    enp7s0f0:
      virtual-function-count: 7
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v0:
      link: enp7s0f0
      addresses:
          - 10.0.0.10/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v2:
      link: enp7s0f0
      addresses:
          - 10.0.0.12/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v3:
      link: enp7s0f0
      addresses:
          - 10.0.0.13/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v4:
      link: enp7s0f0
      addresses:
          - 10.0.0.14/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v5:
      link: enp7s0f0
      addresses:
          - 10.0.0.15/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v6:
      link: enp7s0f0
      addresses:
          - 10.0.0.16/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
## End SR-IOV on enp7s0f0
## Begin Bridge on enp7s0f1
    enp7s0f1:
      dhcp4: false
      dhcp6: false
      optional: yes
  bridges:
    br0:
      interfaces: [enp7s0f1]
      addresses: [10.0.0.6/8]
      routing-policy:
         - from: 10.0.0.6
           table: 10
      # ** ADDITIONAL ROUTING POLICY **
         - to: 172.16.1.0/24
           table: 172
      # *******************************
      routes:
         - to: 0.0.0.0/0
           via: 10.0.0.1
           table: 10
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1, 1.0.0.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no
      optional: yes
## End Bridge on enp7s0f1

```
That translates to this:
```

mafoelffen@msi-ubuntu:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 04:7c:16:c3:58:a0 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.5/8 brd 10.255.255.255 scope global enp6s0
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::d417/128 scope global dynamic noprefixroute 
       valid_lft 4361sec preferred_lft 4361sec
    inet6 2601:603:4900:77e0:67c:16ff:fec3:58a0/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::67c:16ff:fec3:58a0/64 scope link 
       valid_lft forever preferred_lft forever
3: enp7s0f0v0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether da:74:cf:06:2b:81 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.10/8 brd 10.255.255.255 scope global enp7s0f0v0
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::64f9/128 scope global dynamic noprefixroute 
       valid_lft 4388sec preferred_lft 4388sec
    inet6 2601:603:4900:77e0:d874:cfff:fe06:2b81/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::d874:cfff:fe06:2b81/64 scope link 
       valid_lft forever preferred_lft forever
4: enp7s0f0v5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether 5a:a7:dd:e6:c6:41 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.15/8 brd 10.255.255.255 scope global enp7s0f0v5
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::fe45/128 scope global dynamic noprefixroute 
       valid_lft 3124sec preferred_lft 3124sec
    inet6 2601:603:4900:77e0:58a7:ddff:fee6:c641/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::58a7:ddff:fee6:c641/64 scope link 
       valid_lft forever preferred_lft forever
5: enp7s0f0v1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether 1e:b8:b0:32:81:c8 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.11/8 brd 10.255.255.255 scope global enp7s0f0v1
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::d101/128 scope global dynamic noprefixroute 
       valid_lft 2553sec preferred_lft 2553sec
    inet6 2601:603:4900:77e0:1cb8:b0ff:fe32:81c8/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::1cb8:b0ff:fe32:81c8/64 scope link 
       valid_lft forever preferred_lft forever
6: enp7s0f0v6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether aa:a9:4a:a7:70:67 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.16/8 brd 10.255.255.255 scope global enp7s0f0v6
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::75ff/128 scope global dynamic noprefixroute 
       valid_lft 2803sec preferred_lft 2803sec
    inet6 2601:603:4900:77e0:a8a9:4aff:fea7:7067/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::a8a9:4aff:fea7:7067/64 scope link 
       valid_lft forever preferred_lft forever
7: enp7s0f0v2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether 96:2a:a8:67:fe:3b brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.12/8 brd 10.255.255.255 scope global enp7s0f0v2
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::6a80/128 scope global dynamic noprefixroute 
       valid_lft 3583sec preferred_lft 3583sec
    inet6 2601:603:4900:77e0:942a:a8ff:fe67:fe3b/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::942a:a8ff:fe67:fe3b/64 scope link 
       valid_lft forever preferred_lft forever
8: enp7s0f0v3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether 96:21:7d:53:be:10 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.13/8 brd 10.255.255.255 scope global enp7s0f0v3
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::c80e/128 scope global dynamic noprefixroute 
       valid_lft 2911sec preferred_lft 2911sec
    inet6 2601:603:4900:77e0:9421:7dff:fe53:be10/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::9421:7dff:fe53:be10/64 scope link 
       valid_lft forever preferred_lft forever
9: enp7s0f0v4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq state UP group default qlen 1000
    link/ether 32:59:25:9c:af:37 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.14/8 brd 10.255.255.255 scope global enp7s0f0v4
       valid_lft forever preferred_lft forever
    inet6 2601:603:4900:77e0::5abe/128 scope global dynamic noprefixroute 
       valid_lft 2871sec preferred_lft 2871sec
    inet6 2601:603:4900:77e0:3059:25ff:fe9c:af37/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::3059:25ff:fe9c:af37/64 scope link 
       valid_lft forever preferred_lft forever
10: enp7s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 98:b7:85:01:77:42 brd ff:ff:ff:ff:ff:ff
    inet6 2601:603:4900:77e0::385e/128 scope global dynamic noprefixroute 
       valid_lft 4605sec preferred_lft 4605sec
    inet6 2601:603:4900:77e0:9ab7:85ff:fe01:7742/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::9ab7:85ff:fe01:7742/64 scope link 
       valid_lft forever preferred_lft forever
11: enp7s0f1v0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e2:20:ff:96:89:dd brd ff:ff:ff:ff:ff:ff permaddr 5e:d8:7b:fc:eb:5f
12: enp7s0f1v1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 36:61:46:78:e6:fd brd ff:ff:ff:ff:ff:ff permaddr 5a:d8:0d:91:c4:6d
13: enp7s0f1v2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 32:7a:7d:a2:00:29 brd ff:ff:ff:ff:ff:ff permaddr 0a:31:6d:d3:01:42
14: enp7s0f1v3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ee:72:62:32:22:2f brd ff:ff:ff:ff:ff:ff permaddr 1a:4d:76:a2:32:94
15: enp7s0f1v4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 5a:b2:f6:f6:ad:51 brd ff:ff:ff:ff:ff:ff permaddr aa:52:bf:2f:6f:c0
16: enp7s0f1v5: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 52:2b:2e:db:30:15 brd ff:ff:ff:ff:ff:ff permaddr 86:b5:32:09:09:f8
17: enp7s0f1v6: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 8e:92:2f:2c:6c:97 brd ff:ff:ff:ff:ff:ff permaddr 2a:59:ae:93:bb:7d
18: enp7s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq master br0 state DOWN group default qlen 1000
    link/ether 98:b7:85:01:77:43 brd ff:ff:ff:ff:ff:ff
19: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether a4:f9:33:cc:0e:d9 brd ff:ff:ff:ff:ff:ff
    altname wlp0s20f3
    inet 10.0.0.17/24 brd 10.0.0.255 scope global dynamic noprefixroute wlo1
       valid_lft 143360sec preferred_lft 143360sec
    inet6 2601:603:4900:77e0:9d8b:11bd:db27:a9e8/64 scope global temporary dynamic 
       valid_lft 299sec preferred_lft 299sec
    inet6 2601:603:4900:77e0:83d3:9635:23b4:b0dd/64 scope global temporary deprecated dynamic 
       valid_lft 299sec preferred_lft 0sec
    inet6 2601:603:4900:77e0:a8dc:f87f:652c:509a/64 scope global temporary deprecated dynamic 
       valid_lft 299sec preferred_lft 0sec
    inet6 2601:603:4900:77e0:720f:67dc:93ba:5590/64 scope global temporary deprecated dynamic 
       valid_lft 299sec preferred_lft 0sec
    inet6 2601:603:4900:77e0:efbd:503f:f425:8d81/64 scope global temporary deprecated dynamic 
       valid_lft 299sec preferred_lft 0sec
    inet6 2601:603:4900:77e0:e78a:fe23:befa:930a/64 scope global temporary deprecated dynamic 
       valid_lft 299sec preferred_lft 0sec
    inet6 2601:603:4900:77e0:e679:d463:c7b4:fd3b/64 scope global temporary deprecated dynamic 
       valid_lft 299sec preferred_lft 0sec
    inet6 2601:603:4900:77e0::baa3/128 scope global dynamic noprefixroute 
       valid_lft 4528sec preferred_lft 4528sec
    inet6 2601:603:4900:77e0:c4b4:889d:a033:f95b/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 299sec preferred_lft 299sec
    inet6 fe80::c504:7f74:c1a7:d18f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
20: br0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether a6:5e:15:92:7a:cd brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.6/8 brd 10.255.255.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::a45e:15ff:fe92:7acd/64 scope link 
       valid_lft forever preferred_lft forever
21: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:04:a1:8b brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
22: virbr1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:ba:65:30 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.1/24 brd 192.168.100.255 scope global virbr1
       valid_lft forever preferred_lft forever
23: virbr3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:1a:63:ed brd ff:ff:ff:ff:ff:ff
    inet 192.168.120.1/24 brd 192.168.120.255 scope global virbr3
       valid_lft forever preferred_lft forever
24: virbr2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:4b:30:6d brd ff:ff:ff:ff:ff:ff
    inet 192.168.130.1/24 brd 192.168.130.255 scope global virbr2
       valid_lft forever preferred_lft forever

```

---

### Post by Quarkrad on 2023-10-21
I must say I'm extremely nervous about this - last time I 'played' with my networking set up I messed up badly and had to re-install.  This is my ip a data:

```
dad@dadubuntu:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master nm-bridge state UP group default qlen 1000
    link/ether 2c:f0:5d:92:6d:9e brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:bf:a1:f7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: nm-bridge: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 4e:fc:b1:5b:4c:70 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.9/24 brd 192.168.1.255 scope global noprefixroute nm-bridge
       valid_lft forever preferred_lft forever
```

Looking at your script I think it is beyond my skill level to compare with my set up and to know what to do in detail.  Probably best for me to put up with the delay or go but to NAT rather than Bridge connectivity.  Or maybe wait until I have more skill/experience - perhaps I need to practice and break a VM a few times before I attempt network changes on my live system.

---

### Post by MAFoElffen on 2023-10-21
I am sorry that overwhelmed you. I have some very, very advanced virtual networking going on there, which "most people" do not do, nor do they attempt to do.

***And...*** Before you try to make any changes to your system, you routinely do backups right? So that you can rollback any changes if they didn't work out as planned, right? Always have a fallback plan... Even then, you should have a recent backup of your system. Things do happen, when you least expect them to. I myself, have crashed my own systems, doing things I thought might work... I am only human. Always have a fallback point to go back to.

Before attempting something like this, let me explain what it entails and map it out for you, so you know what is involved. Decisions like this are personal choices.

It is really not as hard as it looked in my last post... Sorry, that was probably not a good example. If I only had one Ethernet adapter, and all I was doing was to create a bridge, then that file would be this instead:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp6s0:
      dhcp4: false
# Begin Bridge on enp6s0
  bridges:
    br0:
      interfaces: [enps0]
      addresses: [10.0.0.5/24]
      gateway4: 10.0.0.1
      mtu: 1500
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
# End Bridge on enp6s0

```
Note that in the above example, the device name "enp6s0" is based on what mine is. Your's would be " eno1" based on your 'ip a' results.

Since you are a fan of Videos: [https://www.youtube.com/watch?v=P-PbTBGF3-g&t=76s](https://www.youtube.com/watch?v=P-PbTBGF3-g&t=76s)

I like that the person in that video is not perfect, makes mistakes, and learns from them... NetPlan files are very picky about spacing and indentation, which watching that video will demonstrate.

What that video did not cover, is that:

[LIST=1]
[*]You are currently on Network Manager... 
[*]You already have a bridge defined in Network Manager... 
[/LIST]
 
So before doing that:

You would need to backup your Network Manager connection files

[LIST=1]
[*]Delete your Network Manager defined bridge 
[*]Turn off the NetworkManager service 
[*]Turn on the systemd-networkd and systemd-resolved services 
[*]"Then" generate and apply your NetPlan config to apply the changes made by your NetPlan File... 
[/LIST]
 
So the config files for Network Manager are in directory /etc/NetworkManager/ssystem-connections... Make sure you have that folder backed up, and/or make backup copies of those files.

You already know how to use nmcli to create a bridge. That is what you would use to delete it.

The commands to change from Network Manager to network would be:
```

sudo systemctl stop NetworkManager
sudo systectl disable NetworkManager
sudo systectl mask NetworkManager
sudo systemctl enable systemd-networkd
sudo systectl start systemd-networkd
sudo systemctl enable systemd-resolved
sudo systemd start systemd-resolved
sudo systectl status systemd-networkd --no-pager
sudo stsemctl status systemd-resolved --no-pager

```
Then you would apply the NetPlan configs:
```

sudo netplan generate
sudo netplan apply

```
The you add your virtual bridge connectio to KVM, which is just a short file and one virsh command... 

If that is something your would like to do? Any further questions? Or is that too much?

Because it "is" working for you now... It just has a delay. 

I tend to avoid Network Manager because if you check your syslog and grep NetworkManager or check that same in your journalctl... It's scary how much errors will display. Most of that is nothing fatally serious. But still...

Make your own decisions based on your system and what you do.

---

### Post by TheFu on 2023-10-21
Set a static IP on the system (inside the VM), not in the bridge settings ... er ... unless a static IP on the host isn't already setup.  Avoid using DHCP, since that is delaying networking.

And you don't need network manager in either system. It is often more trouble than it is worth, IMHO.  Others have different opinions on that.

---

### Post by Quarkrad on 2023-10-24
> **DuckHook said:**
> This happens to me too.

Possibly just your router going "whaa-aat?" from having to assign separate IP addresses to the same physical endpoint. Depending on your router, it may just take that long for it get over the schizophrenia and make the assignment.

Another culprit could be network manager. I've found that it's not very clever and sometimes gets confused with non-default configs.

I've been playing with a VM to get some confidence and have now changed my live system to running without NetworkManager

```
dad@dadubuntu:~$ pidof systemd     &&  echo "systemd"  || echo "other"
1608
systemd
dad@dadubuntu:~$ sudo service systemd-networkd status
&#9679; systemd-networkd.service - Network Configuration
     Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled; ven>
     Active: active (running) since Tue 2023-10-24 08:17:25 BST; 3min 26s ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
   Main PID: 1001 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18710)
     Memory: 2.7M
        CPU: 28ms
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;1001 /lib/systemd/systemd-networkd

Oct 24 08:17:25 dadubuntu systemd[1]: Starting Network Configuration...
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: lo: Link UP
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: lo: Gained carrier
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: Enumeration completed
Oct 24 08:17:25 dadubuntu systemd[1]: Started Network Configuration.
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: eno1: Link UP
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: nm-bridge: Link UP
Oct 24 08:17:26 dadubuntu systemd-networkd[1001]: virbr0: Link UP
Oct 24 08:17:27 dadubuntu systemd-networkd[1001]: eno1: Gained carrier
Oct 24 08:17:57 dadubuntu systemd-networkd[1001]: nm-bridge: Gained carrier
lines 1-23
dad@dadubuntu:~$ systemctl status systemd-networkd
&#9679; systemd-networkd.service - Network Configuration
     Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled; ven>
     Active: active (running) since Tue 2023-10-24 08:17:25 BST; 3min 45s ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
   Main PID: 1001 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18710)
     Memory: 2.7M
        CPU: 28ms
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;1001 /lib/systemd/systemd-networkd

Oct 24 08:17:25 dadubuntu systemd[1]: Starting Network Configuration...
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: lo: Link UP
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: lo: Gained carrier
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: Enumeration completed
Oct 24 08:17:25 dadubuntu systemd[1]: Started Network Configuration.
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: eno1: Link UP
Oct 24 08:17:25 dadubuntu systemd-networkd[1001]: nm-bridge: Link UP
Oct 24 08:17:26 dadubuntu systemd-networkd[1001]: virbr0: Link UP
Oct 24 08:17:27 dadubuntu systemd-networkd[1001]: eno1: Gained carrier
Oct 24 08:17:57 dadubuntu systemd-networkd[1001]: nm-bridge: Gained carrier

```

I have tested my yaml file in /etc/netplan and it passed ok.

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  ethernets:
    eno1:
      dhcp4:  false
      dhcp6:  false
      
      
  bridges:
    nm-bridge:
      interfaces: [eno1]
      addresses:  [192.168.1.96/24]
      routes:
        - to: default
          via: 192.168.1.254
      nameservers:
        addresses:
          - 1.1.1.1
          - 1.0.0.1
          - 8.8.8.8
          - 8.8.4.4
          
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
```

However, it is still taking well over 12 secs for my bridge to make a connection.   Perhaps it is my router *going "whaa-aat?"*.  I'm not sure what I should be looking at in my router to see if this is happening.  Any advice appreciated.

---

### Post by Quarkrad on 2023-10-24
Sorry to go a little off tangent but this doesn't seem right to me:

```
dad@dadubuntu:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master nm-bridge state UP mode DEFAULT group default qlen 1000
    link/ether 2c:f0:5d:92:6d:9e brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:bf:a1:f7 brd ff:ff:ff:ff:ff:ff
4: nm-bridge: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 4e:fc:b1:5b:4c:70 brd ff:ff:ff:ff:ff:ff
```

This, I understand, tells me my  bridge is called nm-bridge (which I have when I originally set the kvm bridge up), but then

```
dad@dadubuntu:~$ virsh net-dumpxml nm-bridge
error: failed to get network 'nm-bridge'
error: Network not found: no network with matching name 'nm-bridge'

dad@dadubuntu:~$ virsh net-list --all
 Name      State    Autostart   Persistent
--------------------------------------------
 default   active   yes         yes

```

Seems to me I have created a bridge called nm-bridge but something is missing.  I'm not sure I have "deleted my Ethernet port" - this is where in the past I have broken my system.   (When I played in the VM is was deleting NetworkManager and using systemd/netplan.  I didn't set up a bridge as such.

---

### Post by MAFoElffen on 2023-10-24
Look at your /etc/netplan .yaml file. If you grep it searching for the string 'renderer', you will come up blank...

Please try adding this as your third line, right below "version: 2", at the same indent column:
```

  renderer: networkd


```

---

### Post by Quarkrad on 2023-10-24
That solved it in terms of the speed of net connection on my host but as before, I'm somewhat lost and fear this virtual Bridge connectivity is not actually working.  My confusion is in the area of the physical ethernet interface in my machine and the virtual bridge (mine is called nm-bridge) - I sometimes read that at some point you delete the ethernet i/f once it is tied to the bridge.  I'm not convinced I've done this - if I have to.  Although I'm doing all this via the terminal the attached shows me graphically my network connections and it appears both my bridge and ethernet interfaces are connected.

Also - my nm-bridge has a problem

```
dad@dadubuntu:~$ sudo systemctl status networking.service
× networking.service - Raise network interfaces
     Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor pr>
     Active: failed (Result: exit-code) since Tue 2023-10-24 20:58:24 BST; 44mi>
       Docs: man:interfaces(5)
    Process: 1052 ExecStart=/sbin/ifup -a --read-environment (code=exited, stat>
   Main PID: 1052 (code=exited, status=1/FAILURE)
        CPU: 94ms

Oct 24 20:58:22 dadubuntu ifup[1107]: /etc/network/if-up.d/resolved: 12: mystat>
Oct 24 20:58:22 dadubuntu ifup[1247]: Cannot find device "netplan-nm-bridge"
Oct 24 20:58:22 dadubuntu ifup[1251]: Waiting for a max of 0 seconds for eno1 t>
Oct 24 20:58:23 dadubuntu ifup[1314]: Cannot find device "netplan-nm-bridge"
Oct 24 20:58:23 dadubuntu ifup[1369]: Waiting for netplan-nm-bridge to get read>
Oct 24 20:58:24 dadubuntu ifup[1469]: Cannot find device "netplan-nm-bridge"
Oct 24 20:58:24 dadubuntu ifup[1052]: ifup: failed to bring up netplan-nm-bridge
Oct 24 20:58:24 dadubuntu systemd[1]: networking.service: Main process exited, >
Oct 24 20:58:24 dadubuntu systemd[1]: networking.service: Failed with result 'e>
Oct 24 20:58:24 dadubuntu systemd[1]: Failed to start Raise network interfaces.
lines 1-18/18 (END)

```

The attachment called bridge name shows that the bridge interface name is nm-bridge but the connection name is netplan-nm-bridge - another source of confusion for me re the name of the bridge in various files.

I have created a ubuntu vm and configured it for bridge working - but unsurprisingly it never makes a connection.  This is from the xml 

```
<interface type="bridge">
  <mac address="52:54:00:5e:1a:b0"/>
  <source bridge="nm-bridge"/>
  <target dev="vnet1"/>
  <model type="virtio"/>
  <alias name="net0"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```

Should the device name be nm-bridge or netplan-nm-bridge?  (note.  changed the xml name to netplan-nm-bridge and it still will not connect so I think my host is actually not using the virtual bridge but a plan/direct ethernet connection).

---

### Post by MAFoElffen on 2023-10-24
What does your xml look like for it?

Here is mine:
```

mafoelffen@msi-ubuntu:~$ virsh net-list
 Name          State    Autostart   Persistent
------------------------------------------------
 default       active   yes         yes
 host-bridge   active   yes         yes
 Isolated      active   yes         yes
 Open          active   yes         yes
 Routed        active   yes         yes

mafoelffen@msi-ubuntu:~$ grep . ./Scripts/host-bridge.xml
<network>
  <name>host-bridge</name>
  <forward mode="bridge"/>
  <bridge name="br0"/>
</network>

```
I define things like that with
```

virsh net-define ./Scripts/host-bridge.xml

```
That adds the define into KVM. Then you start is and have it autostart at boot so you don't have to do it manually again...
```

virsh net-start host-bridge
virsh net-autostart host-bridge

```
Did you do something like that? Because I don't see it defined in your output...

---

### Post by Quarkrad on 2023-10-25
This is my output - so my nm-bridge is not recognised 


```
dad@dadubuntu:~$ virsh net-list
 Name      State    Autostart   Persistent
--------------------------------------------
 default   active   yes         yes

```

At this point I'm afraid to do anything as I've already lost track of what I've done.  Last time I lost all connectivity and had to re-install.

```
dad@dadubuntu:~$ virsh iface-list --all
 Name              State      MAC Address
-------------------------------------------------
 eno1              active     2c:f0:5d:92:6d:9e
 lo                inactive   00:00:00:00:00:00
 netplan-nm-brid   inactive   06:53:6c:85:38:98
 nm-bridge         inactive   4e:fc:b1:5b:4c:70
 virbr0            inactive   52:54:00:bf:a1:f7

```

---

### Post by Quarkrad on 2023-10-25
I'm more than happy to follow text, as well as a video, but there are so many explanations of how to do this, that are subtly different (as versions of software changes) that I get into a mess with things I do not fully understand.

---

### Post by MAFoElffen on 2023-10-25
> **Quarkrad said:**
> 
...
This, I understand, tells me my  bridge is called nm-bridge (which I have when I originally set the kvm bridge up), but then

```
dad@dadubuntu:~$ virsh net-dumpxml nm-bridge
error: failed to get network 'nm-bridge'
error: Network not found: no network with matching name 'nm-bridge'

dad@dadubuntu:~$ virsh net-list --all
 Name      State    Autostart   Persistent
--------------------------------------------
 default   active   yes         yes

```

I didn't set up a bridge as such.
The bridge is define in the system, but not to KVM. See in your output where it say no network with match name 'nm-bridge'? That is why in the next output, that is not found there...

That is why I posted my xml file as an example for you, and the commands that you would need to run (modified to yours) to define it and turn it on...

Okay... Create this file in $HOME/Documents/ named as nm-bridge.xml
```

<network>
  <name>nm-bridge</name>
  <forward mode="bridge"/>
  <bridge name="nm-bridge"/>
</network>

```
Then do these commands
```

virsh net-define $HOME/Documents/nm-bridge.xml
virsh net-start nm-bridge
virsh net-autostart nm-bridge
virsh net-list --all

```
Tell me how that goes for you...

---

### Post by Quarkrad on 2023-10-26
Thank you - that seemed to go well

```
dad@dadubuntu:~$ virsh net-define $HOME/Documents/nm-bridge.xml
Network nm-bridge defined from /home/dad/Documents/nm-bridge.xml

dad@dadubuntu:~$ virsh net-start nm-bridge
Network nm-bridge started

dad@dadubuntu:~$ virsh net-autostart nm-bridge
Network nm-bridge marked as autostarted

dad@dadubuntu:~$ virsh net-list --all
 Name        State      Autostart   Persistent
------------------------------------------------
 default     inactive   no          yes
 nm-bridge   active     yes         yes

```

I will now reboot and see what happens

---

### Post by Quarkrad on 2023-10-26
Wow - I think I am there.  I have created a vm (ubuntu mate 22.04) with a static ip (192.168.1.30) that is configured to have bridge networking to my nm-bridge  interface.  At the moment from my host I can ping the vm and from the vm ping my bridge all with in the 192.168.1.x range (the bridge has a fixed ip of 192.168.1.96).  

```
dad@dadubuntu:~$ ip a s
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master nm-bridge state UP group default qlen 1000
    link/ether 2c:f0:5d:92:6d:9e brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
3: nm-bridge: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 4e:fc:b1:5b:4c:70 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.96/24 brd 192.168.1.255 scope global nm-bridge
       valid_lft forever preferred_lft forever
    inet6 2a00:23c8:4198:e201:4cfc:b1ff:fe5b:4c70/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 289sec preferred_lft 109sec
    inet6 fe80::4cfc:b1ff:fe5b:4c70/64 scope link 
       valid_lft forever preferred_lft forever
4: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master nm-bridge state UNKNOWN group default qlen 1000
    link/ether fe:54:00:bd:21:aa brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:febd:21aa/64 scope link 
       valid_lft forever preferred_lft forever

```

However, I do not know what the ip is of my host - I would like my host to have a static ip as well.

```
dad@dadubuntu:~$ ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 2c:f0:5d:92:6d:9e  txqueuelen 1000  (Ethernet)
        RX packets 15285  bytes 8019212 (8.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8051  bytes 1132676 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0x8e500000-8e520000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1875  bytes 250115 (250.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1875  bytes 250115 (250.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

nm-bridge: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.96  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2a00:23c8:4198:e201:4cfc:b1ff:fe5b:4c70  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::4cfc:b1ff:fe5b:4c70  prefixlen 64  scopeid 0x20<link>
        ether 4e:fc:b1:5b:4c:70  txqueuelen 1000  (Ethernet)
        RX packets 13921  bytes 7669060 (7.6 MB)
        RX errors 0  dropped 3905  overruns 0  frame 0
        TX packets 7305  bytes 1043372 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:febd:21aa  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:bd:21:aa  txqueuelen 1000  (Ethernet)
        RX packets 231  bytes 24618 (24.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5489  bytes 864380 (864.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Thank you for your time on this and helping me - this has been quite a journey!

---

### Post by MAFoElffen on 2023-10-26
Your IP of the host is actually 192.168.96 shared with your bridge (set in the nm-bridge section of your netplan yaml file). That is why I set that as static there, when there is  only one NIC, and it needs to "share it" to make it work. (Explanation to TheFU who was wondering about the why of that.) 

If you try to set anything for "en01" in the host section, then the NIC will not share the device and the bridge device will fail.

This type of config works okay for machines like laptop's where there is only a room internally to have one single internal NIC... (But still possible to add an USB Ethernet NIC as a second.) If I have a machine with KVM, and if there is any way to add a second NIC, then I do, and set one with my dedicated Static IP, and the other dedicated as a bridge for KVM.

---

### Post by MAFoElffen on 2023-10-27
If this is fixed for you... It seems as such... Then you are responsible to mark your thread as solved.

Visit the "Thread Tools" link in the upper right of the first page of a thread, ad mark it as "Solved". This really help other users later who search on answers for their similar problems to see what worked for you.

---

