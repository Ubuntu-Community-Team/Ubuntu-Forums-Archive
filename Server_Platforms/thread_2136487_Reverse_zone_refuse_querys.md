---
title: "Reverse zone refuse querys"
date: 2013-04-17
forum: Server Platforms
---

### Post by SorlaK on 2013-04-17
Hi i am using BIND 9.8.1-P1 from ubuntu 12.04 repos and i setup a dns with two view and a slave transferring zone trough TSIG-KEYS all that work without problem the issue here is that the reverse zone (only) is refusing querys from outside, all zone are load without problem but now i am clueless here. Any ideas what my be the problem here. Thanks for your time.

PD this was a migration from my previus server on debian 6 using BIND 9.7.3.

---

### Post by SeijiSensei on 2013-04-18
If by "outside" you mean reverse lookups for addresses given to you by your ISP, the ISP is authoritative for those.  You would need to have arranged with your ISP for RFC2317 "[delegation]("http://www.ietf.org/rfc/rfc2317.txt")" so you could be authoritative for those addresses instead.

Alternatively, you might be asking why you cannot query some Internet-facing nameserver and asking it to resolve addresses in some private IP space behind the firewall like 192.168/16 or 10/8.  Then all I would have to do to map out your entire network is send a set of queries for all the addresses in the private IP spaces.  Shudder.

Can you post a sample refusal and any corresponding entries in /var/log/syslog?  Put the results in [noparse]```

```[/noparse] tags for easy reading.

---

