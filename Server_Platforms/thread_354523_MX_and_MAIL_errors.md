---
title: "MX and MAIL errors"
date: 2007-02-06
forum: Server Platforms
---

### Post by MAO on 2007-02-06
[http://dnsreport.com/tools/dnsreport...in=software.kg](http://dnsreport.com/tools/dnsreport...in=software.kg)

**Reverse DNS entries for MX records**
ERROR: The IP of one or more of your mail server(s) have no reverse DNS (PTR) entries/* (if you see "Timeout" below, it may mean that your DNS servers did not respond fast enough)*/. RFC1912 2.1 says you should have a reverse DNS for all your mail servers. It is strongly urged that you have them, as many mailservers will not accept mail from mailservers with no reverse DNS entry. You can double-check using the 'Reverse DNS Lookup' tool at the DNSstuff site if you recently changed your reverse DNS entry (it contacts your servers in real time; the reverse DNS lookups in the DNS report use our local caching DNS server). The problem MX records are:
205.22.29.217.in-addr.arpa [No reverse DNS entry (rcode: 3 ancount: 0) (check it)]

**Connect to mail servers**
ERROR: I could not complete a connection to any of your mailservers!

kadamjai.software.kg: Timed out [Last data sent: [Did not connect]]

If this is a timeout problem, note that the DNS report only waits about 40 seconds for responses, so your mail *may* work fine in this case but you will need to use testing tools specifically designed for such situations to be certain.

[COLOR="Blue"]How to Correct THIS??? :confused:  Please help[/COLOR]

---

### Post by MJN on 2007-02-06
The reverse DNS issue is something you're unlikely be able to do anything about. Your ISP provides these mappings and usually reverse maps your IP address to a name within its own zone. For a residential customer they are unlikely to point it to your domain, but you can but ask.
 
The second one is that kadamjai.software.kg did not respond to a connection to port 25 (SMTP). I've just tried it now, whilst kadamjai.software.kg is pointing to 217.29.22.205 and got the same problem. Is that your current IP address? Are any routers configured to forward port 25 to your server? Is your mail server running?
 
Mathew

---

