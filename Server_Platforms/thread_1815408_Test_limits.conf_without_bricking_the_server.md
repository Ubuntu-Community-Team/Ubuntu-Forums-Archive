---
title: "Test limits.conf without bricking the server?"
date: 2011-07-31
forum: Server Platforms
---

### Post by fela on 2011-07-31
I'm running a server using Debian 5, on which a few people log on to over SSH using a user account with limited permissions. Basically I want to make sure they can't run things like fork loops as a lot of bad stuff would happen were the server to hard reboot.

So, how can I test what something **like** this will do:

```
:(){ :|:& };:
```

in a controlled environment, ie. so that I can kill it without rebooting?

Thanks very much :D

---

### Post by gmargo on 2011-07-31
> **fela said:**
> a controlled environment


Use a Virtual Machine.

---

### Post by fela on 2011-07-31
I have tested it in an Ubuntu virtual machine but wanted to check the actual server just in case.

---

### Post by Gyokuro on 2011-08-01
Try it on your workstation or on a identical test system - nobody try out such things on a production server :confused: Later you can adjust your server configuration files in case you found out how to crash your test system.

---

### Post by CharlesA on 2011-08-01
If it's working on a system with an identical (or very similar) configuration, it should work fine on the production server.

If you really want to test it, back up your data (just in case) and run a forkbomb after notifying everyone that you're doing some maintenance on the box.

Not responsible if it forces you to reboot the box, ofc.

---

### Post by fela on 2011-08-01
Seems like it's more hassle than it's worth, so I'll trust the ulimit values for now and if something happens, well, not the end of the world ;)

By the way, this isn't exactly a major company server, it's my home server but it runs quite a few different things like IRC, web servers, file server etc.

---

### Post by CharlesA on 2011-08-01
Worst thing that could happen is having it hardlock and you having to bounce it.

That and losing any data you were working on.

---

### Post by fela on 2011-08-01
> **CharlesA said:**
> Worst thing that could happen is having it hardlock and you having to bounce it.

That and losing any data you were working on.

Yep, that in this case is not worth the risk.

---

