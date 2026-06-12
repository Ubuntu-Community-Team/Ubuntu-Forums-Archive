---
title: "Turning Old PC into Server: Want to partition HD for proxy email vpn ftp"
date: 2017-03-10
forum: Server Platforms
---

### Post by prc12 on 2017-03-10
Hey, I am learning about networks quickly, but I was wonder about the best practice to partition your HD and host your vpn, proxy, email and webpage on each partition. Can i get some help? Or should you just host in one partition?

---

### Post by ajgreeny on 2017-03-11
*Thread moved to **Server Platforms**.* which is more appropriate and a better fit.

---

### Post by TheFu on 2017-03-11
> **prc12 said:**
> Hey, I am learning about networks quickly, but I was wonder about the best practice to partition your HD and host your vpn, proxy, email and webpage on each partition. Can i get some help? Or should you just host in one partition?

Welcome to the forums.  Disk partitioning isn't really the way these things are normally split up.  Different services are normally run on different virtual machines, if you don't have multiple servers that can be placed into different network zones/subnets with a firewall controlling in/out access to each zone.

Solid network architecture is the basis for a secure infrastructure. Segment and firewall each different zone based on the different access requirements.  It is common to have the following networks:
* DMZ - internet only access
* Server LAN - intranet-only access
* Desktop LAN - only for desktops
* Management LAN - only for server administrators - highly restricted access only from admin, internal, IPs
* Storage LANs - each Zone has their own storage LAN - don't mix across other subnets.

So, it really comes down to what external access you must provide to each of the services.  If you can, only allow external access to the VPN and force all approved users to use the VPN to access their email, outbound proxy and internal webpages.  I'd setup an email-gateway if you need internet-based email too.  Email is a dangerous service, so running it on a dedicated VM is a best practice. The same for VPNs.  If the websites are all of a similar criticality and access is similar from the end-users, I'd host them all inside the same VM.  If there are external and internal websites, I'd put those into different network zones, which usually means different physical servers.

I'm uncertain as to what sort of "proxy" you mean.  Reverse proxy to protect your web/email servers or outbound proxy for use by desktops?  Both are a good idea. In an enterprise, desktops shouldn't have any direct access to the internet. We don't allow even DNS queries from desktops - DNS can be used for unintended purposes.

Anyway, as you can see it can get complicated.

Oh ... and don't allow the VM hosts to be on any internal or externally facing network. It should only be available on the management network to which only admins have access through highly restrictive firewalls.

Make sense?

---

