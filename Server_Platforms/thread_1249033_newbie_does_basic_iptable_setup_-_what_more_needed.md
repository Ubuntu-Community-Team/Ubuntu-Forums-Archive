---
title: "newbie does basic iptable setup - what more needed to secure"
date: 2009-08-24
forum: Server Platforms
---

### Post by krraleigh on 2009-08-24
I setup my iptable and am wondering how secure I am.
The article was a bare bones no frills type and I need to
store sensitive data in my DB on the server.
 
this is my iptable:
Chain INPUT (policy DROP)
target prot opt source destination
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ACCEPT all -- anywhere anywhere
ACCEPT tcp -- anywhere anywhere tcp dpt:54321
ACCEPT tcp -- anywhere anywhere multiport dports www,https
tcp -- anywhere anywhere tcp dpt:ftp
ACCEPT icmp -- anywhere anywhere icmp echo-request
Chain FORWARD (policy DROP)
target prot opt source destination
Chain OUTPUT (policy ACCEPT)
target prot opt source destination
 
 
I will need to eventually setup email for those I host for, and of course I need to be able to connect via ftp so I can upload my web files to the server.
any insight would be appreciated
 
thank You
Kevin

---

