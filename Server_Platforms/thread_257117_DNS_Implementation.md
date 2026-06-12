---
title: "DNS Implementation"
date: 2006-09-14
forum: Server Platforms
---

### Post by janskey on 2006-09-14
hi guys

i need advice on implementing DNS Server.

example situation:

* there is a company named foo.com and they host the there dns records to ultradns.com. they have offices in US and JAPAN. in US they have servers: [name like pc1.foo.com,pc2.foo.com..] which are serving the svn repository,company websites and others..

questions:
- i want make a DNS server to delegate the subdomain record like us.foo.com so that the public servers in US will look like: pc1.us.foo.com,pc2.us.foo.com and etc.

- how about their internal network, should i build a another dns server for the internal network to host for: employee1.us.foo.com

any advice.?thanks!

---

