---
title: "Bind9 fails to redirect only Windows"
date: 2010-08-28
forum: Server Platforms
---

### Post by R.Bucky on 2010-08-28
I operate a home network with Ubuntu Server 10.04 with services including DHCP3, Bind9, Apache, and so on. Since I host several dozen websites from home, I have to run Bind DNS. All Ubuntu boxes on my network operate fine. However, all Windows boxes on the network seem to forget to look internally for DNS after a couple of page loads on my internal sites. The network settings still indicate that my internal domain name server is the first lookup and everything seems normal. 

any suggestions here?

---

### Post by craigp84 on 2010-08-28
Do you have the windows boxes configured to look to both your local dns server and to an external nameserver?

If that is the case --

The host can legitimately choose to query either nameserver configured for any query it has to do.

To fix --

Don't tell your clients to use the upstream DNS, only look to local dns server. Reconfigure your local dns server to forward or recurse for localnet client queries.

---

### Post by Vegan on 2010-08-28
I have so many DNS servers listed in BIND I lost count. I have a copy of all my registered domains on my server and my registrar has a copy.

When I make a change it takes about 2 minutes, if that, for the planet to figure it out.

Does it matter what you use for a DNS?

If its setup right any DNS server should do.

---

