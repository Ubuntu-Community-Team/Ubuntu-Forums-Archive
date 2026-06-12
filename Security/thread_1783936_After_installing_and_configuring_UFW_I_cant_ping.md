---
title: "After installing and configuring UFW I cant ping"
date: 2011-06-16
forum: Security
---

### Post by pcarlos853 on 2011-06-16
Hi,

I have set up UFW as such: (Deny All Out/ IN)

```
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere
22                         ALLOW OUT   Anywhere
515/tcp                    ALLOW OUT   Anywhere

```When ever I try to ping anything (LAN or WAN) I get:

```
PING 10.200.200.20 (10.200.200.20) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

```What do I have to do to allow pings out?

Thanks!

---

