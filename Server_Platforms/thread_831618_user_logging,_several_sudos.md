---
title: "user logging, several sudos"
date: 2008-06-17
forum: Server Platforms
---

### Post by Mr.Carramba on 2008-06-17
Hi,

I'm setting upp server with several webspaces, and thus to allow user config apache and install libs for it I want to give sudo to few users.
How can I log these user activities then using sudo? 
Is it saved to auth.log?
is yea, can I some how denied for sudo to edit this file, and maybe some other?
would it be waise to just create group and and write rigth to specific files, instead of giving away sudo?

thanks in advance!

---

### Post by cdtech on 2008-06-17
I wouldn't allow anyone sudo privileges, I would set the permissions and groups instead.

Just my thoughts........

---

### Post by iskatyel on 2008-06-17
If you give them sudo, they've got root.  Don't give sudo to anyone who is not a full admin of the machine.  Set rights and limit access that way.

And yes, by default sudo will log to auth.log, but once they type sudo su, they just have a root session and each command will not be logged.

---

### Post by Mr.Carramba on 2008-06-17
so there is no way to "unroot" sudo?
problem is that creating group will take a time from me, granding access to file that I didn't thought they needed. But it obviously by most secure solution.

---

### Post by iskatyel on 2008-06-17
Sudo wasn't designed to provide any sort of scaled access, it just lets you perform root tasks without giving out the root password.  Basically, anyone who can sudo can destroy the system.

---

### Post by windependence on 2008-06-17
> **iskatyel said:**
> Sudo wasn't designed to provide any sort of scaled access, it just lets you perform root tasks without giving out the root password.  Basically, anyone who can sudo can destroy the system.

This is not true. Sudo can be configured to give users only the access they need to only the apps the need. 

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)


-Tim

---

### Post by Mr.Carramba on 2008-06-17
> **windependence said:**
> This is not true. Sudo can be configured to give users only the access they need to only the apps the need. 

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)


-Tim


great! thank you!

---

### Post by mlapaglia on 2008-06-17
Isn't that just setting up the sudo command to use "permissions"? I thought if you set up groups and permissions, tasks that the user does regularly wouldn't need the "sudo" in front?

---

