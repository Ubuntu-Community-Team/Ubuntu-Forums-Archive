---
title: "rkhunter results"
date: 2008-02-19
forum: Security Discussions
---

### Post by saxuntu on 2008-02-19
I just ran rkhunter and got the following warnings:

> [10:37:14]   Checking for hidden files and directories       [ Warning ]
[10:37:14] Warning: Hidden directory found: /etc/.java
[10:37:14] Warning: Hidden directory found: /dev/.static
[10:37:14] Warning: Hidden directory found: /dev/.udev
[10:37:14] Warning: Hidden directory found: /dev/.initramfs
[10:37:14] Warning: Hidden file found: /etc/.exports.swp: Vim swap file, version 7.1
[10:37:14] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0) 

I believe the top 4 are false positives but what about the other 2 (swap and block special)? Ideas? And also is there a way to configure rkhunter to not show the false positives?

---

