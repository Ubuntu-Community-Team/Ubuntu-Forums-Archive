---
title: "Allow one user to write to www"
date: 2013-08-16
forum: Server Platforms
---

### Post by ConcreteDonkey on 2013-08-16
Hello,

I'm wondering if it's possible to allow a new user to only write to the www folder holding the nginx hosted files. I'm also worried about accidentally breaking the permissions as I also want PHP files to be able to write here. This is a small webserver for just me and a few friends so nothing mission critical is going on and it's mainly used as a file host.

Here is the output of ls on the www folder:
```

total 44K
drwxr-xr-x 3 root root  4.0K Aug 16 21:27 .
drwxr-xr-x 3 root root  4.0K Dec 23  2012 ..
-rw-r--r-- 1 root root   383 Jul  7  2006 50x.html
-rw-r--r-- 1 root root   692 Mar  1 05:03 analytics.php
drwxr-xr-x 2 root root  4.0K Jan  7  2013 cpanel
-rw-rw-r-- 1 root root 318 Jul 30 18:38 favicon.ico
-rw-r--r-- 1 root root   151 Oct  4  2004 index.html
-rw-r--r-- 1 root root   189 Feb 25 23:45 index.php
-rw-r--r-- 1 root root  1.3K Mar  2 01:46 ip.php
-rw-r--r-- 1 root root    25 Feb 25 22:57 robots.txt
-rw-r--r-- 1 root root   778 Mar  3 04:12 status.php

```

Any help will be appreciated.

---

### Post by MG&amp;TL on 2013-08-16
EDIT: I *was* much mistaken! Please see the post by Lars below. Post left for referential reasons.

Unless much mistaken, those files should be owned by the group *www-data*, not by the user *root*. Make a backup of the directory (so you can restore it if this messes it up), change the ownership of the files and directories so that they are owned by *www-data*. This should not have any effect on whether or not *nginx* can read the files or not.

Then you need to add the new user (and anyone else who wishes to write to the *www* folder) to the *www-data* group. Assuming the user you wish to add is called *fred*, execute this command:

```
sudo usermod -a -G www-data fred
```

*fred* should then be able to read and write the files owned by *www-data*.

If at some point this messed up your webserver, simply delete everything in the *www* folder and copy the backup in, reverting you to the earlier situation, then post about what happened so we can examine the cause.

---

### Post by Lars Noodén on 2013-08-17
MG&TL, that is a sound method but the wrong group.  No files or directories should be owned by the user www-data or in the group www-data. Their purpose is to provide an unprivileged user and group for the web server processes. That purpose is defeated if httpd serves up files and directories writeable to www-data. Using www-data for files and directories gives the web server permission to write those files and directories. That permission extends to unwanted guests who figure out how to get the web server to write or execute these files. If that happens it is game over and the server is owned.

To prevent such risk, the files and directories should be owned by some other user and group than www-data. The default is user root and group root. But if you are the only user on that server, you can own the files yourself.  So at the simplest, you have the following:

```

sudo chown -R concretedonkey /var/www/

```

---

### Post by MG&amp;TL on 2013-08-17
> **Lars Noodén said:**
> MG&TL, that is a sound method but the wrong group.  No files or directories should be owned by the user www-data or in the group www-data. Their purpose is to provide an unprivileged user and group for the web server processes. That purpose is defeated if httpd serves up files and directories writeable to www-data. Using www-data for files and directories gives the web server permission to write those files and directories. That permission extends to unwanted guests who figure out how to get the web server to write or execute these files. If that happens it is game over and the server is owned.


Ah, my mistake then. I was going by my friends' (evidently severely misconfigured!) webserver directories. I shall alert them to this possibility ASAP. Thanks!

OP: It still might be worth using a group (NOT *www-data*) to allow everyone in that group access to the same files.

---

### Post by Lars Noodén on 2013-08-17
It would help if the system came with a second group named www or webmasters or something like that and had the /var/www hierarchy be in that group by default.

---

### Post by ConcreteDonkey on 2013-08-17
So I'm assuming best practise would be to create a new "www" group, add myself to it, give it permission to edit the www folders and then if needed I can add any other user to that www group and they will be able to modify the files aswell.

---

### Post by Lars Noodén on 2013-08-17
That's about it.  You'll also want to set the gid bit on the directories so that your group settings are applied to new items, especially new directories, so that you don't have to keep setting it manually.

```

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

```

---

