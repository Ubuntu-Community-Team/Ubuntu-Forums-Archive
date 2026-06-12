---
title: "sub-sub-domains?"
date: 2006-02-02
forum: Server Platforms
---

### Post by OneSeventeen on 2006-02-02
I have been given a few static IPs and sub-domains for my company domain, and as usual, when I say go to "foo.example.com" people inevitably go to "www.foo.example.com"

Can I force "anything.foo.example.com" to go to "foo.example.com"?

---

### Post by MJN on 2006-02-02
Sure, the following will suffice in the DNS zone file for foo.example.com:
 
***.foo.example.com IN CNAME foo.example.com**
 
Mathew

---

