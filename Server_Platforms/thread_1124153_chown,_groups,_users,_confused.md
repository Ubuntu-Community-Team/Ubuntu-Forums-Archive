---
title: "chown, groups, users, confused"
date: 2009-04-13
forum: Server Platforms
---

### Post by blindmist on 2009-04-13
justin@sfhs:~$ id justin
uid=1000(justin) gid=33(www-data) groups=33(www-data)


as you can see, I am part of the www-data group. although, anything that is not chowned to my username itself (justin) I cannot write to that folder, even if it is chowned to www-data.

What am I doing wrong here?

---

### Post by hw-tph on 2009-04-13
Check the permissions of the directory you're trying to write to (**ls -l** works wonders :)). In order to create files in that directory it needs to be group writable, and if you want to change files they need to be group writable too (and belong to a group you are member of).

Also, check out the set group id bit (**chmod g+s** on a directory) which makes files created in a directory belong to the same group as the directory.

---

