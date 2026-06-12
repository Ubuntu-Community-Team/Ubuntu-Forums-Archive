---
title: "user permissions"
date: 2011-04-13
forum: Security
---

### Post by crazymao on 2011-04-13
i installed ubuntu server on my computer and have a few people working on it, however i want to host a website on it but i dont want the others to be able to access it. so basically restrict access to <folder> for all users except for me. i did that however there is a problem, they have sudo privileges because they need them but it also means that they can just "sudo su" and enter the directory, which is annoying. so is there any way for prevent this? thanks a bunch

---

### Post by bodhi.zazen on 2011-04-13
You can not easily do this (restrict root).

You can restrict what other can do with sudo by configuring sudo and limiting what commands they can execute (see man sudoers) or you can try using apparmor, and restrict root from accessing the files.

You would then need to assign this new shell, confined by apparmor, to root in /etc/passwd.

See: [http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

For starting.

---

