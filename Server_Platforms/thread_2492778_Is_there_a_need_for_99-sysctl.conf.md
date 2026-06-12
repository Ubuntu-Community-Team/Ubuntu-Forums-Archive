---
title: "Is there a need for 99-sysctl.conf"
date: 2023-11-22
forum: Server Platforms
---

### Post by sorquan on 2023-11-22
The drop-in files for sysctl have a symlink to /etc/sysctl.conf, but is it necessary? What is it for?


```
root@srv:~# ls -l /etc/sysctl.d/ | grep 99
lrwxrwxrwx 1 root root 14 Mar 2 2023 99-sysctl.conf -> ../sysctl.conf

```

Considering that the /etc/sysctl.conf file is in any case applied last in the queue:


```
...
* Applying /etc/sysctl.d/99-sysctl.conf ...
...
* Applying /etc/sysctl.conf...

```

---

### Post by deadflowr on 2023-11-22
Yes,
systemd uses it.

Edit:
A little more here:
[https://github.com/systemd/systemd/issues/8360#issuecomment-370457533]("https://github.com/systemd/systemd/issues/8360#issuecomment-370457533")

---

