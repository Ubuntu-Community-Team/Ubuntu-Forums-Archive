---
title: "smbldap-useradd -am option creates account with owner root"
date: 2010-04-24
forum: Server Platforms
---

### Post by macpraveen on 2010-04-24
I created a new account using the following command

$ sudo smbldap-useradd -amP testuser

Instead of having testuser as owner, it is showing root. why?

$ ls -l /home

drwx------ 2 root      root      4096 2010-04-24 09:37 testuser

Pls help.

---

