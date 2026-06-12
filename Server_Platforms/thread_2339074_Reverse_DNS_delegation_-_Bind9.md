---
title: "Reverse DNS delegation - Bind9"
date: 2016-10-04
forum: Server Platforms
---

### Post by manochio on 2016-10-04
Hello Everyone!

[COLOR=#212121][FONT=arial]I have a problem to set up a reverse dns [/FONT][/COLOR][COLOR=#212121][FONT=arial]delegation [/FONT][/COLOR][COLOR=#212121][FONT=arial]to an external server:I have a subdomain on my network and would like to delegate the  reverse dns [/FONT][/COLOR][COLOR=#212121][FONT=arial]resolution of[/FONT][/COLOR][COLOR=#212121][FONT=arial] this domain to an external dns server.domain to be delegated: 113.0.203.in-addr.arpaexternal server: 203.0.113.1 (ns1.test)                          203.0.113.2 (ns2.test)Could anyone help me to configure Bind9 to do this?

[/FONT][/COLOR]Sorry for the bad english.

[COLOR=#212121][FONT=arial]I have a problem to set up a delegation of reverse dns to an external server:I have a subdomain on my network and would like to delegate the resolution dns reverse this domain to an external server to mine.Track to be delegated: 113.0.203.in-addr.arpaexternal server: 203.0.113.1 (ns1.exemplo)203.0.113.2 (ns2.exemplo)Could anyone help me with Bind9 setting for this?I use forward?[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-10-05
If by "external" server you mean one on the public internet, then only your provider can delegate reverse resolution.  You will also need to have an IP subnet routed to you.  Talk to your provider about this after reading [RFC2317](https://www.ietf.org/rfc/rfc2317.txt).

---

### Post by manochio on 2016-10-05
Thanks SeijiSensei, yes, external is one server on the public internet, i already have de reverse dns delegation of this ip subnet to my internal DNS from my ISP.

---

### Post by SeijiSensei on 2016-10-06
Your delegated subnet should have been given a name like 113/24.0.203.in-addr.arpa.  Your ISP will need to create the NS records on its DNS servers that point this name to your name servers.  Then you just need to create a zone file for the 113/24.0.203.in-addr.arpa domain with PTR records for each host.

---

