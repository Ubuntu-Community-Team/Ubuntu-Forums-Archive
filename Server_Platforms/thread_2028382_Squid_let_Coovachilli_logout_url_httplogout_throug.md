---
title: "Squid: let Coovachilli logout url http://logout through"
date: 2012-07-18
forum: Server Platforms
---

### Post by moboticdes on 2012-07-18
Hi everyone, I'm trying to pass the url [http://logout](http://logout) used by coovachilli to logout from the walled garden through Squid proxy server.

However when I type [http://logout](http://logout) the Squid proxy sends me to the OpenDNS error page instead of the internal coovachilli logout page.
I tried adding without success

```

acl no_cache_server1 dstdomain logout
no_cache deny no_cache_server1

```Then I tried visiting directly [http://10.1.0.1:3990/logoff](http://10.1.0.1:3990/logoff) however this url instead gives me a "The system returned: (104) Connection reset by peer" although I added

```
acl Safe_ports port 3990
```Other websites with strange ports howver work flawlessy (for instance [http://freeunix.dyndns.org:8088/site2/links.shtml](http://freeunix.dyndns.org:8088/site2/links.shtml))
I think it may have with the fact that [http://10.1.0.1:3990/logoff](http://10.1.0.1:3990/logoff) is inside the network..

Help is appreciated here
Thank you

---

