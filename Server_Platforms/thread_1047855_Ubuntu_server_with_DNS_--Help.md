---
title: "Ubuntu server with DNS --Help"
date: 2009-01-22
forum: Server Platforms
---

### Post by ovcrash on 2009-01-22
Hi,

I'm looking to install bind9 DNS service on my Ubuntu server box. I'm in a DHCP environement, only my server has a static adresse. I know that if i would install the DHCP service on my ubuntu box i could make the DHCP auto-update the DNS with the new IP adresses. But my DHCP server is my DLink router, can i make the router auto-update the DNS? Or could i make the DNS auto-update it self?

It there a way to do this?

Thanks for your help.

---

### Post by Nostalos on 2009-01-22
Not a chance.  Best you could hope for on your router is that its running Dnsmasq (only if you are running something like dd-wrt or openwrt). 


If you are running stock firmware i would recommend trying dd-wrt or openwrt.  DNSmasq will link dhcp and dns lookups.   Or disabling dhcp on the router and setting up your Ubuntu Server with dnsmasq.   DHCP/Bind9 is completely possible.  But can get overly complex pretty quickly.

---

### Post by ovcrash on 2009-01-22
Thanks for the answer.
I will looking into that. But i doubt that the DIR-655 is open source.

---

### Post by redroad55 on 2009-01-23
Maybe this thread will help .. best to you 
 [http://http://ubuntuforums.org/showthread.php?t=897084&highlight=redroad55]("http://http://ubuntuforums.org/showthread.php?t=897084&highlight=redroad55")

---

### Post by redroad55 on 2009-01-23
[http://ubuntuforums.org/showthread.php?t=897084&highlight=redroad55]("http://ubuntuforums.org/showthread.php?t=897084&highlight=redroad55")
not sure what happened there try this

---

### Post by Iowan on 2009-01-23
[EDIT] button does wonders to fix those little oopsies... ;)

---

