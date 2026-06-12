---
title: "Every Linux file permission listed &amp; explained (all 4,096 of them)"
date: 2017-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by sonicwind on 2017-08-10
I found this page today and thought I would share. It shows every possible permission with its numeric mode, what the permissions look like, and an explanation.

[http://ixbrian.com/unixpermissions.html](http://ixbrian.com/unixpermissions.html)

This page goes with it as an introduction: [https://www.ibm.com/developerworks/community/blogs/brian/entry/every_possible_unix_linux_file_permission_listed_and_explained_all_4_096_of_them?lang=en](https://www.ibm.com/developerworks/community/blogs/brian/entry/every_possible_unix_linux_file_permission_listed_and_explained_all_4_096_of_them?lang=en)

---

### Post by ajgreeny on 2017-08-10
It would have been more helpful to almost everyone if the web-page explained what **sticky bits**, **SGID** and **SUID** were.

I had to do a quick search to make sure I was correct about them, but I can imagine that to most people it will be just gobbledegook.

---

### Post by #&amp;thj^% on 2017-08-10
> **ajgreeny said:**
> It would have been more helpful to almost everyone if the web-page explained what **sticky bits**, **SGID** and **SUID** were.

I had to do a quick search to make sure I was correct about them, but I can imagine that to most people it will be just gobbledegook.
+1 :)
Kind of a brief/short meanings?examples

Set-user Identification (SUID)

Have you ever thought, how a non-root user can change his own password when he does not have write permission to the /etc/shadow file. hmmm… interesting isn’t it? Well to understand the trick check for the permission of /usr/bin/passwd command :

```
# ls -lrt /usr/bin/passwd
-r-sr-sr-x   1 root     sys        31396 Jan 20  2014 /usr/bin/passwd

```
If you check carefully, you would find the 2 S’s in the permission field. The first s stands for the SUID and the second one stands for SGID.
– When a command or script with SUID bit set is run, its effective UID becomes that of the owner of the file, rather than of the user who is running it.
Another good example of SUID is the su command :

```
# ls -l /bin/su 
-rwsr-xr-x-x 1 root user  16384 Jan 12 2014 /bin/su

```
** The setuid permission displayed as an “s” in the owner’s execute field.

**SGID on a directory**
** When SGID permission is set on a directory, files created in the directory belong to the group of which the directory is a member.
 For example if a user having write permission in the directory creates a file there, that file is a member of the same group as the directory and not the user’s group.
 This is very useful in creating shared directories.

How to set SGID on a directory

```
# chmod g+s [path_to_directory]
```


***** The sticky bit is primarily used on shared directories.**
 It is useful for shared directories such as /var/tmp and /tmp because users can create files, read and execute files owned by other users, but are not allowed to remove files owned by other users.
** For example **if user bob creates a file named /tmp/bob, other user tom can not delete this file even when the /tmp directory has permission of 777. If sticky bit is not set then tom can delete /tmp/bob, as the /tmp/bob file inherits the parent directory permissions.
root user (Off course!) and owner of the files can remove their own files.
This was from another site but I had no address to link here.
So Kudos/credit belongs to someone else and not me.

---

### Post by vocx on 2017-08-10
> **ajgreeny said:**
> It would have been more helpful to almost everyone if the web-page explained what **sticky bits**, **SGID** and **SUID** were.
This is correct.

This is like a multiplication table. When kids are in school, they typically learn the products between the first ten numbers. There is a reason people don't learn multiplication tables beyond that. It's unnecessary if you already know how to make additions, and the rules of multiplication for the previous nine numbers.

So, if I wanted to multiply 13 x 15, I don't need to memorize the result with the help of a table. Instead, I need to know how larger multiplications are produced.
```

13 = 10 + 3
15 = 10 + 5
(13) x (15) = (10 + 3) x (10 + 5) = 100 + 50 + 30 + 15
(13) x (15) = 195

```

So, Linux permissions are the same. You don't need a huge table with all combinations. Instead, it's better to learn the rules behind the octal and binary numbers so any permission can be understood.
```

0754

s       u     g     o
0       7     5     4
000   111   101   100
---   rwx   r-x   r--

```

And yeah. I don't think the regular user, or even the advanced user, would know readily know about the sticky bits, SUID, SGID. That's almost never used, except in a few cases.

---

