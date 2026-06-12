---
title: "VirtualBox 3.2 Access Guest from Host Works"
date: 2010-07-18
forum: Virtualisation
---

### Post by owenjwest on 2010-07-18
All,

Just wanted to say a quick thanks to all the gurus out there. I've been trying for the past two days to get access to a SQL Server on my VBox XP guest from my Ubuntu 10.04 host and finally figured it out! Steps below:

1. Use Bridged Networking in VBox. Easy as pie in VBox 3.6 - just set adapter type to Bridged, then choose your host physical network (eth1 for me) and select the adapter type (PCNet-FAST III)

2. Boot into the XP guest and give it a static IP - I used an address in the 192.168.1 range. 

3. The big one! TURN OFF THE WINDOWS FIREWALL!!! This is what took me two days to figure out.

Anyhow, thanks to everyone who's posted on this topic, you've all been extremely helpful! :p

---

