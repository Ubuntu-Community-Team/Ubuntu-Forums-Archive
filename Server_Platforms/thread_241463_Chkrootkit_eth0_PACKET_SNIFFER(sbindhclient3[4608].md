---
title: "Chkrootkit: eth0: PACKET SNIFFER(/sbin/dhclient3[4608]) Do I need to be concerned"
date: 2006-08-22
forum: Server Platforms
---

### Post by fubadubrub on 2006-08-22
Hello all.  Chkrootkit in it's daily log shows: eth0: PACKET SNIFFER(/sbin/dhclient3[4608]).

Do I need to be concerned.  What is this packet sniffer.  I use DHCP for my network, 1 computer and router connected to internet.  Rkhunter does not show this in it's daily log.

---

### Post by MrHorus on 2006-08-23
Not sure but it it's something that has just shown up then I would be worried.

dhclient is the binary that gets you an IP address via DHCP but "dhclient3" could be an attempt by a malicious binary to try and hide itself...

BTW if you don't know what it is then a packet sniffer analyses packets for interesting payloads such as logins and passwords.

---

### Post by fubadubrub on 2006-08-23
Thanks I also googled this as well and it seems to be a common false positive.  I normally use static networking however when I just recently installed Dapper I used DHCP networking so that's the cause probably.  I will just switch back to static networking since I don't really need DHCP.  Thanks.
> **MrHorus said:**
> Not sure but it it's something that has just shown up then I would be worried.

dhclient is the binary that gets you an IP address via DHCP but "dhclient3" could be an attempt by a malicious binary to try and hide itself...

BTW if you don't know what it is then a packet sniffer analyses packets for interesting payloads such as logins and passwords.

---

