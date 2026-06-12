---
title: "Unix user management"
date: 2010-07-27
forum: Server Platforms
---

### Post by Thyagaraj on 2010-07-27
Hai all!

I need help on the following things

- command to list all the members of a group 

-how to create super user(root)

-only user in superuser group can issue su or sudo command, others should give insufficient privilege error

---

### Post by rubylaser on 2010-07-27
This will show you members of a group, in this case adm or admin on your Ubuntu server.
```
grep admin /etc/group | tail -n1 | cut -d ":" -f 4
```

Then add your new user and add them to the admin group
```
useradd roger -G admin
```
```
passwd roger
```

This adds the user to the admin group so they can use sudo, and will give insufficient permissions errors to users who are not.

Hope that helps.

---

### Post by Thyagaraj on 2010-07-27
Thanks a lot!

Any unix user can do su and sudo. So i want to enable this to only for a user. Is there any way?

---

### Post by capscrew on 2010-07-27
> **Thyagaraj said:**
> Thanks a lot!

Any unix user can do su and sudo. So i want to enable this two only for a user. Is there any way?

The proper way to see users or groups is the term ***getent***, as in```
getent group
or
getent user
```

See the man pages for more information on **getent**.

The term **su **stands for ***switch user ***, all users should have this available to them.  As long as you know the users password you can switch to that user.  Remember, not all users are human.

With sudo you have to be a member of the admin group to have the rights to ***execute a command with root powers***.  Users do not become the root user.  This includes *sudo -i*.  The -i switch provides you with the root environment.  These are minor points, but well worth knowing.  Someday not knowing will drive you nuts trying to cure some insanity.

See the man pages for more information on **su**.

---

