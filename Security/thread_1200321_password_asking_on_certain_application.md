---
title: "password asking on certain application"
date: 2009-06-29
forum: Security
---

### Post by kuipou on 2009-06-29
since i installed onenote in crossover i cant seem to be able to password lock my journal is there a way that ubuntu could ask me a password i set for the app before it launches or a way that i can password lock my journals as it dosent seem to want to do it ?

---

### Post by bodhi.zazen on 2009-06-30
This is a FAQ on these forums.

The basic function you are wanting is performed on linux by permissions. As long as you give each user a separate account , you set the permissions of your file so that only your user can access the file.

say the file is called "foo"

chmod 600 foo

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Now only your user and root can access the file. Since people can not access your account without your password .

Essentially Linux is already password protected.

The caveat is Ubuntu is fairly permissive by default (user home directories are readable by anyone). You can change the permissions of /home/usename (not recursively).

chmod 770 $HOME

last, if you need to restrict root use encryption.

---

