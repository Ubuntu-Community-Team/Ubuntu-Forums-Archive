---
title: "Both nameservers point to the same IP"
date: 2007-05-20
forum: Server Platforms
---

### Post by foresth on 2007-05-20
Hi,
I have a question related to setting up DNS server.

I have a domain, eg. mydomain.com. The nameservers of this domain are ns1.mydomain.com and ns2.mydomain.com. In my configuration file there are NS records set to ns1.mydomain.com and ns2.mydomain.com and ns1 is set to point to 72.xx.xx.2, ns2 is set to point to 72.xx.xx.6.

But when I request a report from dnsreport.com, I get:

> ERROR: Your nameservers report glue that is different from what the parent servers report. This will cause DNS servers to get confused; some may go to the IP provided by the parent servers, while others may get to the ones provided by your authoritative DNS servers. Problem record(s) are:

ns2.mydomain.com.:
Parent server (k.gtld-servers.net) says A record is 72.xx.xx.2, but
authoritative DNS server (72.xx.xx.2) says it is 72.xx.xx.6

How can I "tell" to the parent server that the ns2 nameserver is set to point to .6?

Thanks a lot!

---

### Post by nixfaced on 2007-05-20
At first glance, it seems the records in question are the ones your registrar has.  You'd probably want  to login to the  website through which you registered your domain (e.g. register.com, godaddy, or whatever) and doublecheck your nameserver settings there.  Hope this helps.

---

