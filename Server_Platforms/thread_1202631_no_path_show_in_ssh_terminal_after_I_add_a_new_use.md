---
title: "no path show in ssh terminal after I add a new user"
date: 2009-07-02
forum: Server Platforms
---

### Post by gzmask on 2009-07-02
Hello guys:
I used useradd to add a new user and then after I ssh in using the new user, the terminal doesn't show the "user@host/pwd" thing that feels very strange for me. How can I fix this?

P.S I m using ubuntu server 9.04

---

### Post by google44 on 2009-09-11
I have the same problem, I didn't want to open a new thread.
Basically when I login trhorugh ssh with a user created with useradd a lot of bash standard features, like history, path and so on are missing.

How can i solve this ?

---

### Post by DaithiF on 2009-09-11
try editing /etc/passwd (as root) and change the shell for your new user from /bin/sh to /bin/bash.

you can also set bash as the users shell when creating the user with useradd, check out 
```
man useradd
```.

---

### Post by grantemsley on 2009-09-11
Make sure their shell is bash.  Either edit /etc/password, or use the chsh command.

If that doesn't solve it, try copying ~/.bashrc from an account that works to the new account (and change the owner on the copy to the new user).

---

