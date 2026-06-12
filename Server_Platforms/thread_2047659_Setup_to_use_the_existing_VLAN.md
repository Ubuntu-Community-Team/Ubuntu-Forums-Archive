---
title: "Setup to use the existing VLAN"
date: 2012-08-25
forum: Server Platforms
---

### Post by bakegoodz on 2012-08-25
I setting up some servers, but the Network Admin set it up so I have to use VLAN 51. It was easy on my ESXi server I just put in the 51 into the VLAN menu. I can't find what I need to put /etc/network/interfaces on my Ubuntu server. All the the instructions I find instruct how to create a VLAN in Linux. I just want it to use existing VLAN 51. How do I do that?

---

### Post by darkod on 2012-08-25
I think it's very easy, in /etc/network/interfaces you simply use something like eth0.51 instead of eth0.

Have you tried that?

---

### Post by LHammonds on 2012-08-25
I guess your VLAN is not controlled by the IP addresses being used?  For my network, I do not have to concern myself with VLANs.  That is handled by my switch/router guy.  I don't have to do anything at the server configuration level.

---

### Post by The Cog on 2012-08-25
You need to install the vlan module first:
```
sudo apt-get install vlan
```
You may need to then load the vlan module:
```
sudo modprobe 8021q
```
Then you can add the vlan to the physical interface:
```
sudo /sbin/vconfig add eth0 51
```


But this guide looks good:
[http://www.mysidenotes.com/2007/08/17/vlan-configuration-on-ubuntu-debian/](http://www.mysidenotes.com/2007/08/17/vlan-configuration-on-ubuntu-debian/)

---

### Post by bakegoodz on 2012-08-25
Awesome Thanks. :guitar: Yea!, I'll have to manually install the deb file on a flash drive before I can get network service.

---

### Post by bakegoodz on 2012-08-27
Awesome, thanks! Turned out VMware ESXi handles VLAN tagging, so it not needed on the Ubuntu server running in ESXi. I needed to put VLAN 51 in also "VM Network", not just the Management Network.

---

