---
title: "using barnyard to process logs"
date: 2018-02-24
forum: Security
---

### Post by sniper8752 on 2018-02-24
I have barnyard2 / snort installed on my ubuntu server.  there are logs in /var/log/snort with the 'u2' format.  When I run ```
sudo barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo -g snort -u snort
``` I get this output: ```
Running in Continuous mode

        --== Initializing Barnyard2 ==--
Initializing Input Plugins!
Initializing Output Plugins!
Parsing config file "/etc/snort/barnyard2.conf"




+[ Signature Suppress list ]+
----------------------------
+[No entry in Signature Suppress List]+
----------------------------
+[ Signature Suppress list ]+


Barnyard2 spooler: Event cache size set to [2048]
Log directory = /var/log/barnyard2
INFO database: Defaulting Reconnect/Transaction Error limit to 10
INFO database: Defaulting Reconnect sleep time to 5 second

```
There are several log files that need to be uploaded to the mysql DB.  I am not sure why they are not being processed.

---

