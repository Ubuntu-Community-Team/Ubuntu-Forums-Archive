---
title: "Resolving IP addresses in iptables logs"
date: 2010-01-19
forum: Security
---

### Post by JanisD on 2010-01-19
Hi all,

Does anyone have any tips/ideas on whether iptables logs can be set to automatically resolve IP addresses? 

I am running the firewall on a network with DDNS/DHCP, and this ability would really help quickly identify hosts with suspect traffic.

Failing this, I guess the simplest solution will be to simply set static addresses!

Cheers,
Janis

---

### Post by bswilson on 2010-02-15
Janis,

The **iptables** tool does not have the ability to resolve hostnames from IP addresses.  However, there are several tools you can employ to get this information.  There's a neat tool called [IPtables log analyzer]("http://www.gege.org/iptables/") that you might want to try; however, it needs a MySQL engine and a Web server to display the reports.

---

