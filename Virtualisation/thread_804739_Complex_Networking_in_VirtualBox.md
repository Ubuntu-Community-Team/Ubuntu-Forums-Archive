---
title: "Complex Networking in VirtualBox"
date: 2008-05-23
forum: Virtualisation
---

### Post by pokkits on 2008-05-23
Hello Community! 

I have a question regarding networking in VirtualBox on Ubuntu Hardy. 
I'm trying to use Host Interface Networking. 
I'm trying to achieve a setup where my host pc w/ a single physical nic is assigned a static ip address, but the guest OS'es obtain a dhcp address by default, which could then possibly be changed to static from within the guest OS. 
I have accomplished this in WindowsXP running VirtualPC, creating virtual environs that run Server2003, XP, Fedoa, and Ubuntu. They boot with dhcp, but if configure the ve's to run some kind of service, i can then assign them static addresses. The host all the while has a static IP. 

Is this possible? How do I configure eth0, br0, and tap0-4 to get this fuctionality?
The idea is to have all the computers (real and virtual) on the same network (10.1.x.x. 255.255.0.0) and access to the internet thru the same gateway (10.1.1.254). Host is always static (10.1.6.66)

---

### Post by MystaMax on 2008-05-23
I believe you want to bridge your network connection, here are some links to do so:

**[http://tinyurl.com/626wqx](http://tinyurl.com/626wqx) - **Samiux's blog[B]
[http://tinyurl.com/3dzkp4](http://tinyurl.com/3dzkp4) - [/B]ubuntu Documentation[B]
[http://tinyurl.com/5m57ls](http://tinyurl.com/5m57ls) - [/B]John Hun'ts blog - Wireless bridging

good luck!

---

