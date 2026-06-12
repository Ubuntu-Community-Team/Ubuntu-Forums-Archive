---
title: "Unable to delete user account"
date: 2009-11-08
forum: Security
---

### Post by mpsantos on 2009-11-08
I am trying to delete a user account. After deleting the account and exiting from the user/group dialog, I can go back in and the user account is still present. What am I doing wrong?

Thanks,
Mark

---

### Post by bodhi.zazen on 2009-11-08
by default , the user is removed in that they can no longer log in, however, system files and the /home/user directory are not removed.

see :

[http://linux.die.net/man/8/userdel](http://linux.die.net/man/8/userdel)

[http://man.he.net/man8/deluser](http://man.he.net/man8/deluser)

You can manually remove everything bu searching for it (which is a bit of an inconvenience) or use deluser

```
deluser --remove-home --remove-all-files user_name_to_delete
```

You probably need to re-add the user first.

---

### Post by lensman3 on 2009-11-09
At a text command window and as superuser do: "rm -fr /home/<user_Name>".  Where <user_Name> is the exact home directory of the user you want to remove.  Look in the /etc/passwd file for that users home-directory. 

You can use the "find" command to locate other userid files that were created by the user.

---

