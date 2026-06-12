---
title: "Two Ubuntu VM's can't reach each other on VirtualBox network"
date: 2018-01-25
forum: Virtualisation
---

### Post by timothylegg on 2018-01-25
I was referred here by a member of the VirtualBox forum that believes the network issue I am facing is an Ubuntu configuration issue instead of a VirtualBox issue.

[https://forums.virtualbox.org/viewtopic.php?f=7&t=86395](https://forums.virtualbox.org/viewtopic.php?f=7&t=86395)

I have two machines named Frick and Frack.  They are also known as 192.168.10.10 and 192.168.10.20 and have been assigned those as a static IP. They are running Ubuntu 16.04 and are a relatively fresh install with very little done to them other than installing vim, ssh and pv packages.

Presently, the /etc/network/interfaces reads as follows

```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp0s3
iface enp0s3 inet static
address 192.168.10.10
netmask 255.255.255.0
gateway 192.168.10.1
```

The other machine differs only in the address parameter.  Within the network configuration of VirtualBox, each of these machines are set to be "Internal Network" as they need to communicate with each other, but don't need to interact with any other devices.

I can ssh into my own IP address, such as machine 192.168.10.10 being able to ssh to 192.168.10.10, but not to 192.168.10.20 as there is "No route to host"

I was suggested to try this command:

sudo route add default gw 192.168.10.1 enp0s3

but that made no difference, even after rebooting.

I'm running out of ideas...  How can I get these two VM's to communicate with each other?

[COLOR=#800080]
[/COLOR]

---

### Post by deadflowr on 2018-01-25
*Thread moved to **Virtualization** *

---

