---
title: "Does tor browser use dns requests from the tor network?"
date: 2011-03-01
forum: Security
---

### Post by asdfghjkl67 on 2011-03-01
Ok i think Tor has some way of making the dns queries anonymous by default. 

I did the DNS nameserver spoofablity test here at [https://www.grc.com/dns/dns.htm](https://www.grc.com/dns/dns.htm)  and the results i got showed about 30 different dns servers. Normally  when i carry out this test on my standard isp connection or the vpn i  use i just get one dns servers settings consistently.

Can anyone here more experienced with TOR comment on tor's use of dns?

---

### Post by MechaMechanism on 2011-03-02
> **asdfghjkl67 said:**
> Ok i think Tor has some way of making the dns queries anonymous by default. 

I did the DNS nameserver spoofablity test here at [https://www.grc.com/dns/dns.htm](https://www.grc.com/dns/dns.htm)  and the results i got showed about 30 different dns servers. Normally  when i carry out this test on my standard isp connection or the vpn i  use i just get one dns servers settings consistently.

Can anyone here more experienced with TOR comment on tor's use of dns?
Tor by default sends everything through Tor.  Just to be safe do this:

In Firefox URL bar type about:config

Type in search bar, proxy.

search for network.proxy.socks_remote_dns

change it to true

---

