---
title: "Invalid zone type (ipv4)"
date: 2010-05-06
forum: Security
---

### Post by egulik on 2010-05-06
Hello,

I'm testing upgrade of shorewall from 4.0.6 to 4.2.9,
got most of the configs done but when I issue
shorewall6 check I get these errors:

 WARNING: Unknown configuration option (MACLIST_LOG_LEVEL) ignored : /etc/shorewall6/shorewall6.conf (line 53)
   WARNING: Unknown configuration option (IPTABLES) ignored : /etc/shorewall6/shorewall6.conf (line 67)
   WARNING: Unknown configuration option (IPSECFILE) ignored : /etc/shorewall6/shorewall6.conf (line 84)
   WARNING: Unknown configuration option (ADD_IP_ALIASES) ignored : /etc/shorewall6/shorewall6.conf (line 112)
   WARNING: Unknown configuration option (ADD_SNAT_ALIASES) ignored : /etc/shorewall6/shorewall6.conf (line 114)
   WARNING: Unknown configuration option (RETAIN_ALISES) ignored : /etc/shorewall6/shorewall6.conf (line 116)
   WARNING: Unknown configuration option (ROUTE_FILTER) ignored : /etc/shorewall6/shorewall6.conf (line 131)
   WARNING: Unknown configuration option (DETECT_DNAT_IPADDRS) ignored : /etc/shorewall6/shorewall6.conf (line 133)
   WARNING: Unknown configuration option (DELAYBLACKLISTLOAD) ignored : /etc/shorewall6/shorewall6.conf (line 141)
   WARNING: Unknown configuration option (DISABLE_IPV6) ignored : /etc/shorewall6/shorewall6.conf (line 147)
   WARNING: Unknown configuration option (BRIDGING) ignored : /etc/shorewall6/shorewall6.conf (line 149)
   WARNING: Unknown configuration option (DYNAMIC_ZONES) ignored : /etc/shorewall6/shorewall6.conf (line 151)
   WARNING: Unknown configuration option (PKTTYPE) ignored : /etc/shorewall6/shorewall6.conf (line 153)
   WARNING: Unknown configuration option (RFC1918_STRICT) ignored : /etc/shorewall6/shorewall6.conf (line 155)
   WARNING: Unknown configuration option (MACLIST_TABLE) ignored : /etc/shorewall6/shorewall6.conf (line 157)
   WARNING: Unknown configuration option (MACLIST_TTL) ignored : /etc/shorewall6/shorewall6.conf (line 159)
   WARNING: Unknown configuration option (SAVE_IPSETS) ignored : /etc/shorewall6/shorewall6.conf (line 161)
   WARNING: Unknown configuration option (USE_ACTIONS) ignored : /etc/shorewall6/shorewall6.conf (line 169)
   WARNING: Unknown configuration option (MACLIST_DISPOSITION) ignored : /etc/shorewall6/shorewall6.conf (line 196)
Checking /etc/shorewall6/zones...
   ERROR: Invalid zone type (ipv4) : /etc/shorewall6/zones (line 5)


What is wrong with zone file?
It's the same like in old version.
That means that ipv4 is not supported in that version of shorewall ?

---

### Post by noway2 on 2010-05-06
Given the number of and type of errors, it look like you have a syntax error in the shorewall6.conf file, or in a file that is included by the file.

---

