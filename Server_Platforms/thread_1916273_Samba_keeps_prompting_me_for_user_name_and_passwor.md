---
title: "Samba keeps prompting me for user name and password"
date: 2012-01-27
forum: Server Platforms
---

### Post by rough60 on 2012-01-27
Hi all

I have installed samba on my server according to this link:
[http://www.jonathanmoeller.com/screed/?p=3331](http://www.jonathanmoeller.com/screed/?p=3331)

From my ubuntu 11.10 laptop I can see the share fine but when I try to access it, it continues to ask me for my password credentials.

Any help appreciated.

Thanks.

---

### Post by amauk on 2012-01-27
in the samba config file, change
```
security = user
```to```
security = share
```

Default config requires clients are setup with accounts on the server (user-level security)
This changes it to allow anonymous connections (shared-security)

---

### Post by redmk2 on 2012-01-27
> **amauk said:**
> ...

This changes it to allow anonymous connections (shared-security)

It's not *[COLOR="DarkRed"]shared[/COLOR]* security, it's *[COLOR="Green"]share security[/COLOR]*: as in the share provides security via file perms only.

Edit: Both ways provide for guest usage.

---

### Post by codmate on 2012-01-28
Alternatively, set up a Linux account with the same username and password as the foreign account accessing the Samba share; and allow this account access.

...Or you could get into the users.map file in /etc/samba.

---

