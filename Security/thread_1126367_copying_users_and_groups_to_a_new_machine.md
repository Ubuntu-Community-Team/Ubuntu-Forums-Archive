---
title: "copying users and groups to a new machine"
date: 2009-04-15
forum: Security
---

### Post by whitteng on 2009-04-15
We often upgrade hardware for our servers and when we do, we need to copy the users and groups info to the new machine which is often running a new OS. Is there some easy (not tedious) way to do this? Just copying /etc/passwd,group,shadow,gshadow causes major permission problems since many of the system group ids are inconsistent with actual files on the file system. It seems like this would be a pretty common need, is there any good solution other than tediously adding dozens of users and groups manually?

Thank you,
Gary Whitten

Edit bodhi.zazen : email deleted to prevent spam.

---

### Post by bodhi.zazen on 2009-04-15
I would script it. Have your script read the users from a file.

[http://www.linewbie.com/2007/11/using-bash-script-to-mass-create-users-and-change-passwords.html](http://www.linewbie.com/2007/11/using-bash-script-to-mass-create-users-and-change-passwords.html)

[http://www.howtoforge.com/user_password_creating_with_a_bash_script](http://www.howtoforge.com/user_password_creating_with_a_bash_script)

---

