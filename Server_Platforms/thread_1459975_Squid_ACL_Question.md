---
title: "Squid ACL Question"
date: 2010-04-22
forum: Server Platforms
---

### Post by igb on 2010-04-22
I want to use Squid to restrict the hours of access for a single computer in my network, but allow unlimited access for all others.

In my squid.conf I have:

```
acl our_network src 192.168.0.0/24
acl john src 192.168.0.19
acl WorkingHours time D 06:00-22:00

http_access allow our_network
http_access allow john WorkingHours
```

So my question is will the allow for the single ip address during working hours override the global allow for our_network. Is there a better way of doing this?

Ian.

---

