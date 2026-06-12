---
title: "Is Firewall necessary on computers behind a router w/ NAT ?"
date: 2006-03-10
forum: Server Platforms
---

### Post by luna6 on 2006-03-10
I have been hearing conflicting opinions on this, but is it necessary to run firewalls on computers that sit behind a router with / NAT? This is under the assumption that the local LAN is safe and trusted (meaning the computers are in my apartment & only worry about computers outside of my lan). Any opinions...? would like to hear...

---

### Post by frodon on 2006-03-10
It's not not necessary to have a firewall even if you don't have a router, therefore if you have one don't worry ;)

---

### Post by luna6 on 2006-03-10
Ok should have clarified, to protect from unwanted intrusions, is the NAT on a router enough, or should the computers behind the NAT run firewalls on each individual computer? - to prevent security breaches from computers outside the local lan...

---

### Post by frodon on 2006-03-10
It's really not needed except if, like me, you want to get peace of mind.
Seriously if you keep your ubuntu box up to date with the secutity releases you will not gain more security installing a firewall, because an ubuntu box _up to date_ is secure enough.
Generally you use a firewall with ubuntu, if you really want that nobody can see your computer name or when you run services (apache servers, FTP, samba, ....) so in that case a firewall allow to control the traffic and block unwanted IP's or hosts, or in most of the case you may run a firewall to gain peace of mind even if it don't improve the secutity.
So for me a NAT on the router is enough.

---

### Post by dermotti on 2006-03-10
[http://www.dslreports.com/scan](http://www.dslreports.com/scan)

try that and see what it returns.

---

### Post by kmi on 2006-03-10
[QUOTE=dermotti][http://www.dslreports.com/scan](http://www.dslreports.com/scan)

try that and see what it returns.[/QUOTE]
You may also analyse your computer/network with Nessus : see [http://www.ubuntuguide.org/#nessus](http://www.ubuntuguide.org/#nessus)...

It works perfectly for me and seems more accurate and efficient than many other online tools... Nessus also gives advises and tips related to what it discovers during a scan.

If you only use your Ubuntu box as a desktop, Nessus will certainly prove your router with NAT is more than OK...

---

### Post by jinacio on 2006-03-10
[QUOTE=luna6]I have been hearing conflicting opinions on this, but is it necessary to run firewalls on computers that sit behind a router with / NAT? [/QUOTE]

It depends:

- If you don't run ANY web services in ANY of your computers, you probaly shouldn't bother with a firewall.
- If you are running a few computers behind a router with NAT, and you have no port forwarding (the services are not available to the web), you shouldn't need a firewall.

- If you are running a computer/server set as DMZ on the router, or with port forwarding (http, ftp, ssh, whatever) then a firewall may grant an additional layer of protection (wich may be usefull at times).
Also, keep in mind that if any computer inside your lan is compromised, it will have easier access to the rest of the lan.

---

