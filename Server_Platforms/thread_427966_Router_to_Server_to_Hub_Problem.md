---
title: "Router to Server to Hub Problem"
date: 2007-04-29
forum: Server Platforms
---

### Post by Darko-TheRaven on 2007-04-29
Related to topic: [http://ubuntuforums.org/showthread.php?t=189458](http://ubuntuforums.org/showthread.php?t=189458)

I am trying to setup a subnetwork whose topology is as follows. I have a Cable modem that feeds to a 108-super g NETGEAR Wireless router, to which i have an ubuntu 7.04 server connected through an asus wireless NIC. In this server i have the asus NIC and a Fast Ethernet wired nic that feeds into the uplink port of my hub that feeds to other desktop machines.

Depiction:

{Cable Modem}=={Router}__|* ) ) Wireless ) ) *|__[Server Box]==={Hub}==[Desktop Machines]

What DHCP program would you recommend running on the server to allow the desktops to access the internet?

---

### Post by Darko-TheRaven on 2007-04-30
Sorry bout the above post, here is the problem more clearly now:

Problem:
I want to use different servers for HTTP, FTP, and game servers so that one server is not crashed by the processing load for all three service types. the servers must connect wirelessly to Internet. the problem is only 1 wireless card. I figure that by using a server as a router i can link the other computers through it to Internet.

How I plan to do this:
**computers** connected to the **hub** form their own network. The **hub**'s uplink port is connected to the **wired eth0 interface** of the **server**. The **server** connects **wirelessly** through **physicaly seperate** interface **ra0** to the **router** for my home network. This **router** connects to the **internet**.

What I know must happen:
[LIST]
[*]I know that traffic from eth0 must be routed to ra0.
[*]The server must function as a router.
[/LIST]

Questions:
[LIST=1]
[*]How can i acomplish the above.
[*]Since I am using a hub to connect multiple computers to eth0 of the server, do I need to manualy subnet.
[/LIST]

EDIT:
Also i have read through posts about usind two different ethernet cards, but am not sure about an ethernet and wireless.

---

