---
title: "Firewall // Proxy Server Quick Question"
date: 2011-10-31
forum: Server Platforms
---

### Post by withoutfences on 2011-10-31
Hi Everyone;
 
I need just a quick reminder about setting up a firewall here in my house.
 
Here is what I recall to be a valid setup.
 
 
Cable Modem <--> Ubuntu FW//PS <--> Exisiting WiFi Router <--> Assorted Gadgets // 'puters
 
What I can't recall is for my firewall I have two ethernet interfaces one connecting to modem and the other to WiFi.  what I would prefer to do is assign
 
eth0 to 192.168.0.2 / 255.255.255.0
eth1 to 192.168.0.3 / 255.255.255.0
 
and just route traffic across them accordly via iptables and // or squid.
 
Am I recalling this setup correctly, it's been a while for me?
 
Oh I will also be running BIND caching server on this machine as well.
 
Thanks

---

### Post by Devi1903 on 2011-10-31
Looks good to me

I would however usually use 2 different IP ranges on either side of the Firewall.

Have you considered using PFSense? I very nice, stable and easy to setup firewall OS.

---

### Post by withoutfences on 2011-10-31
I was looking around at the Firewall driven OS's but since i'm trying to refresh my admin'ing skills, I decided that rolling up my sleves and digging in would be my best bet.
 
using different IP ranges would be IP Masquarding if I recall correctly?!?!.
 
thanks for the quick response.
 
Cheers,

---

### Post by Devi1903 on 2011-10-31
Yes, IP Masquerading enables the communication across the ranges.

---

