---
title: "ClamAV-freshclam does wierd on network"
date: 2010-04-25
forum: Server Platforms
---

### Post by WimVM on 2010-04-25
Hello,
 
I have installed my first Ubuntu server today. It is connected to our corporate network. On this network there is a Windows 2008 R2 server that serves as DNS Exchange and file server. For some unknown reason this Windows server looses network connection when the ubuntu server comes online. 
After some investigation the network connection is instantly restored when I stop the clamav-freshclam service on the ubuntu server. When I start the service the network connection of the Windows server goes down.
The only "link" with the Windows service and the Ubuntu server is that the Windows server is configure as the nameserver on the ubuntu server.
 
Wierd situtation. I want to run this in production because the ubuntu will serve as anti-spam server. I need to understand what is happing and why to prevent this. Any idea?

---

### Post by WimVM on 2010-04-26
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Hello,
 
I did some extra tests without any success at the moment. The problem stays the same and can be reinitiated. When I open a continues ping to our domain controller from a workstation on the network, it replies correctly. As soon as I start the service ClamAV-freshclam on the ubuntu server it goes instantly in requested timed out. When I stop the service the network connection is restored.
There is no duplicate IP setting or so involved. Checked all settings, nothing abnormal can be found. Why and especially why is it happing with the domain controller... really makes no sense.
[/SIZE][/FONT][/SIZE][/FONT]

---

