---
title: "ircd-irc2 O:Line help needed"
date: 2009-01-11
forum: Server Platforms
---

### Post by Before on 2009-01-11
Hey,

I got a problem with Ubuntu Server 8.10 running ircd-irc2.
When I try ```
/oper [password] Beforez
``` when connected on IRC I get the following error message:
```
No O-lines for your host
```
I searched on google, and the problem should be in the O:Line in /etc/ircd/ircd.conf

I tried the following O:Lines and each of them gives the same error:
```
O:beforez.lan:[password]:Beforez::10:A:
O:~before@beforez.lan:[password]:Beforez::10:A:
O:*.lan:[password]:Beforez::10:A:
O:*:[password]:Beforez::10:A:
O:*@*:[password]:Beforez::10:A:
O:192.168.1.74:[password]:Beforez::10:A:

```

Examples in ircd.conf.example got the same syntax.
I think I have made an incredibly stupid mistake, but I don't know what I did wrong.

Before_

---

