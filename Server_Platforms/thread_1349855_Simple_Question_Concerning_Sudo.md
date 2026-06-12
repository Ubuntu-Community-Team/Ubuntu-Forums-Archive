---
title: "Simple Question Concerning Sudo"
date: 2009-12-08
forum: Server Platforms
---

### Post by Iacoi on 2009-12-08
Okay, simple question. I understand the basic setup of the /etc/sudoers file, but I am wondering how to stop a group from using certain commands. In particular the passwd, rm, mv and su commands. So far my configuration looks like this.
```

alex ALL=(ALL) ALL //This is an admin
mason ALL=(ALL) ALL //This is another admin
iacoi ALL=(ALL) ALL //Me!

```While the server only has three trusted members, all users having full root capabilities is fine. However once other less-trusted/inexperienced users are added, this becomes a problem.

Any other suggestions for a small, yet needed increase in security are welcome.
Also, I was wondering how do you limit access to a certain directory. Obviously, directories such as /root, /sbin, etc. should also have limited access.

Many thanks in advance,
~~Iacoi

---

### Post by memilanuk on 2009-12-08
Have you looked in the Community Docs?

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by Iacoi on 2009-12-09
Yes, I see and understand how to increase a users abilities (e.g. the NOPASSWD command) but I still cannot find a way to limit a users access to commands and/or directories.

P.S. I have already tried [www.lmgtfy.com](www.lmgtfy.com) ;)

---

### Post by wojox on 2009-12-09
[User Management]("https://help.ubuntu.com/9.10/serverguide/C/user-management.html")

---

### Post by memilanuk on 2009-12-09
> **Iacoi said:**
> Yes, I see and understand how to increase a users abilities (e.g. the NOPASSWD command) but I still cannot find a way to limit a users access to commands and/or directories.

P.S. I have already tried [www.lmgtfy.com](www.lmgtfy.com) ;)

Maybe you need to read the docs again (not trying to be flippant about it).

Looks like you would create a user alias:

> 
**User Aliases**
User aliases are used to specify groups of users. You can specify usernames, system groups (prefixed by a %) and netgroups (prefixed by a +) as follows: 

```
# Everybody in the system group "admin" is covered by the alias ADMINS
 User_Alias ADMINS = %admin
```


Then create a command alias to go with it that has *just* the commands that you want the admin users to be able to access:

> 
**Command Aliases**
Command aliases are lists of commands and directories. You can use this to specify a group of commands. If you specify a directory it will include any file within that directory but not in any subdirectories. 

The special command '"sudoedit"' allows users to run sudo with the -e flag or as the command sudoedit. If you include command line arguments in a command in an alias these must exactly match what the user enters on the command line. If you include any of the following they will need to be escaped with a backslash (/): ",", "/", ":", "=". 

Examples: 

```

 # Admin commands
 Cmnd_Alias ADMIN_CMDS = /usr/sbin/passwd, /usr/sbin/useradd, /usr/sbin/userdel, /usr/sbin/usermod, /usr/sbin/visudo
```


etc., etc., etc.

As for restricting what directories they can go to... there is a way, but I don't even recall what you would look under.  Generally unless you are trying to lock the place down like Ft. Knox there's not a lot of point in keeping users from 'seeing' things, and most of the administrative commands require root or wheel/admin group permissions.  If you just add them to the sudoers file with power to only run limited commands (i.e. don't make them the equivalent of the original user added during install, with full root powers) then I don't see what the problem is...

---

