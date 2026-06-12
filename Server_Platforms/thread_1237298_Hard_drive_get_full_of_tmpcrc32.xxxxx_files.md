---
title: "Hard drive get full of /tmp/crc32.xxxxx files"
date: 2009-08-11
forum: Server Platforms
---

### Post by gecka on 2009-08-11
hello,

On a virtual ubuntu (python vmbuilder/KVM) I get a lot of /tmp/crc32.xxxxx files. All those are just empty files and I run out of disk space.

-rw-r--r--  1 www-data www-data     0 2009-08-11 08:52 crc32.025a85
-rw-r--r--  1 www-data www-data     0 2009-08-11 17:53 crc32.025a86
-rw-r--r--  1 www-data www-data     0 2009-08-11 17:53 crc32.025a8a
-rw-r--r--  1 www-data www-data     0 2009-08-11 16:48 crc32.025a8d
-rw-r--r--  1 www-data www-data     0 2009-08-11 16:05 crc32.025a94
-rw-r--r--  1 www-data www-data     0 2009-08-11 20:45 crc32.025a96
-rw-r--r--  1 www-data www-data     0 2009-08-11 11:36 crc32.025a9a
-rw-r--r--  1 www-data www-data     0 2009-08-11 20:31 crc32.025a9b
-rw-r--r--  1 www-data www-data     0 2009-08-11 21:31 crc32.025aab

Has anyone an idea about what is creating those files?


Regards

---

### Post by cdenley on 2009-08-11
Are you running a web application which may be computing crc32 checksums? They are owned by the user apache runs as, so it must be some web script you installed.

---

