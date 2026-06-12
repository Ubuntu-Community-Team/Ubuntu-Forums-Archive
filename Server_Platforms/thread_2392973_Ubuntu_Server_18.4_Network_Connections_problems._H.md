---
title: "Ubuntu Server 18.4 Network Connections problems. Help please."
date: 2018-05-28
forum: Server Platforms
---

### Post by daniel228 on 2018-05-28
Well gyes,

After much trouble I have managed too get Ubuntu 18.4 LTS on my rack, and I have done a full "sudo upgrade" and "full sudo update."

Next was the xubuntu-desktop installation for ease of use. I found several online guides.

I have rebooted the system and now I have no internet connectivity on the server as the network connections are showing up as "Device Unmanaged"

I followed this guide but it has done nothing.

[https://askubuntu.com/questions/1031956/network-manager-not-working-when-installing-ubuntu-desktop-on-a-ubuntu-18-04-ser](https://askubuntu.com/questions/1031956/network-manager-not-working-when-installing-ubuntu-desktop-on-a-ubuntu-18-04-ser)

Is anyone able too advise on how too get my internet connection up and running on 18.4 Ubuntu LTS. I have tried the above but really have no idea were too start. When I ping Google I get "Destination Unreachable."

Thanks gyes in advance.

---

### Post by daniel228 on 2018-05-28
Gyes,

I think I have figured out the problem hear for all the problems I have had in regards too the last two days.

 I have two switches running. One connected too the other like a daisy chain. I have had my server Via: Ethernet plugged in too the second switch with another Ethernet for Internet connectivity Via: Port 24 and my original Server port on the switch connected to port 1.

I have had a daisy chain heading up the tree as I eventually hit my pfsense custom firewall, bridged with my ISP box.

I have unplugged the Ethernet and connected it directly too the first switch and I have been able too ping googles servers and also set up ssh on my main client terminal with my ubuntu rack 18.4 .

8.8.8.8 is receiving requests and I'm getting no packet loss.

---

