---
title: "Squid Server Error"
date: 2018-02-01
forum: Server Platforms
---

### Post by slkamath on 2018-02-01
Hi,

I installed new Ubuntu 16.04 server and installed squid server in that. It's giving error. Can someone help me to solve below error.

My squid configuration file is in 
/etc/squid3/squid3.conf

_**In terminal**_
root@lesvr3:/home/administrator# squid -z
root@lesvr3:/home/administrator# 2018/02/01 10:38:10 kid1| Set Current Directory to /var/spool/squid
2018/02/01 10:38:10 kid1| Creating missing swap directories
2018/02/01 10:38:10 kid1| No cache_dir stores are configured.
---------------------------------------------------------------------------------------------------------------------------
_**In Webmin**_
_**Initializing the Squid cache with the command squid3 -f /etc/squid3/squid3.conf -z ..**_
FATAL: Unable to open configuration file: /etc/squid3/squid3.conf: (13) Permission denied Squid Cache (Version 3.5.12): Terminated abnormally.
CPU Usage: 0.016 seconds = 0.008 user + 0.008 sys
Maximum Resident Size: 161984 KB
Page faults with physical i/o: 0

In Webmin Squid Server section I am getting this message at the top
Your Squid cache directories /hdd1, /ssd1, /hdd2, /ssd2, /hdd3, /ssd3 have not been initialized.This must be done before Squid can be run.

Initialize Cache

Can some one help me to resolve this?

Lokesh Kamath

---

