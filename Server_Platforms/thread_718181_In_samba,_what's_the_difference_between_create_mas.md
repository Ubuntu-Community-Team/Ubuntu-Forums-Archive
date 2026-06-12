---
title: "In samba, what's the difference between create mask and create mode?"
date: 2008-03-07
forum: Server Platforms
---

### Post by cpthk on 2008-03-07
In  samba conf, we may set share having create mask and create mode. What's the difference between them?

Thanks.

---

### Post by astrotech226 on 2008-03-08
It's technically the same command as one is an alias to another.  Here's the excerpt from the smb.conf man page:

> create mode
This parameter is a synonym for create mask.

---

