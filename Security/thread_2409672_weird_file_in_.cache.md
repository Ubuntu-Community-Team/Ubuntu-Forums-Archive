---
title: "weird file in .cache"
date: 2019-01-05
forum: Security
---

### Post by mcyber4 on 2019-01-05
HI
what is that .doc that's not writable by root?
Thanks


[email]root@notUrbusiness:~/.cache[/email]# ls -lat
total 16
drwxrwxr-x  5 michael michael 4096 Jan  5 12:35 .
drwxr-xr-x  2 michael michael 4096 Jan  5 12:35 fontconfig
drwxr-xr-x  3 michael michael 4096 Jan  5 12:29 mozilla
drwxr-xr-x 18 michael michael 4096 Jan  5 12:20 ..
dr-x------  2 root    root       0 Jan  1  1970 doc
[email]root@notUrbusiness:~/.cache[/email]#

---

