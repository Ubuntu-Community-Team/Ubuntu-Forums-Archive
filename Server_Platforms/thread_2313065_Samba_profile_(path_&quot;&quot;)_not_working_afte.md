---
title: "Samba profile (path &quot;/&quot;) not working after apt-get update (Ubuntu Server 14.04)"
date: 2016-02-09
forum: Server Platforms
---

### Post by Dimas on 2016-02-09
Hi,

I've an Ubuntu Server 14.04 and I've done an apt-get update. I've Samba configurated with some profiles, but there is one for root access to the server filesystem:

[root]
        path = /
        username = root, @"s103"
        valid users = root, @s103
        admin users = root, @s103
        read only = No

Until now, I can access from Windows to \\server\root\var (for example), but now it says that "Permission denied". I only can view \\server\root, but I can't enter any folder there.
The other profiles (path others than "/")  work as expected.

Any ideas?

---

### Post by howefield on 2016-02-09
Thread moved to the "*Server Paltforms*" forum.

---

### Post by Dimas on 2016-02-09
I think I found it, it's a Samba bug: [https://bugzilla.samba.org/show_bug.cgi?id=11647](https://bugzilla.samba.org/show_bug.cgi?id=11647)

:'(

---

