---
title: "named has trouble with AAAA resloves"
date: 2011-05-25
forum: Server Platforms
---

### Post by wlraider70 on 2011-05-25
I use DNS on my server as a chasing DNS so its not fully configured.

I seem to be having trouble with IPV6 addresses.
I'm guessing this is linked to the 6to4 tunnel I have set up to my windows box, but I'm not really sure.

```


May 21 18:00:16 hyrule named[1148]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
May 21 18:00:16 hyrule named[1148]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'zg.akamaitech.net/AAAA/IN': 2001:503:a83e::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'zm-2.akamaitech.net/AAAA/IN': 2001:503:231d::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'zd.akamaitech.net/AAAA/IN': 2001:503:231d::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'zf.akamaitech.net/AAAA/IN': 2001:503:231d::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
May 21 18:00:17 hyrule named[1148]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:500:3::42#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'zb.akamaitech.net/AAAA/IN': 2001:503:a83e::2:30#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'ze.akamaitech.net/AAAA/IN': 2001:503:231d::2:30#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'zh.akamaitech.net/AAAA/IN': 2001:503:a83e::2:30#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'zh.akamaitech.net/AAAA/IN': 2001:503:231d::2:30#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
May 21 18:00:18 hyrule named[1148]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'd.gtld-servers.net/AAAA/IN': 2001:dc3::35#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'e.gtld-servers.net/AAAA/IN': 2001:dc3::35#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'e.gtld-servers.net/AAAA/IN': 2001:500:2f::f#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'f.gtld-servers.net/AAAA/IN': 2001:500:2f::f#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'k.gtld-servers.net/AAAA/IN': 2001:500:1::803f:235#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'k.gtld-servers.net/AAAA/IN': 2001:dc3::35#53
May 21 18:00:22 hyrule named[1148]: error (network unreachable) resolving 'l.gtld-servers.net/AAAA/IN': 2001:500:1::803f:235#53
May 21 18:00:23 hyrule named[1148]: error (network unreachable) resolving 'ns1.aplus.net/AAAA/IN': 2001:503:a83e::2:30#53
May 21 18:00:23 hyrule named[1148]: error (network unreachable) resolving 'ns3.aplus.net/AAAA/IN': 2001:503:a83e::2:30#53
May 21 18:00:23 hyrule named[1148]: error (network unreachable) resolving 'j.gtld-servers.net/AAAA/IN': 2001:503:ba3e::2:30#53
May 21 18:00:23 hyrule named[1148]: error (network unreachable) resolving 'h.gtld-servers.net/AAAA/IN': 2001:500:1::803f:235#53
May 21 18:00:23 hyrule named[1148]: error (network unreachable) resolving 'ns2.aplus.net/AAAA/IN': 2001:503:a83e::2:30#53
May 21 18:00:24 hyrule named[1148]: error (network unreachable) resolving 'g.gtld-servers.net/AAAA/IN': 2001:dc3::35#53
May 21 18:00:24 hyrule named[1148]: error (network unreachable) resolving 'g.gtld-servers.net/AAAA/IN': 2001:503:ba3e::2:30#53
May 21 18:00:24 hyrule named[1148]: error (network unreachable) resolving 'g.gtld-servers.net/AAAA/IN': 2001:7fe::53#53
May 23 07:28:43 hyrule named[1148]: error (FORMERR) resolving 'frazettagallery.com/AAAA/IN': 74.86.203.163#53
May 23 10:06:37 hyrule named[1148]: error (connection refused) resolving 'echo.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 23 10:06:52 hyrule named[1148]: error (connection refused) resolving 'hknecndns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 23 10:06:53 hyrule named[1148]: error (connection refused) resolving 'amswatmdns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 23 10:06:53 hyrule named[1148]: error (connection refused) resolving 'sinwatmdns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 23 10:06:53 hyrule named[1148]: error (connection refused) resolving 'bl380003f.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 23 10:06:53 hyrule named[1148]: error (connection refused) resolving 'by2watmdns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 25 09:01:40 hyrule named[1148]: error (connection refused) resolving 'echo.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 25 09:01:55 hyrule named[1148]: error (connection refused) resolving 'sinwatmdns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 25 09:01:56 hyrule named[1148]: error (connection refused) resolving 'amswatmdns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 25 09:01:56 hyrule named[1148]: error (connection refused) resolving 'by2watmdns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 25 09:01:56 hyrule named[1148]: error (connection refused) resolving 'hknecndns01.msrapollo.net/AAAA/IN': 65.55.169.252#53
May 25 09:01:56 hyrule named[1148]: error (connection refused) resolving 'bl380003f.msrapollo.net/AAAA/IN': 65.55.169.252#53


```

---

### Post by wlraider70 on 2011-05-26
bump

---

### Post by hawkmage on 2011-05-26
How is your named configured?  Posting your configs or at least the relivent portions of the config files would help.

---

### Post by wlraider70 on 2011-05-26
I'm not really sure how it should be setup I followed a guide to use it has a cache server. 

The DB files are not setup, what other files are pertinent. 


/etc/resolv.conf

```


nameserver 127.0.0.1

nameserver 8.8.8.8
nameserver 209.18.47.61
nameserver 209.18.47.62
domain zion.org
search zion.org



```

---

