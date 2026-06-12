---
title: "How Many VMWare Appliances Can Access 1 NIC"
date: 2008-07-08
forum: Virtualisation
---

### Post by mesocal on 2008-07-08
I have a sweet fully loaded Dell PowerEdge 2900 (not like it makes that much of a difference).  Anyhow, i have two Gig Ethernet cards in there.  My question is how many XP (or any for that matter) appliances can I have up and running at the same time using 1 nic.  I've only been running 4 or 6 appliances at the same time and now my network connection from the XP appliances has been terrible.  

Is there a limit to how many appliances can use a nic? Or is this a setup issue?

Let me add that I am using the vmware server 1.05

---

### Post by fjgaude on 2008-07-08
Looking over the vmware server manual I don't see anything where a limit is placed of a NIC with a NAT function.

Tough to get info on what you are looking for, a limit on a NIC.

---

### Post by mesocal on 2008-07-08
thanks.  I can't find anything on it either.  It could be my connection, although it is a T1.  I wonder if it has anything to do with the VM Server and XP (couldnt imagine that it would, but . . .)

---

### Post by fjgaude on 2008-07-08
I run vmware WinXP guest under Ubuntu 8.04 host and a 6Mb/sec DSL NAT connection... all very quick. Like four T1s. <smile>

---

### Post by Chris33478 on 2008-07-08
I haven't found anything on suggested guest to NIC ratios for VMWare Server (which is based on the older GSX version). However, I know in our production environment using ESX 3.5 we have a functional limit of 25 guests per NIC.

Granted the hosts are pretty beefy SAN attached Dell R900s (Quad Quad-core with 64 GB of RAM) and that's only taking moderate network usage from the guests.

How hard are you working the guest systems?

-Chris

---

### Post by mesocal on 2008-07-08
on a few of the guests, we are working them quite hard.  we setup a couple of guest as our server and we are constantly making sql calls to them.  but even with they are idle,  our connection lags.

---

### Post by fjgaude on 2008-07-08
> **mesocal said:**
> on a few of the guests, we are working them quite hard.  we setup a couple of guest as our server and we are constantly making sql calls to them.  but even with they are idle,  our connection lags.

And a T1 is no longer considered much in the way of through-put... connection lag... what does it show in terms of bytes/second?

---

### Post by Chris33478 on 2008-07-08
> **fjgaude said:**
> And a T1 is no longer considered much in the way of through-put... connection lag... what does it show in terms of bytes/second?

Frank has a good point. Have you thrown up any monitoring to get a feel for the environment? Some SysMon counters for CPU, RAM, HHD, and NIC usage and bottlenecking would be useful. Also EtherApe on your hosts will help you see where the bockage is if it's on the network side.

-Chris

---

