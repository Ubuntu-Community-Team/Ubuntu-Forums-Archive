---
title: "Snort- BASE not updating"
date: 2019-10-25
forum: Security
---

### Post by sniper8752 on 2019-10-25
I am running Snort 2.9, BASE and Barnyard2 on my Ubuntu server.  After running snort for some time, I get some events:
```
-rw-------  1 snort snort   25K Oct 25 18:15 snort.u2.1572044746
-rw-------  1 snort snort   974 Oct 25 18:15 portscan.log
```
Barnyard2 is running:
```
sudo barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.bookmark -g snort -u snort
```
When I check my BASE GUI though, there are no events listed.  
On the barnyard terminal screen, I see this:
```
Barnyard2 spooler: Event cache size set to [2048] Log directory = /var/log/barnyard2
INFO database: Defaulting Reconnect/Transaction Error limit to 10 
INFO database: Defaulting Reconnect sleep time to 5 second 
```

---

