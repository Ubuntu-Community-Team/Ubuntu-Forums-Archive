---
title: "Squid url_regex doesn't work for me :("
date: 2008-09-01
forum: Server Platforms
---

### Post by PryGuy on 2008-09-01
Good day everyone! I'm VERY new to Squid and I have made the following config file:```
cache_dir ufs /var/spool/squid 256 16 256
cache_mem 32 MB
visible_hostname 192.168.0.1
http_port 3128

acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl all src 0.0.0.0/0.0.0.0
acl allowed_hosts src 192.168.0.0/255.255.255.0

http_access deny manager all
http_access allow allowed_hosts
http_access deny all

icp_access allow allowed_hosts
icp_access deny all

miss_access allow allowed_hosts
miss_access deny all

acl nosex url_regex -i sex
http_access deny nosex
http_access allow all

```Squid works, but it doesn't block domains containing the word 'sex' for instance as shown here.:(
Where's my problem? Please help!

---

