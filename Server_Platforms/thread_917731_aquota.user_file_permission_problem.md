---
title: "aquota.user file permission problem"
date: 2008-09-12
forum: Server Platforms
---

### Post by ubitos on 2008-09-12
Dear all,


I'm totally new here, and a real beginner with Linux admin. So, Hi everyone and sorry for any so-called 'stupid' question...


I have a strange message when booting my server, saying that it could not overwrite the aquota.user file by the fresh aquota.user.new one. I don't get it because I thought root was booting so why does it have any permission issue? Fortunately, it does not prevent booting but I don't like it.


For info:

$ ls -al /home/ aquota.user.*
drwxr-xr-x  7 root      root       4096 2008-09-09 15:30 .
drwxr-xr-x 22 root      root       1024 2008-06-03 12:28 ..
-rw-------  1 root      root       7168 2008-09-10 17:52 aquota.group
-rw-------  1 root      root       7168 2008-07-03 09:42 aquota.group.new
-rw-------  1 root      root       7168 2008-09-10 17:51 aquota.user
-rw-------  1 root      root       7168 2008-07-03 09:42 aquota.user.new


Should I chmod it to something else? And if so, how do I set the correct permissions of the next aquota.user files produced after each boot?

Many thanks in advance,
ubitos.

---

