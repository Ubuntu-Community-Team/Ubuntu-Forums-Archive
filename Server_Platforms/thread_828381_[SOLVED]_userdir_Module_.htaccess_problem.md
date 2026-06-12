---
title: "[SOLVED] userdir Module .htaccess problem"
date: 2008-06-13
forum: Server Platforms
---

### Post by x12Networks on 2008-06-13
I have been trying to resolve this problem on a new Hardy install.  I have Apache running, however the UserDir module seems to be having issues with this .htaccess problem that has been circulating.

Now my userdir.conf looks like this:
```
<IfModule mod_userdir.c>
        UserDir WWW
        UserDir disabled root

        <Directory /home/*/WWW/>
                Options FollowSymLinks
                AllowOverride None
                Allow From All
        </Directory>
</IfModule>
```

Permissions on the /home/*/WWW/ directories are 755, and all the files within are as well.

And I still have this in the Apache2 error.log:
```
(13)Permission denied: /home/<username>/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

Notice that it's looking in the users home directory, and not the WWW dir for the .htaccess file.  I have even tried adding one where it's looking for one, made it 777 and it still doesn't work.

I have been scouring the fourms and Googling stuff like crazy, but I cannot seem to find a way to make this work.  Anyone have thoughts?

---

### Post by logical_thought on 2008-06-13
I don't know if this will help, but try removing the slash at the end of your directory statement.

<Directory /home/*/WWW/> to <Directory /home/*/WWW>

---

### Post by x12Networks on 2008-06-13
I had tried it before, but for S#!75 & Giggles, I gave it another shot...  Still no go.

---

### Post by logical_thought on 2008-06-13
Are you doing anything in the .htaccess files?

---

### Post by x12Networks on 2008-06-13
Nope, I am not even using one.  I have no reason to for this particular server.  What's weird is that it's looking for one and there shouldn't be a reason for it to do so.

---

### Post by logical_thought on 2008-06-13
If you don't mind, run **ls -la** on the /home/<username> and /home/<username>/WWW directories and post the results here.

---

### Post by x12Networks on 2008-06-14
Just for my own sanity, I substituted <username> for the real username... :)  Here's what I have.

This is the /home/<username>
```
total 8232
drwx------ 27 <username> <username>    4096 2008-06-14 23:22 .
drwxr-xr-x  5 root   root      4096 2008-05-24 21:17 ..
-rw-------  1 <username> <username>    1809 2008-06-13 18:33 .bash_history
-rw-r--r--  1 <username> <username>     220 2008-05-17 22:25 .bash_logout
-rw-r--r--  1 <username> <username>    2948 2008-05-17 22:28 .bashrc
drwxr-xr-x  3 <username> <username>    4096 2008-05-17 22:44 .cache
drwxr-xr-x  3 <username> <username>    4096 2008-06-10 20:51 .config
drwxr-xr-x  2 <username> <username>    4096 2008-05-24 12:15 Desktop
-rw-------  1 <username> <username>      28 2008-05-24 12:03 .dmrc
drwxr-xr-x  5 <username> <username>    4096 2008-05-26 14:07 Downloads
-rw-------  1 <username> <username>      16 2008-05-17 22:44 .esd_auth
drwx------  4 <username> <username>    4096 2008-06-14 07:35 .gconf
drwx------  2 <username> <username>    4096 2008-06-14 07:35 .gconfd
-rw-r-----  1 <username> <username>       0 2008-05-24 21:30 .gksu.lock
drwx------  8 <username> <username>    4096 2008-05-24 12:19 .gnome2
drwx------  2 <username> <username>    4096 2008-05-17 22:44 .gnome2_private
drwx------  2 <username> <username>    4096 2008-06-10 20:51 .gnupg
drwxr-xr-x  2 <username> <username>    4096 2008-05-17 22:44 .gstreamer-0.10
-rw-r--r--  1 <username> <username>     112 2008-05-24 21:29 .gtk-bookmarks
drwx------  2 <username> <username>    4096 2008-05-17 22:44 .gvfs
-rw-------  1 <username> <username>    1272 2008-06-10 20:51 .ICEauthority
drwxr-xr-x  2 <username> <username>    4096 2008-05-17 22:49 .icons
drwxr-xr-x  3 <username> <username>    4096 2008-05-17 22:44 .local
drwx------  3 <username> <username>    4096 2008-05-17 22:44 .metacity
drwx------  4 <username> <username>    4096 2008-05-23 15:09 .mozilla
drwxr-xr-x  3 <username> <username>    4096 2008-05-24 12:19 .nautilus
-rw-r--r--  1 <username> <username>     586 2008-05-17 22:25 .profile
drwxr-xr-x  2 <username> <username>    4096 2008-05-24 12:19 .pulse
-rw-------  1 <username> <username>     256 2008-05-17 22:44 .pulse-cookie
-rw-r--r--  1 <username> <username>     218 2008-05-24 12:19 .recently-used.xbel
-rw-r--r--  1 <username> <username>     127 2008-05-20 17:45 .screenrc
drwx------  2 <username> <username>    4096 2008-05-17 22:44 .ssh
-rw-r--r--  1 <username> <username>       0 2008-05-17 22:28 .sudo_as_admin_successful
drwxr-xr-x  2 <username> <username>    4096 2008-05-17 22:49 .themes
drwx------  3 <username> <username>    4096 2008-05-17 22:49 .thumbnails
drwxr-xr-x  5 <username> <username>    4096 2008-05-23 16:23 .transmission
drwxr-xr-x  2 <username> <username>    4096 2008-05-23 15:08 .update-manager-core
drwx------  2 <username> <username>    4096 2008-05-17 22:44 .update-notifier
drwxr-xr-x  2 <username> <username>    4096 2008-06-10 20:51 .vnc
drwxr-xr-x  2 <username> <username>    4096 2008-06-10 11:58 WWW
-rw-------  1 <username> <username>     508 2008-06-14 23:22 .Xauthority
-rw-------  1 <username> <username> 8253832 2008-06-12 12:57 .xsession-errors
```

This is the /home/<username>/WWW/
```
total 12
drwxr-xr-x  2 <username> <username> 4096 2008-06-10 11:58 .
drwx------ 27 <username> <username> 4096 2008-06-14 23:23 ..
-rwxr-xr-x  1 <username> <username>   24 2008-06-08 20:54 index.php
```

---

### Post by soulresin on 2008-06-15
drwx------ 27 <username> <username>    4096 2008-06-14 23:22 .

Permissions on /home/username are only 700, so Apache doesn't have permission
to see /home/username/WWW

Try setting /home/username to 711 to see if that does the trick.  Looks like /home/username/WWW is already 755 so no worries there.

---

### Post by x12Networks on 2008-06-18
I cannot believe it was something that stupid.  I changed the users dir to 711 and it worked fine.  Thank you both VERY MUCH! :)

---

