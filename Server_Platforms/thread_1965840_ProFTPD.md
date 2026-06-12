---
title: "ProFTPD:"
date: 2012-04-26
forum: Server Platforms
---

### Post by awacs on 2012-04-26
Under Lucid, I can upload files as anonymous ftp, and I can list them with ls, but I cannot download them:

ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
[...]
-rw-r--r--   1 ftp      ftp      86231638 Jul 12  2009 shuki.zip
[...]
226 Transfer complete
ftp> get shuki.zip
local: shuki.zip remote: shuki.zip
200 PORT command successful
550 shuki.zip: No such file or directory

passive mode doesn't work, either.

Eh?

---

### Post by awacs on 2012-04-26
I guess I should add that I've made NO modifications to proftpd out of the box.

---

