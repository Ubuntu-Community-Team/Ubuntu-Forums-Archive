---
title: "Cannot install gueat on Virtualbox..."
date: 2009-07-04
forum: Virtualisation
---

### Post by RadarBat on 2009-07-04
Host = Ubuntu 9.04-AMD64
Guest = Eeebuntu 9.04-Standard......(Installed okay)
Guest = Eeebuntu 9.04-NBR...........(Installed okay
Guest = Easy Peasy 9.04.............(Will not install) It gets to "82% -Scanning Mirror" and locks up. The first two guests lock up when I try to do an update (Update Manager). It must be something with tha eth0 connection because they lock up when I try to access the Internet.
Specs (on all three) = 25 GB virtual hard drive, 500 MB RAM, 64 MB Video RAM. What is wrong?:confused:

---

### Post by Perryg on 2009-07-05
What mode are you using to connect these machines to the host?  NAT, Bridged, host only, internal only and the version of VBox would help.

Depending on the version most usually it is the Virtual adapter you choose.  By default it will be the PCnet III and you may need to switch it to a different adapter.  
Another problem depending again on the version, is NAT which had issues in 2.0.X and DNS.

---

### Post by RadarBat on 2009-07-06
> **Perryg said:**
> What mode are you using to connect these machines to the host?  NAT, Bridged, host only, internal only and the version of VBox would help.

Depending on the version most usually it is the Virtual adapter you choose.  By default it will be the PCnet III and you may need to switch it to a different adapter.  
Another problem depending again on the version, is NAT which had issues in 2.0.X and DNS.

NAT (out-of-the-box). Version 3.0 VirtualBox. Thanks for the reply.  RB

---

### Post by Perryg on 2009-07-06
The first thing I would try is to switch to the IntelPRO/1000 Mt driver and see if it will complete the network mirror download.  Some Distros. are none to happy with the PCNet drivers in Version 3.0.0 and especially with NAT.  Let me know if this does not work and we can do some more checking.

---

### Post by Sean_L on 2009-07-06
Similar/Same problem:

I am trying to host Ubuntu 9.04 using virtualbox 3.0 in Mac OS X and am getting to a similar point in the installation. 

My settings are:  
System:
Base Memory: 768MB
Extended Features: Enabled IO APIC 
VT-x/AMD-V: Enabled 

Display:
12MB
3d Acceleration : Enabled

Network Adapter Enabled :
Adapter 1
Intel Pro/1000 MT Desktop (82540EM)
Attached to: NAT

I tried with the PC net drivers and was not successful. Do you have any thoughts on this? 
Maybe a bad CD/DVD?

---

### Post by Perryg on 2009-07-06
MACs are a little different.  Most people that I know that use them with VBox need to turn on the passthrough for the CD/DVD to get them to work properly.  But if you have changed the adapter to Intel and are still freezing at the same spot I would start to consider the CD may be bad.

---

### Post by RadarBat on 2009-07-06
I am now running xubuntu 9.04 guest on ubuntu 9.04 host....and have just received 113 updates at my max rate (596 KB/s). Everything seems to be working OK.

SETUP for the Virtual Machine was:
541 MB RAM, 1 processor, AMD-V enabled, Nested Paging disabled,  16 MB Video RAM, 3D Acceleration disabled, Primary IDE Master=12.21 GB, Network adapter Intel PRO/1000 MT Desktop (82540EM) attached to NAT.

Thank you, Perryg for your input & help.

---

### Post by RadarBat on 2009-07-06
Did you check the md5 on the .iso? Did you put yourself in the "vboxusers" group?
On every attempted guest install (whatever the distro), it halted at 82% ("Scanning Mirror") and froze **until** I changed the network adapter to the Intel PRO/1000.

---

