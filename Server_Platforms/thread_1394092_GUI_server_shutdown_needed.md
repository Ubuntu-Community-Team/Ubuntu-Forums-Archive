---
title: "GUI server shutdown needed"
date: 2010-01-30
forum: Server Platforms
---

### Post by pdc124 on 2010-01-30
im looking for a GUI shuutdown for an ubuntu server ( ie my non-teccy sister can shut the machine off when finishing work).
Ive installed ebox but have no 'system' page .

$ sudo apt-cache search ^ebox
ebox - the eBox platform - Base framework
ebox-ca - eBox - Certificate Authority Manager for eBox
ebox-dhcp - eBox - DHCP server module
ebox-dns - eBox - DNS server
ebox-firewall - eBox - Firewall
ebox-network - eBox - Network configuration module
ebox-ntp - eBox - NTP server
ebox-objects - eBox - Object management
ebox-openvpn - eBox - OpenVPN server module
ebox-printers - eBox - Printer sharing
ebox-samba - eBox - File sharing
ebox-services - eBox - Services management
ebox-squid - eBox - Proxy cache and content filter
ebox-usersandgroups - eBox - User and Group management
libebox - eBox common library for server and client
$ 


 [https://help.ubuntu.com/9.04/serverguide/C/ebox.html](https://help.ubuntu.com/9.04/serverguide/C/ebox.html) makes reference to a system module.

Where is it (or is there an alternative)?

---

### Post by volkswagner on 2010-01-30
I never ran ebox, so I am not sure if it is there.  Webmin does have the ability to shutdown/reboot the server.  I am not sure if you would want to add webmin just for that function, yet it may allow you to replace ebox.

---

### Post by pdc124 on 2010-01-30
Ive done it with webmin in the past, but they've pulled it from the repositories - IIRC there have been security issues in the past.
having installed ebox , id be interested to at least try it.

---

### Post by ene_dene on 2010-01-30
> **pdc124 said:**
> Ive done it with webmin in the past, but they've pulled it from the repositories - IIRC there have been security issues in the past.
having installed ebox , id be interested to at least try it.
Why don't download webmin deb package from webmin site?

---

### Post by tlsarles on 2010-01-30
Low Tech, but won't tapping the power button initiate a shutdown? You could also set chron to do a shutdown at a certain time each day if it will be consistent.

---

### Post by wojox on 2010-01-30
Write a simple shell script.

---

