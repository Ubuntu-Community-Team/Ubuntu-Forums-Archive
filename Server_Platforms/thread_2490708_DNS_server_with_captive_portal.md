---
title: "DNS server with captive portal?"
date: 2023-09-13
forum: Server Platforms
---

### Post by that12guy on 2023-09-13
Can anyone help me set up a DNS server that forces a captive portal?  I've been playing around with dnsmasq and some other software on Ubuntu but I haven't been able to achieve this.  Help?  This is what I need:
- A recursive DNS server, which I can set the master DNS where it gets it's records
- Public facing, but with ACL to prevent abuse
- Forces a captive portal on any device using it for DNS lookups

---

### Post by SeijiSensei on 2023-09-13
Can't you accomplish the same thing by limiting the IP address ranges that the server supports? For ISC bind, there is the "alllow-query" parameter.

[https://kb.isc.org/docs/aa-00503](https://kb.isc.org/docs/aa-00503)

---

### Post by that12guy on 2023-09-13
> **SeijiSensei said:**
> Can't you accomplish the same thing by limiting the IP address ranges that the server supports? For ISC bind, there is the "alllow-query" parameter.

[https://kb.isc.org/docs/aa-00503](https://kb.isc.org/docs/aa-00503)
I've already got that part working.  It's the getting it to force a captive portal that I need help with.  Suggestions?

---

