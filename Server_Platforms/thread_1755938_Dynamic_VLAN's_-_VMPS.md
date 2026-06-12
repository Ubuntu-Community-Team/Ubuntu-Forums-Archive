---
title: "Dynamic VLAN's - VMPS"
date: 2011-05-11
forum: Server Platforms
---

### Post by Frizianz on 2011-05-11
Hey guys,

Basically im trying to setup a dynamic vlan setup with my Cisco 2950 switch. I understand that freeradius has support for vmps and i'm wanting to use this. (as i'd also use the radius server for authentication for my squid proxy server)

But i have no idea where to start to get this configured. Right now i've got the freeradius package installed and i've done a bit of google'ing and i cant seem to find much about vmps and freeradius.

Anyone know anything?

Thanks

---

### Post by Frizianz on 2011-05-16
Anyone?

---

### Post by terazen on 2011-05-17
I use mac-auth-bypass.  It is basically 802.1x that falls back on mac-auth-bypass so you set the switchport 802.1x timeouts to go as quickly as possible for devices that don't support 802.1x.

[http://freeradius.1045715.n5.nabble.com/Cisco-Mac-Auth-Bypass-with-Freeradius-2-0-4-td2770738.html](http://freeradius.1045715.n5.nabble.com/Cisco-Mac-Auth-Bypass-with-Freeradius-2-0-4-td2770738.html)

If you are just starting with freeradius be sure to check the man pages and the deployingradius.org website.  I remember it being a bit of a bear when I first started!

---

### Post by Frizianz on 2011-05-17
From what ive read Cisco 2950's dont support mac-auth-bypass? Can someone confirm this?

Wanting to get this setup so any device can plug in anywhere and be assigned to their appropriate vlan and if they dont have mac entry's they go into a fallback vlan which has different permissions.

---

