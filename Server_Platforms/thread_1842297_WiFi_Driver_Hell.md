---
title: "WiFi Driver Hell"
date: 2011-09-11
forum: Server Platforms
---

### Post by LiteDrive on 2011-09-11
Looking to install the wifi driver's for my Belkin usb device. It's about 4-5 years old, but was recognized fine on normal installations of Ubuntu. 

I checked the documentation, and tried running lspci | grep Network, but that didn't turn up anything at all. iwconfig doesn't lend much help either. 

Alas, I feel quite lost. My end result is to make this server web accessible, but I have no idea how to do this. Is there any resources out there which can A) Help me with my problem and B) show me how to do this?

---

### Post by rubylaser on 2011-09-11
If it's a server, and you want consistent upltime, might I suggest using a wired connection rather than wireless?  Seems counterintuitive to use wireless as the sole connection for a server designed for uptime.

Maybe paste in your whole lspci, and the exact model number of your Belkin device would allow people to help you.

---

### Post by pytheas22 on 2011-09-11
Yes, please paste your entire output from "lspci -nn" (the -nn bit is important) and also "lsusb."  With that someone can probably help you find directions.

Of course, a wired connection is always definitely better if one is available.

---

### Post by arrrghhh on 2011-09-12
> **pytheas22 said:**
> Yes, please paste your entire output from "lspci -nn" (the -nn bit is important) and also "lsusb."  With that someone can probably help you find directions.

Of course, a wired connection is always definitely better if one is available.

Adding another post here, agreeing with the last two.  Please post the output of the above commands, but really - if you want a consistently stable connection (for any server) wired is always, ***always*** best.

---

