---
title: "Admin help"
date: 2010-08-25
forum: Security
---

### Post by Legendman3 on 2010-08-25
I screwed up badly and now i need my account to be admin again. The one that was made with ubuntu first I need it to be admin again after i made it un-admin what would be the commands for the terminal (or the recovery mode) to make it admin again. Ubuntu 10.04

---

### Post by sisco311 on 2010-08-25
Boot into Recovery Mode and run:
```
gpasswd -a **username** admin
```
where **username** is your login name.

For details, check out:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

