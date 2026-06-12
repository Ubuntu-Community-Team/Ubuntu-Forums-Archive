---
title: "reason for &quot;sudo: must be setuid root&quot; issue on 12.04 ubuntu server"
date: 2013-01-15
forum: Server Platforms
---

### Post by xihad on 2013-01-15
Hellow,

i just did a fresh install of ubuntu 12.04 - 32 bit on my vps.
then i created a new user  and added it into "sudo" group to allow  sudo permission. then i tried to sudo to see whether it works or not. then i got "sudo: must be setuid root" warning. after googling for sometime i found out that /urs/bin/sudo file must be given chmod +s permission to make sudo work. i did that from my root user and everything seemed to work fine from then on. My question is should this issue occur on a fresh installation? everyone out there having the same issue somehow messed up their file/owner permission on user/bin. Does that mean my fresh installation somehow  did not went well as it should be? should i reinstall again or i just overlook it? I am looking forward to hearing insights from you. Thanks in advance.

---

### Post by bab1 on 2013-01-15
> **xihad said:**
> Hellow,

i just did a fresh install of ubuntu 12.04 - 32 bit on my vps.
then i created a new user  and added it into "sudo" group to allow  sudo permission. then i tried to sudo to see whether it works or not. then i got "sudo: must be setuid root" warning. after googling for sometime i found out that /urs/bin/sudo file must be given chmod +s permission to make sudo work. i did that from my root user and everything seemed to work fine from then on. My question is should this issue occur on a fresh installation? everyone out there having the same issue somehow messed up their file/owner permission on user/bin. Does that mean my fresh installation somehow  did not went well as it should be? should i reinstall again or i just overlook it? I am looking forward to hearing insights from you. Thanks in advance.
The /usr/bin/sudo suid bit should be set by default.  YOu should net have to do that.

---

