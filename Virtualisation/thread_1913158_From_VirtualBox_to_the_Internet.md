---
title: "From VirtualBox to the Internet"
date: 2012-01-22
forum: Virtualisation
---

### Post by 2bob on 2012-01-22
Okay! I got to study Windows server 2008 and I have this problem now:
I got VirtualBox on Ubuntu 11.10, 64 bit. Inside I got 4 servers, connected to internal network: s0, s1, s2 and s3, all of them windows server 2008. 
How do I get them to connect to the internet through s0 as a gateway? 
If I connect them to NAT there is no problem but this is not the idea because they interfere with the host's connection slowing it down, and I need to “see” this network working like being behind a firewall.
Thanks in advance.

---

### Post by japzone on 2012-01-22
Do you mean you want the VM servers to connect to the Net but be accessible from your own LAN and Host OS? If so simply open the Settings of the VM in VirtualBox and then go to Networking and change the Device from NAT to Bridge, select your Host's Network Adapter that connects to the Net/LAN. Boot your server and it should now connect to the Internet via your Router's DHCP and now be available on your Network just like any other Computer.

---

### Post by memilanuk on 2012-01-22
On the settings for s0 add a second network card and set it for either NAT (if you don't care about being able to get 'in' to the VMs thru the connection easily) or Bridged (if you do).  Configure that machine to be a gateway for the other VMs on the internal network.  

I do much the same thing using dedicated Linux 'router' distros like Vyatta or Smoothwall.  I have found that it makes life easier, or at least less confusing if you pick a different make/model for the second network card in Virtualbox - otherwise you're down to having to look at the MAC addresses to tell them apart when trying to set up which one is facing 'in' and which one is facing 'out' - and at least in Linux, not every distro shows you that during the install, you just see two identical cards and have to guess (usually wrong!) ;)

HTH,

Monte

---

### Post by Cheesemill on 2012-01-22
> **memilanuk said:**
> On the settings for s0 add a second network card and set it for either NAT (if you don't care about being able to get 'in' to the VMs thru the connection easily) or Bridged (if you do).  Configure that machine to be a gateway for the other VMs on the internal network.  

I do much the same thing using dedicated Linux 'router' distros like Vyatta or Smoothwall.  I have found that it makes life easier, or at least less confusing if you pick a different make/model for the second network card in Virtualbox - otherwise you're down to having to look at the MAC addresses to tell them apart when trying to set up which one is facing 'in' and which one is facing 'out' - and at least in Linux, not every distro shows you that during the install, you just see two identical cards and have to guess (usually wrong!) ;)

HTH,

Monte


+1

I do exactly the same with my VM setup, using SmoothWall as a gateway for the other machines on the internal network.

---

### Post by 2bob on 2012-01-23
Thanks a lot for the ideas. I'll try them all today.:D

---

