---
title: "Squid proxy: big initial delay with certain pages"
date: 2010-10-28
forum: Server Platforms
---

### Post by Xylian on 2010-10-28
Hi,
I've noticed a very bad problem with my squid installation... it seems to work without errors (nothing wrong in the log files), but when I load some sites as [www.repubblica.it](www.repubblica.it) my browser shows a blank page and it says "waiting for oas.repubblica.it".. after several seconds (more than 20 secs, which means eternity in this case), the site shows up immediately (almost everything is loaded, something still loads after a while but the most important parts of the page are loaded).. I've looked at the access.log file and the first line I can see after the initial long delay is:

```
1288281355.044  63243 10.1.0.1 TCP_MISS/503 4996 GET http://oas.repubblica.it/RealMedia/ads/adstream_mjx.ads/repubblica.it/nz/home/1004754881@Position3,Position2,Top3,Top2,Top1,Middle1,TopLeft,Right1,Middle2,Left,Left1,Left2,Top,x61,x62,x63,x41,x42,x43,x44,x45,x46,Position1 - DIRECT/194.244.107.100 text/html

```

So there are problems with the oas.repubblica.it links... how can I avoid squid getting stuck on some links? Can I tell him to load more than a link in parallel? Can I set a timeout? Can you do a test with the same site and tell me which is the result of your test?

These are the options I've set in /etc/squid3/squid.conf (I've experienced the same with both squid and squid3 proxies):

```

acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl localnet src 10.0.0.0/8     # RFC1918 possible internal network
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
http_access allow manager localhost localnet
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow localhost
http_access deny all
http_port 3128
hierarchy_stoplist cgi-bin ?
cache_mem 32 MB  # --> (I can not give squid a bigger amount of memory, but I don't think it is a problem)
maximum_object_size_in_memory 10 MB
cache_dir aufs /var/spool/squid3 100 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320
dns_nameservers 127.0.0.1
forwarded_for transparent  # (I've also tried with "on" instead of "transparent")

```

Thank you very much!

---

### Post by SeijiSensei on 2010-10-28
Use a Squid ACL:

```
acl REP_REAL url_regex -i oas\.repubblica\.it/RealMedia
http_access deny REP_REAL
```

Place these before the "http_access allow localnet" line in /etc/squid3/squid.conf.

---

### Post by Xylian on 2010-10-28
> **SeijiSensei said:**
> Use a Squid ACL:

```
acl REP_REAL url_regex -i oas\.repubblica\.it/RealMedia
http_access deny REP_REAL
```

Place these before the "http_access allow localnet" line in /etc/squid3/squid.conf.
Thank you very much Seiji, this works for repubblica.it, very nice workaround.
BTW, is it possible to tell squid to load at least two links in parallel (i.e. having two web-fetching threads), so that if there is a link on which squid gets stuck it can still load other links?

---

