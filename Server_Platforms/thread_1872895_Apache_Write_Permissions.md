---
title: "Apache Write Permissions"
date: 2011-10-31
forum: Server Platforms
---

### Post by jimbob_2011 on 2011-10-31
Hello,

I'm trying to help a friend with his online store, which is running on a ubuntu server.

I believe the problem is due to a permissions problem. All of the folders have an owner on root. If the images folder is owned by root, would that stop Apache from writing to it?

The user account he has access to is not root, just is an account that is able to sudo.

How would I change the folder (plus the contents) owner and permissions?

Cheers!

---

### Post by cj13579 on 2011-10-31
Apache normally runs under the user "www-data". The command to change the permissions would be:

```
sudo chown -R www-data:www-data /path/to/folder
```

---

### Post by SeijiSensei on 2011-10-31
Don't give the www-data user blanket write permissions to /var/www and all its subdirectories, though.  That can be a giant security hole.  Since you said that he needed to write to the /images/ directory, I'd try this to start:

```

cd /var/www
chgrp -R www-data yourstoreappdir
cd yourstoreappdir
chmod -R g-w *
chmod -R g+w images

```

This assigns /var/www/yourstoreappdir and its subdirectories to group "www-data," the one that Apache2 on Ubuntu runs as.  The chmod lines remove group-writable permissions on all files and directories, then grants write privileges to the www-data group (essentially the Apache server) on the images directory and its files.

Now if your friend has only an ordinary user account, he'll only be able to make these changes if his account owns yourstoreappdir, and if his account is a member of the www-data group.  If he can't manage this himself, I'd recommend either reading the hosting company's documentation or talking to one of the their technical support people.  This problem should come up all the time, and the hosting firm should have good documentation for dealing with it.

---

