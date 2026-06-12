---
title: "Creating your own special Blocklist for iplist / ipblock"
date: 2012-06-26
forum: Security
---

### Post by starz677 on 2012-06-26
Does anyone know if text lists you create yourself (for IPLIST) can contain notes?

For example, lets say I add an IP address range but want to have a note so that down the road I can know why the IP was added to the list in the first place.

For example,

A typical entry would look like this.....
[B]
ProxyServer:123.123.123.111-123.123.123.255[/B]

but I would like to add a note like this......

**ProxyServer:123.123.123.111-123.123.123.255 [COLOR=Gray] ## Malicious URL 06-22-2012[/COLOR]**

Where the ## would represent the beginning of a note for the entry yet not interfere with the blocklist entry.

Anyone know of a way to do this?

---

### Post by unspawn on 2012-06-26
Try 'iptables -m comment --help'

---

