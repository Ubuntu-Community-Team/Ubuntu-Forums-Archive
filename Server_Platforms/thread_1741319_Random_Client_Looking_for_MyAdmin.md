---
title: "Random Client Looking for MyAdmin"
date: 2011-04-28
forum: Server Platforms
---

### Post by cpicon92 on 2011-04-28
Hi everybody, 
I was just checking my Apache error log and I noticed that some random client has been asking for all kinds of directories that don't exist (i.e. myadmin, webdav), the messages look like this: 
```

[Wed Apr 27 16:51:32 2011] [error] [client 75.125.94.194] File does not exist: /home/picon/waffl.in/myadmin

```
Should I be worried? I don't have MySql installed anyway, but I want to make sure that I haven't accidentally left something open on my server...

Thanks

---

### Post by t3r0 on 2011-04-28
Hi,

These are usually just some random script kiddies or hacked server scanning for insecure scripts to infect other computers.

Just make sure all your scripts and software is up to date and secure and you should be fine.. 

It's good idea always to report these issues to the network owner. Run whois query on that ip-address and send notice with logfiles attached to their abuse - address.

- Tero

> **cpicon92 said:**
> Hi everybody, 
I was just checking my Apache error log and I noticed that some random client has been asking for all kinds of directories that don't exist (i.e. myadmin, webdav), the messages look like this: 
```

[Wed Apr 27 16:51:32 2011] [error] [client 75.125.94.194] File does not exist: /home/picon/waffl.in/myadmin

```
Should I be worried? I don't have MySql installed anyway, but I want to make sure that I haven't accidentally left something open on my server...

Thanks

---

### Post by cpicon92 on 2011-04-28
Thank you for your advice. I will do that.

---

