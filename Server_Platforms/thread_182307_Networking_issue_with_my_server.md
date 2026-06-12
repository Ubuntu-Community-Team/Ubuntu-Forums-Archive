---
title: "Networking issue with my server"
date: 2006-05-25
forum: Server Platforms
---

### Post by Tux_Phoenix on 2006-05-25
Ok I have been trying to figure this out on and off for about 6 months now and have had no luck at all.   I have my Ubuntu server up and running with appache, php, and mysql.  I can see the server and the site on my local network with the static IP I gave it all good to go.  But when I try my static my isp gave me I get nothing.  I have a zoom adsl 5551a modem and a DLink 8 port 707p router,  I have changed the nat seeting on my modem as instructed by zoom and I have set the settings on the virtual server set up on the dlink.  But still nothing.  

I have called tech support from both hardware companies and my isp but non of the are any help.

Does any one have a hardware set up like mine or can anyone sugest a better modem or router that they use and have no problem with?  Or is there something server side that might cause this?  

Thanks in advance
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Socratez on 2006-05-26
have you tried running a dynamic dns clint just for the hell of it ... see if it si the DNS records at your location causing the issues ??

---

### Post by MJN on 2006-05-26
**From the LAN side** some routers don't allow access to other machines using the WAN IP address. My DLink DI604 does, but perhaps yours doesn't?
 
Have you confirmed that you can't see your server from outside your LAN (i.e. from the Internet) as opposed to just from other LAN-connected machines?
 
Mathew

---

