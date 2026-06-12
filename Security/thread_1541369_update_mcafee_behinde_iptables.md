---
title: "update mcafee behinde iptables"
date: 2010-07-29
forum: Security
---

### Post by yashar on 2010-07-29
i opened access to ftp.nai.com (without port limit) in iptables to let my systems to update mcafee, but still get unable to download in mcafee update log, do you have any idea?

i have another ip that tried to connect via port 21 on those machines, but the ip is not belongs to ftp.nai.com, is this possible thats redirecting?

---

### Post by bodhi.zazen on 2010-07-30
Check your logs and see what traffic is blocked.

Last time I looked macafee was a windows thing, so you may have better luck on a windows forums.

---

### Post by OpSecShellshock on 2010-07-30
They do have a scanner for Linux as well. It's proprietary, of course, and I suspect that it's mostly made for enterprises with multiple platforms. As with the others, it probably scans exclusively for Windows malware.

---

### Post by cprofitt on 2010-07-30
Or he could be using a Linux workstation as a firewall and is trying to update a Windows client behind that...

Or maybe something with a virtual Windows machine on a host?

---

### Post by bodhi.zazen on 2010-07-30
> **OpSecShellshock said:**
> They do have a scanner for Linux as well. It's proprietary, of course, and I suspect that it's mostly made for enterprises with multiple platforms. As with the others, it probably scans exclusively for Windows malware.

Most Linux AV software scan for Linux viruses as well. I am unaware of any antvirus that scans exclusively for windows viruses, but, honestly I don not use AV software ...

ClamAV for example :

[http://clamav-du.securesites.net/cgi-bin/clamgrok?virus=linux&search-type=contains&case-sensitivity=No&database=daily&database=main&display=database&display=virus&.submit=Submit+Query&.cgifields=database&.cgifields=search-type&.cgifields=case-sensitivity&.cgifields=display](http://clamav-du.securesites.net/cgi-bin/clamgrok?virus=linux&search-type=contains&case-sensitivity=No&database=daily&database=main&display=database&display=virus&.submit=Submit+Query&.cgifields=database&.cgifields=search-type&.cgifields=case-sensitivity&.cgifields=display)

---

### Post by yashar on 2010-07-31
> **cprofitt said:**
> Or he could be using a Linux workstation as a firewall and is trying to update a Windows client behind that...

Or maybe something with a virtual Windows machine on a host?


this is true, i set up linux server for internet sharing and firewall and all other systems are windows base, and i hope that i can move mail server to it also.

it was my mistake , i set  -m state for related and established connections for incoming through  port 21, as i remove that part it works smooth.

---

### Post by BigCityCat on 2010-07-31
I had a McCafe this morning at Mcdonalds, Their really good.:p

---

