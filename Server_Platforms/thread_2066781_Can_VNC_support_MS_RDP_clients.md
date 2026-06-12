---
title: "Can VNC support MS RDP clients?"
date: 2012-10-05
forum: Server Platforms
---

### Post by MakOwner on 2012-10-05
I have a (maybe) odd setup where I need a solution - I have a lab that is setup inside a private company network.  for various reasons, we are using a Linux NAT firewall to enclose a section of the lab so that we can have a larger network without using company provided IP addresses, and contain the DHCP and DNS services needed for some applications.

We set the RED interface of the firewall on a company provided IP address, set up a Windows VM on the same network, and configured OpenVPN on the Windows VM to allow a route into the private network.
This works, but is generally annoying as we have obvious stability issues with Windows 2003/2008 server in this capacity.  

Is it possible to set up VNC on a linux desktop so that the clients that have only MS RDP clients can access it without having to install a VNC client?

---

### Post by HermanAB on 2012-10-05
Try rdesktop.

---

### Post by MakOwner on 2012-10-18
> **HermanAB said:**
> Try rdesktop.

Maybe I'm missing something - it looks like rdesktop is a client that can attach to MS terminal services and give you access to a Windows desktop from a linux client.  I need it the other way round.

I need to set up a linux server that will provide a desktop-in-a-window on a Windows client.  

Or have I completely misunderstood rdesktop?


xrdp seems to be the solution - installed and started up as part of the installation and I can connect from an XP desktop using default RDP client settings.
Exactly what I was looking for.

---

### Post by albandy on 2012-10-18
> **MakOwner said:**
> Maybe I'm missing something - it looks like rdesktop is a client that can attach to MS terminal services and give you access to a Windows desktop from a linux client.  I need it the other way round.

I need to set up a linux server that will provide a desktop-in-a-window on a Windows client.  

Or have I completely misunderstood rdesktop?


If you want to connect some windows clients to a linux server with graphical environment you need something like NX Application Server.

---

