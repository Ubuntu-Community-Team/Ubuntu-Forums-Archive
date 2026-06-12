---
title: "DHCPD vs  DHCP3-SERVER"
date: 2006-11-12
forum: Server Platforms
---

### Post by FrozenPixel on 2006-11-12
Is the DHCP3-SERVER the latest version or something. I tried to follow the Ubuntu Server guide for setting up DHCP and nothing in there relates to anything available.

I did a APT-CACHE search and only came up with dhcp3-server but the config instructions refer to files that this package does not contain.

Quite confused.

---

### Post by Iowan on 2006-11-13
DHCP3 has been around since (at least) Breezy - it took me some stumbling around to find it when I was looking for a DHCP server.  It seems to work fine for my application...

---

### Post by Paris Heng on 2008-01-31
> **Iowan said:**
> DHCP3 has been around since (at least) Breezy - it took me some stumbling around to find it when I was looking for a DHCP server.  It seems to work fine for my application...

Can you tell where we actually go edit the .conf file if we installed dhcp3-server? Thanx

---

### Post by koenn on 2008-01-31
> **Paris Heng said:**
> Can you tell where we actually go edit the .conf file if we installed dhcp3-server? Thanx

try 
 /etc/dhcp3/

---

### Post by Paris Heng on 2008-01-31
Thanx

---

