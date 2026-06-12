---
title: "Zentyal USB Modem Support"
date: 2012-06-05
forum: Server Platforms
---

### Post by cruising on 2012-06-05
Hi Everyone!

I have Zentyal 2.3 running on a pc with three NICs: eth0, eth1 and eth2. eth2 is my main gateway, through which Zentyal gets connection to the Internet and shares it via eth0. 

My main goal is to share the bandwidth using Traffic Shaping. I've confifgured it properly to allocate upload and download speeds based on IP. I also love that Zentyal has a UTM (Unified Threat Management) system. It also comes with the added bonus that you have all the repositories of ubuntu at your finger tips, should you need them. This was the main reason why I switched to trying out Zentyal from pfSense (based on freeBSD). 

I can connect using wvdial via my USB Modem (which I thought gnome-network-manager would handle, but it's okay for now). 

My question is: how do I let zentyal see the wireless LAN via the USB dongle and share the connection from there as the main WAN gateway? It's unclear to me how ubuntu sees the modem, dials out and connects just fine, but I can't make Zentyal to see it?! :confused:

Any help is much appreciated!

Thanks!

---

