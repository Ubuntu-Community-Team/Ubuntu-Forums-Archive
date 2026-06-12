---
title: "how to restrict rbash"
date: 2008-12-03
forum: Server Platforms
---

### Post by mac-duff on 2008-12-03
Hey,
I using one account to create a ssh tunnel but their are some points that disturbs me.

- the user still can use some commands, like sudo, ping etc.
- when the user logs on, he or she can see the "last login" time. Regarding the INTERNET, it can be changed by editing the sshd_config, but it seems it doesnt work with this shell

Old posts were already closed, so it would be nice if someone can help me with that

Thx

---

### Post by Dr Small on 2008-12-03
rbash does not restrict anything.
Put a knowledgeable geek behind that shell, and he can break out it in less that 15 seconds.

---

### Post by LittleBoy on 2008-12-04
rbash only gives you the possibility to restrict a login.

Some points are:
1. Set the users home directory to read-only (owned by root)
2. Create a usr/bin inside the users home directory
3. Symlink the commands you want to allow into this directory
4. cleanup all .bash_* files (.bashrc, .bash_login, .bash_logout, etc.) - set PATH only to the directory of step 2
(=> google is your friend)

You really need to think about the commands you enable: 
e.g. vim has a option to enter a shell, so you could break out of the rbash with vi/vim => [see here](http://php.8ez.com/drsmall/blog/?p=238)

e.g. scp / ssh has some options which are dangerous, too -  [see here](http://pentestmonkey.net/blog/rbash-scp/)

If the rbash is set up in a correct way it is secure.

---

