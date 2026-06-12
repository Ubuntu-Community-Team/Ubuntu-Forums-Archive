---
title: "Permissions Issue"
date: 2010-08-15
forum: Server Platforms
---

### Post by ask21900 on 2010-08-15
I am sorry if this is a really simple issue that has been posted before, but I am not good with permissions and I have searched for hours for a solution.

[LIST]
[*]I have set /var/www recursively to 771
[*]I have recursively set the group for /var/www to www-data
[*]I have added a user to the www-data group (usermod -a -G www-data)
[*]Apache seems to be able to read/write as required (realistically, apache does not need to write to /var/www, but does need to write to some subfolders)
[*]The user is able to list & open /var/www, but not write
[*]The user is not able to list or open any subfolders in /var/www[/LIST]


Can someone please provide me with some direction on this?  Any help would be greatly appreciated!

---

### Post by Ryan Dwyer on 2010-08-15
Please provide the output of:

id username # eg. id johnsmith
ls -l /var/www

---

### Post by ask21900 on 2010-08-15
> **Ryan Dwyer said:**
> Please provide the output of:

id username # eg. id johnsmith
ls -l /var/www


For security reasons, I have replaced sensitive info with <tags>


uid=1000(<username>) gid=1000(<username>) groups=1000(<username>),4(adm),20(dialout),24(cdrom),33(www-data),46(plugdev),104(lpadmin),115(admin),120(sambashare),1001(admins),1002(webadmins)



drwxrwx--x 2 root     www-data  4096 2010-08-14 19:58 <folder>
-rwxrwx--x 1 root     www-data   342 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   482 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   990 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   255 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data 13578 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  5141 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1026 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   290 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  3032 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data 20625 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   583 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  3477 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   907 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  9542 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2632 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2688 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2838 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  5127 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1303 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2257 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2873 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2929 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   590 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1929 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   111 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data    75 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2867 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2366 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2377 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1013 2010-08-14 19:58 <file>.js
-rwxrwx--x 1 root     www-data  2052 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1171 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data    89 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1238 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  4070 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   510 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  4012 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data 13414 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  2076 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  8400 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data    23 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  7611 2010-08-14 19:58 <file>.php
drwxrwx--x 2 root     www-data  4096 2010-08-15 00:34 <folder>
drwxrwx--x 5 root     www-data  4096 2010-08-14 19:58 <folder>
-rwxrwx--x 1 root     www-data  1106 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  1941 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  3615 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data   275 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data  3191 2010-08-14 19:58 <file>.php
-rwxrwx--x 1 root     www-data 14825 2010-08-14 19:58 <file>.php

---

### Post by bprins on 2010-08-15
sudo chown yourusername /var/www

then your user owns the files, and you can give him read rights only if you like.

---

### Post by ask21900 on 2010-08-15
> **bprins said:**
> sudo chown yourusername /var/www

then your user owns the files, and you can give him read rights only if you like.

While that would fix the immediate problem of this specific user not being able to modify the files, etc., I am concerned with (near) future implementation.  I need to have others access the files/folders as well.

I really need to find out why the system is not allowing the group members to modify the files.

---

### Post by bprins on 2010-08-15
ok, then try

su yourusername

chown yourusername:yourgroupname
chmod g=r /var/www

now all users in the group "yourgroupname" are able to read in /var/www

does that help?

google on "chmod"
google on "chown"

it will give all the answers you are looking for :)

---

### Post by mdlueck on 2010-08-15
I came up with the following spec how to achieve group-writable files for the /srv/www area on our servers:

```
Start with non-ACL perms:

sudo mkdir /srv/www
sudo chown -R www-data:www-data /srv/www
sudo chmod 0775 /srv/www
sudo sudo chmod g+s /srv/www

With ACL support on the filesystem:

sudo setfacl -d -m mask::rwx /srv/www

Check the ACL perms:

sudo getfacl -d /srv/www
getfacl: Removing leading '/' from absolute path names
# file: srv/www
# owner: www-data
# group: www-data
user::rwx
group::rwx
mask::rwx
other::r-x
```

We make users that have write access to /srv/www a member of the www-data group.

Unfortunately one hosted VPS box can not support ACL's, so that box is a bit awkward.

---

### Post by ask21900 on 2010-08-16
> **mdlueck said:**
> I came up with the following spec how to achieve group-writable files for the /srv/www area on our servers:

That worked.  I am curious as to why it did not work the first time (being as it was essentially the same as what you offered).  Thank you for your help!

I am now having a problem within the same issue.  Anytime a user of the group modifies a file, apache gets a "Permission Denied" error.  Reissuing the chgrp -R on the dir re-enables apache's access.  The strangest part is that none of the other users loose access, and ls -l doesn't show any changes in the modified files' permissions.

---

### Post by mdlueck on 2010-08-16
> **ask21900 said:**
> I am now having a problem within the same issue.  Anytime a user of the group modifies a file, apache gets a "Permission Denied" error.

Since you implemented my suggested syntax / already!? How odd. I have never seen that sort of thing happen.

You followed the steps exactly and already are getting this trouble???

Ma ei tea... (I do not know...)

---

