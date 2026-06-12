---
title: "wine how to restrict user from running apps"
date: 2010-12-05
forum: Wine
---

### Post by Hikaru-71 on 2010-12-05
Hi!
I want to create linux terminal server and the question is how to deny user to run applications via wine (It should be installed because we have application for windows which can't be replaced by linux software). So the problem is that users definitely will try to install tons of windows software (small games, official icq client and also will definitely find some viruses, which now perfectly lives in wine environment (don't tell me about "clamav" we have squid + kaspersky on gateway, but our license will end soon))
So, I want to find a way to get whitelisting or blacklisting for wine to restrict users from running any software except application we need.
Any help will be appreciated.

---

### Post by ajackson on 2010-12-05
Remove execute rights for all users on the wine executables but leave it on for owner and group. Chown them to a wine group and add allowed users to that group.

Never tried it but it should work.

---

### Post by Hikaru-71 on 2010-12-05
Thank you for your reply! I will try it.
hmm, a think a bit about it.
As I understand we do following:
```
chmod o-rx /usr/bin/wine
grpadd wine
chgrp wine /usr/bin/wine
usermod -G wine hikaru
```
and then we should try to run application. But this user will be able to run all applications, instead of one.
The goal is to give user to run a certain windows application and not to give rights to run application to some users

---

