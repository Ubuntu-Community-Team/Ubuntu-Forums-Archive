---
title: "Odd request, HDD powersaving on server?"
date: 2006-12-15
forum: Server Platforms
---

### Post by viking325i on 2006-12-15
Hi,

I have a fileserver runing 6.10 server, 8 drives, 4 of which are mirrors using mdadm. Is it possible to do a hard drive power saving feature on the server install of 6.10? and if so does it play nicely with mdadm?

---

### Post by MJN on 2006-12-17
Sure, check out **hdparm** (the -S option specifically) - check out the man page as numbering methodology as is rather peculiar.

This setting won't be preserved between boots hence you will need to add the appropriate config to /etc/hdparm.conf (see man hdparm.conf).

As for compatibility with mdadm I don't know - never used it.

Mathew

---

