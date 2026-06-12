---
title: "How to disable certain user remote ssh login in ubuntu?"
date: 2006-11-03
forum: Server Platforms
---

### Post by BodyWeapon on 2006-11-03
Hi,

  I have a ubuntu desktop, I have a few users on it. 

  I only want some of the users can access from ssh remotely.

  How to disable certain user remote ssh login in ubuntu?  :-k 

  Please help!

Thanks!

---

### Post by MJN on 2006-11-03
Check out **man sshd_config** and use either the **AllowUsers **or** DenyUsers** directives in /etc/ssh/sshd_config.

You might also want to include a **PermitRootLogin no** too.

Mathew

---

### Post by nadamsieee on 2006-11-03
Edit **/etc/ssh/sshd_config**:
```
AllowGroups sshers
```

Now create the group **sshers** and add only the users that you want to allow to ssh into your box.

---

### Post by SecurityMonkey on 2006-11-03
> **BodyWeapon said:**
> Hi,

  I have a ubuntu desktop, I have a few users on it. 

  I only want some of the users can access from ssh remotely.

  How to disable certain user remote ssh login in ubuntu?  :-k 

  Please help!

Thanks!

Another neat trick that you can do:

In the user's home directory, do the following:
1) vi .bash_logout:
```

#!/bin/bash
echo "Interactive logins are not permitted on this account."
exit

```
2) chmod 600 .bash_logout
3) chown root:root .bash_logout

Now, when the user goes to ssh to the box, they are told "NO!"

The correct way to do this is mentioned above in sshd_config.  However, the method described here works for any interactive login (telnet, ssh, console, etc).

---

### Post by Rick Z on 2008-04-01
This is EXACTLY what I need.  Thank you..

---

