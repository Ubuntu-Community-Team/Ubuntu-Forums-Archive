---
title: "Server Security"
date: 2006-12-18
forum: Server Platforms
---

### Post by Drakx on 2006-12-18
Hi

Ive installed dapper server on a spare box and been doing some work and some other people have accounts on the same box. I need to know the following info please

make it so only root has use of:

who
write
ls /home
ps aux
users

ill explaine the ls /home one i dont want another user login and be able todo ls /home and it shows other peoples home dirs i would like to make it so that if some one does do ls /home it gives them permission dined same with the others listed.

Thanks for the help

---

### Post by rbalfour on 2006-12-18
you can make the executable for su (/bin/su) only available for people within a group, I think this is done already with the wheel group, if their a part of the wheel group they can access in, if otherwise, not.

I'll base my following example on /sbin/ifconfig. Firstly create a group (do all of the following as root)
Code:

```
groupadd leet
```

this creates a group named leet. Next lets give /sbin/ifconfig this group with
Code:

```
chgrp leet /sbin/ifconfig
```

now set it so that the awner (root in this case) and group can execute it, but not anyone else.
Code:

```
chmod 554 /sbin/ifconfig
```



now if you want user john to have access to the command add him to the group
Code:

```
usermod -g leet john
```

credit: [http://www.linuxforums.org/forum/slackware-linux-help/37172-restrict-commands.html](http://www.linuxforums.org/forum/slackware-linux-help/37172-restrict-commands.html)

---

### Post by Drakx on 2006-12-18
Hi 

Thanks for the answer how ever now when the main user trys su i get this...

Password: 
su: Authentication failure
Sorry.

Even though i can login via root like so [email]root@mydns.com[/email] and enter the same password any ideas how todo that? and stop the out put of ls /home?

Thanks

---

### Post by rbalfour on 2006-12-18
> **Drakx said:**
> Hi 

Thanks for the answer how ever now when the main user trys su i get this...

Password: 
su: Authentication failure
Sorry.

Even though i can login via root like so [email]root@mydns.com[/email] and enter the same password any ideas how todo that? and stop the out put of ls /home?

Thanks

is the main user apart of the wheel?

---

### Post by Drakx on 2006-12-18
should be was able to su before i made the changes

---

