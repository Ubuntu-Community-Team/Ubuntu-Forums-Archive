---
title: "Reverse DNS lookups vs. DNS lookups"
date: 2006-04-10
forum: Server Platforms
---

### Post by blacklantern on 2006-04-10
Forgive me for not asking in the right subforum before.

What makes reverse DNS lookups less secure than DNS lookups? My Networking professor tells us that this is the case. I already know that one resolves IP address from domain name and the other does the opposite.

---

### Post by MJN on 2006-04-11
Why don't you ask him? He is afterall the one that's made the claim! ;)
 
Mathew

---

### Post by h3llfyr3 on 2006-04-11
Hmmnnn, I'd be interested to know his logic on that one.

Really any time you do a DNS lookup unless you know the DNS server is'nt poisoned you are open to abuse with either forward or reverse lookups.

You only real verification that the server you are comunicating with is the real server is PKI certificates issued by a trusted third party CA and checking that the thumbprint of the certificate is correct each time.

For interesting fun with DNS queries try dnsspoof part of dsniff.
[http://www.groar.org/trad/dsniff/dsniff-2.4/english-txt/dnsspoof.8.txt](http://www.groar.org/trad/dsniff/dsniff-2.4/english-txt/dnsspoof.8.txt)

Even connecting directly via IP is open to abuse if you can control the routing process of an upstream router or jud icious use of Arpspoofing, if you happen to be on the same subnet or can control the switch they are connected to.
[http://su2.info/doc/arpspoof.php](http://su2.info/doc/arpspoof.php)

---

