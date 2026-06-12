---
title: "Automatic IP change although configured to static"
date: 2016-04-08
forum: Server Platforms
---

### Post by rcacurs on 2016-04-08
Hello. 
Having issue with IP address random change for network adapter although it is set to be static. The IP gets rteset to address that was assigned by DHCP server when OS was installed although after installation it set to be static.
Using Ubuntu 14.04.4 Server with MAAS 1.9.

Default installation sets network interface for dynamic IP with dhcp (and as far as I know there is no way to change that while installing). I want to use static ip so after installation i do these configuration steps:

1. set region controller for static ip intended to use
```
 sudo dpkg-reconfigure maas-region-controller
```
2. set cluster controller for stati ip intented to use
```
sudo dpkg-reconfigure maas-cluster-controller
```
3. Change settings for network adapter to use static ip address in /etc/network/interfaces
```

# content
auto em2
iface em2 inet static
address 10.13.137.133
gateway 10.13.137.254
netmask 255.255.255.0

```
4. restart network interface
```
sudo ifdown em2 && sudo ifup em2
```

After this configuration everything seems to work for a while, but after some time interval (~1 hour). The IP address for particular network inteface gets changed back to value that was assigned by DHCP server. Interesting part is that network configuration file /etc/network/interfaces is not changed and ip address setting is set to static

Output of ifconfig for em2 inteface:

```
em2       Link encap:Ethernet  HWaddr 98:be:94:29:e7:72            
          inet addr:10.13.137.156  Bcast:10.13.137.255  Mask:255.255.254.0
          inet6 addr: fe80::9abe:94ff:fe29:e772/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:861101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:237023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:688604589 (688.6 MB)  TX bytes:18099047 (18.0 MB)
          Memory:c4580000-c459ffff 
```

What could be the reason for this?

---

### Post by Bucky Ball on 2016-04-08
*Thread moved to **Server Platforms**. *

---

### Post by SeijiSensei on 2016-04-08
Have you tried setting the static address to an IP outside the range served by the DHCP server?

Are you running a server version or a desktop version? Which one?

---

### Post by darkod on 2016-04-08
You mentioned you are also using MAAS. I haven't used it, but reading the brief introduction, the question is whether the machine in question is the controller or a node? Because nodes are supposed to get IP by dhcp from the MAAS setup, right? Not sure if you can change the node to static IP.

As for initial installation, again I am not sure for lubuntu, but for ubuntu server you can stop it getting configured for dhcp. Towards the start of the install process, when it shows the screen saying something like "configuring network with dhcp" you need to be fast and hit Enter. The Cancel option is already highlighted so you only have to hit Enter before that screen/message changes. I usually wait for it ready with the finger on the key. :)

After that it will ask you if you want to configure the network manually in which case you can enter IP, netmask, gateway, dns servers, etc...

But going back to your current issue, could it be related to the MAAS???

---

### Post by rcacurs on 2016-04-11
I am running server version. And the static IP address used was outside the IP range of DHCP server

---

### Post by rcacurs on 2016-04-11
> **darkod said:**
> You mentioned you are also using MAAS. I haven't used it, but reading the brief introduction, the question is whether the machine in question is the controller or a node? Because nodes are supposed to get IP by dhcp from the MAAS setup, right? Not sure if you can change the node to static IP.

As for initial installation, again I am not sure for lubuntu, but for ubuntu server you can stop it getting configured for dhcp. Towards the start of the install process, when it shows the screen saying something like "configuring network with dhcp" you need to be fast and hit Enter. The Cancel option is already highlighted so you only have to hit Enter before that screen/message changes. I usually wait for it ready with the finger on the key. :)

After that it will ask you if you want to configure the network manually in which case you can enter IP, netmask, gateway, dns servers, etc...

But going back to your current issue, could it be related to the MAAS???

The machine in question is the controller. 
Good Idea to cancel network configuration through dhcp when installing.  Setup screen was to short to notice cancel button :) But still it would be better if it would be possible to reconfigure to static IP after the installation.

---

### Post by darkod on 2016-04-11
You definitely can reconfigure to static IP, at least ubuntu server. I have done it various times.

Your settings in /etc/network/interfaces seem correct so I am also puzzled what could change your IP.

---

