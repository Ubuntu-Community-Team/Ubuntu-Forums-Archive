---
title: "How to connect from home PC to Virtualbox/KVM that hosted on Ubuntu server"
date: 2015-05-07
forum: Virtualisation
---

### Post by Quan_Nguyen on 2015-05-07
Hi. I have an Ubuntu server, it's 3TB HDD space total and 24GB RAM, I want to take 1 little bit of space and RAM to make VPS Windows using VirtualBox or KVM.

<strong>I want to install Windows Server 2008 on VirtualBox OR KVM, and I want to remote desktop from my home PC directly to the VPS I create with Vitualbox, and with network on.</strong>


But after searching internet for 2 days, I couldn't make it work, especially for the network part.

Here is my /etc/network/interfaces file : 

 ```
Hetzner Online AG - installimage
 Loopback device:
auto lo
iface lo inet loopback
  device: eth0
 auto  eth0

iface eth0 inet static
    address   46.4.21.70
     broadcast 46.4.21.127
    netmask   255.255.255.192
    gateway   46.4.21.65
     # default route to access subnet
     up route add -net 46.4.21.64 netmask 255.255.255.192 gw 46.4.21.65 eth0
iface eth0 inet6 static
     address 2a01:4f8:131:410c::2
     netmask 64
      gateway fe80::1

```


The ifconfig command: 
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:7a:e8:62
          inet addr:46.4.21.70  Bcast:46.4.21.127  Mask:255.255.255.192
          inet6 addr: fe80::6e62:6dff:fe7a:e862/64 Scope:Link
          inet6 addr: 2a01:4f8:131:410c::2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:302059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:392562631 (392.5 MB)  TX bytes:10964261 (10.9 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:42736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3754256 (3.7 MB)  TX bytes:3754256 (3.7 MB)

```

The IP 46.4.21.70 is my Ubuntu server IP.

I tried set up network for the Virtualbox using NAT : could connect to the internet if using Virtualbox start from it, but I heard people say NAT can't be seen by outside world.

I tried selected Bridged Adapter : 
[IMG]http://ultraimg.com/images/Capture87cc9.jpg[/IMG]
 : 
No internet access and here is the ipconfig I did on Windows server in Virtualbox
[IMG]http://ultraimg.com/images/Capture17e8de.jpg[/IMG]

I'm very noob on this network thing, could anyone show me step by step how to do it, would be appreciate :D.

---

### Post by TheFu on 2015-05-07
Pick either KVM 
or Virtualbox.  For running a desktop on a desktop, virtualbox is generally best. 

You'll need to understand networking much more too. The interfaces file above shouldn't work. There are lines that don't make sense and should break the configuration.
Hetzner - that line cannot be in the file. There are others like that. No extra lines are allowed.

[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) explains normal Linux networking.
[https://help.ubuntu.com/community/KVM/Networking#bridgednetworking](https://help.ubuntu.com/community/KVM/Networking#bridgednetworking) explains KVM's use of normal Linux bridge networking.

I suspect the default networks setup by either libvirt or virtualbox are NAT to protect you from yourself. If you want a bridge, you should create it manually.

Cannot help with anything on Windows Server - never touch it myself.

---

### Post by Quan_Nguyen on 2015-05-07
> **TheFu said:**
> Pick either KVM 
or Virtualbox.  For running a desktop on a desktop, virtualbox is generally best. 

You'll need to understand networking much more too. The interfaces file above shouldn't work. There are lines that don't make sense and should break the configuration.
Hetzner - that line cannot be in the file. There are others like that. No extra lines are allowed.

[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) explains normal Linux networking.
[https://help.ubuntu.com/community/KVM/Networking#bridgednetworking](https://help.ubuntu.com/community/KVM/Networking#bridgednetworking) explains KVM's use of normal Linux bridge networking.

I suspect the default networks setup by either libvirt or virtualbox are NAT to protect you from yourself. If you want a bridge, you should create it manually.

Cannot help with anything on Windows Server - never touch it myself.

Hetzner is my server provider, and it was one of some lines that are comment out on the real file on my server.

I figured out how to achieve what I want by using NAT, and port forward it. It's really easy than what I thought, but couldn't get to work by using Bridge.

---

### Post by TheFu on 2015-05-07
Whenever you post files - please post the EXACT FILE!!!!!!!   so we don't waste our time.

---

### Post by Quan_Nguyen on 2015-05-07
> **TheFu said:**
> Whenever you post files - please post the EXACT FILE!!!!!!!   so we don't waste our time.

why you so mad? that is the exact files. I dont edit, modify, add  anything. The only thing is the first two line are comment out "#", everyone knows if it's not right, my server will not working and I can not login. But that's the default file of Hetzner.


I dont see a reason to get mad in this situation :). If you can help me, I would be appreciated.

---

