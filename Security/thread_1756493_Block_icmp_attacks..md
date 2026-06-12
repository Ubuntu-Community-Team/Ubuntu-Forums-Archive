---
title: "Block icmp attacks."
date: 2011-05-12
forum: Security
---

### Post by nbrochu on 2011-05-12
Hello, i was just wondering if it good practice to block icmp in a servers firewall. Besides not being able to ping the machine, would this have any other ramifications?

---

### Post by Lars Noodén on 2011-05-12
It's not a good idea to block ICMP but you can use iptables to limit ICMP. That would block abusers but allow legitimate use of ICMP.  

This tutorial uses TCP, but if you subsitute ICMP it should still be valid:

[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

[http://codingfreak.blogspot.com/2010/01/iptables-rate-limit-incoming.html](http://codingfreak.blogspot.com/2010/01/iptables-rate-limit-incoming.html)

---

### Post by nbrochu on 2011-05-12
Thanks that did the trick. I have never touched a Linux box before 3 months ago and this place has been awesome for reference. TY

---

### Post by dfreer on 2011-05-12
Don't see any issue with outright blocking ICMP, if the OP doesn't need to use it.

---

