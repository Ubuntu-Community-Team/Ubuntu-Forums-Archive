---
title: "DHCP and thin client oddities - need assistance"
date: 2008-08-13
forum: Server Platforms
---

### Post by Vince-0 on 2008-08-13
Hi!

I'm currently testing hardy 8.04, ltsp and 36 PXE clients in a lab. I've managed to get 11 or so thin clients to get a DHCP IP, and boot right into Firefox (kiosk) which was great...
 
Problem is I cannot get more thin clients to even request/get a DCHP IP and load up. The first oddity is that PCs can get DHCP IPs just fine from exactly the same cables/ports/switch that the thin clients could not, and its only certain cables/ports - others work fine (same switches etc).

The MAC addresses of the clients that don't work doesn't even get show in the DCHP server (no request / offer) but there is network activity on the switch LEDs. Even PC's on these exact cables/ports show in the log, assign and work fine. I've had the network tested, swapped around cables, thin clients, PCs, switches. I've a feeling its the switches (brand new, automatic, unmanaged - I havn't touched their configs) BUT 11 thin clients work? Is there a limit to the amount of thin clients connected? 

I am going to continue investigating tomorrow - its late here - more details and config/log posts to follow! After which I will plead with the skilled nix fundiez for some insight. :confused:

---

### Post by Vince-0 on 2008-08-14
Fixed it!

If I plug an IP phone on the cables/ports that didn't boot and daisy chain a network cable to a thin client, the thin client and phone get IPs and boot just fine.

Wth?

I suspect the little switching mechanism on the IP phone did something to cross over the cables? I have used both type A and B configurations on the UTP connectors - possible cause? 

But its all good, for now! Its the weekend!:guitar:

---

