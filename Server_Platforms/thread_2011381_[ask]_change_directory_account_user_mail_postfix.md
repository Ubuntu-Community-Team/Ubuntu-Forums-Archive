---
title: "[ask] change directory account user mail postfix"
date: 2012-06-27
forum: Server Platforms
---

### Post by Undo_Rider on 2012-06-27
I make mail server with postfix, and if I create account user with command adduser , by default is saved /home
how can I change to another directory?

---

### Post by Vishal Agarwal on 2012-06-27
The complete directory can be changed; but not only the mail directory. This can be done with the help of usermod command.

---

### Post by SeijiSensei on 2012-06-27
> **Undo_Rider said:**
> I make mail server with postfix, and if I create account user with command adduser , by default is saved /home
how can I change to another directory?

Are you asking how to create a user but have his or her home directory be something other than /home?

You can specify a user's home directory at creation with "adduser -d /path/to/home/directory username".  The user's home directory is stored in his or her entry in /etc/passwd like this:

```
seiji:x:1000:1000::/home/seiji:/bin/bash
```

If you edit that file as root with sudo, you can change the home directory.

However, you need to take permissions into account.  If you look at /home, you'll see each user's home directory is owned by that user and assigned to that user's group.  The directory also has 700 permission to limit access to the directory to the user alone.  You'll need to consider which permissions you want your custom home directory to have, and you need to make sure the user can see the directory, list its files, and read from and write to those files.

---

