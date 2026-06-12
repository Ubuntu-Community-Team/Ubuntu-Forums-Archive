---
title: "Cant edit httpd.conf"
date: 2005-08-13
forum: Server Platforms
---

### Post by koggo on 2005-08-13
I cant edit my httpd.conf because it's read-only and owned by root.
How can I edit it?!

---

### Post by Sam on 2005-08-13
You need sudo to perform tasks as root:
```
$ sudo gedit path/to/httpd.conf
```
Then type your password.

More info about sudo: [Ubuntu Wiki RootSudo](https://wiki.ubuntu.com/RootSudo)

---

