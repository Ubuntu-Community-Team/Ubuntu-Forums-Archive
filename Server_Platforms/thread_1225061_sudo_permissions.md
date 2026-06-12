---
title: "sudo permissions"
date: 2009-07-28
forum: Server Platforms
---

### Post by wonderingwout on 2009-07-28
Hi,

I'd like to have one user have all permissions in a certain directory.
For example.

The user mike should have full control over:
/var/www/domains/mikesite.com

How do I define this in the sudoers file?
Currently mike has all privileges:

mike ALL = (ALL) ALL

But his access should be limited to his site folder only.
Probably an easy question but I'm very new to this.

Thanx in advance.

---

### Post by ibutho on 2009-07-28
You do not need to use sudo for this. Look into the chown and chgrp commands e.g. to let the user mike and the group mike own /var/www/domains/mikesite.com, you could do
```
chown mike:mike /var/www/domains/mikesite.com
```
To let them own /var/www/domains/mikesite.com and everything inside there, you could do
```
chown -R mike:mike /var/www/domains/mikesite.com
```

---

### Post by wonderingwout on 2009-07-28
Yes, indeed, that is the situation already.
But this user needs to be a sudoer restricted to that folder.

---

### Post by ibutho on 2009-07-28
> **wonderingwout said:**
> Yes, indeed, that is the situation already.
But this user needs to be a sudoer restricted to that folder.

Why do they need to be a sudoer when all they need is permission to access that directory? Sudo is for giving some root privileges to normal users and not for controlling access to directories.

---

### Post by wonderingwout on 2009-07-28
Well, I'm using that user to deploy a rails application with capistrano.
Those two tasks are always failing without sudo:

- migrating the database to a newer version
- stopping and starting daemons for background processes

I don't want to deploy the application as root because of security reasons.
And a chown after every deploy is out of the question because it is a large project and it takes several minutes to do that.

So I figured, if I can give this user restricted sudo access, my problem is solved.
Now I only need to restrict him a bit more.

---

### Post by ibutho on 2009-07-28
If you want to give them admin privileges to start, stop daemons etc, then they probably should be in the admin group.

---

