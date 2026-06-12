---
title: "squid delay pools"
date: 2006-11-03
forum: Server Platforms
---

### Post by rukinhas on 2006-11-03
Hello ppl,

I'm trying to configure delay pools under squid but it seems that the restrictions I configure don't get applied.
I'm running UBUNTU 6.10 with squid 2.6STABLE1.

my squid.conf (part of it) is this:

```
acl nets src 10.0.88.0/24
acl nets src 10.0.92.0/24
acl nets src 10.0.244.0/24
acl nets src 10.9.96.0/24
acl alunos src 10.9.160.0/24
acl nets src 10.9.252.0/24
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https, snews
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access allow Safe_ports
http_access deny !Safe_ports
http_access allow SSL_ports
http_access deny CONNECT !SSL_ports
#http_access allow all
http_access allow localhost
#http_access allow alunos
http_access deny all

http_reply_access allow all
#http_reply_access allow alunos
icp_access allow all
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname proxy.e-U


delay_pools 1
delay_class 1 3
delay_access 1 allow alunos
delay_access 1 deny all
delay_parameters 1 80000/80000 -1/-1 16000/16000
```


I'm trying to limit the bandwith of each IP address to 16Kbytes/s , but in all my tests I can download an ISO at 70 - 80 Kbytes/s in firefox without any download manager.

I've also tried this:

```
#delay_pools 2

#delay_class 1 2
#delay_parameters 1 80000/80000 8000/8000
#delay_access 1 allow alunos
#delay_access 1 deny all

#delay_access 2 allow nets
#delay_access 2 deny all
#delay_class 2 1
#delay_parameters 2 -1/-1
```

I haven't got it either.
I'm the only person connected to the proxy at the moment because i'm still configuring it.

Am I doing something wrong? Is it the fact that i'm the only one, or the abobe config should limit my download speed at 16Kbytes??

Please help

Rui Silva

PS. My english is not as good as I would like. Sorry

---

### Post by esaym on 2006-12-06
I know nothing about this but people here seem to: [http://community.smoothwall.org/forum/viewtopic.php?t=16636&sid=7af8ff3156c6fd62a223eb747073899b](http://community.smoothwall.org/forum/viewtopic.php?t=16636&sid=7af8ff3156c6fd62a223eb747073899b)

---

### Post by rukinhas on 2006-12-07
Hi there. Thank you for your help.

Delay pools is broken til 2.6 Stable5. Squid's developer said so.

I'm now using that version with great success.

---

### Post by briealeida on 2008-06-06
I know this is old and few (if any) will read it but it may be helpful to others.
Restart squid.
Open 'Terminal' and type ```
sudo /etc/init.d/squid restart
```

That should do it.

---

