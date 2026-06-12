---
title: "Deny External Access to Webmin w/ IPTABLES"
date: 2009-01-11
forum: Server Platforms
---

### Post by trentscott4 on 2009-01-11
Would adding this rule to IPTABLES deny access to Webmin over port 10000 externally?

Accept 	If protocol is TCP and source is not 192.168.1.1 and destination port is 10000

(assuming my router is 192.168.1.1)

Also, is there any easy way where I can set IPTABLES to only allow webmin access from a specific mac address on port 10000?

---

