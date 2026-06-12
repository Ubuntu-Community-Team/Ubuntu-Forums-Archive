---
title: "Run SNMP on non standard port"
date: 2011-06-30
forum: Server Platforms
---

### Post by xkaliburx on 2011-06-30
Afternoon all, I need to check a few webservers on one public IP behind a loadbalacer.  Since I need to get info from each, like I do with HTTP I want to simply do the following;

publicip:161 -> server1 port 161  (currently working)
publicip:162 -> server2 port 162 (failing)

I am looking at the docs ([http://manpages.ubuntu.com/manpages/lucid/man8/snmpd.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/snmpd.8.html)) and see I can change it, but it's not working and I'm not sure on protocol, placement, etc.

The snmpd.conf is working since the correct community string works, but the snmpd.conf file only had the one line;

rocommunity zpublicz

According to the docs, I simply added the following under that one line;
udp:162 which should tell it listen on all interfaces port 162.  When I try an snmpwalk from local on the same device it fails on 162 but still answers on 161, so any idea why that is not working is appreciated.

---

