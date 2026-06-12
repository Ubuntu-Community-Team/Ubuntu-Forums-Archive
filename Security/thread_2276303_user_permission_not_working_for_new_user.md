---
title: "user permission not working for new user"
date: 2015-05-01
forum: Security
---

### Post by DocSnyd3r on 2015-05-01
Hi,

I have a strange problem, when I create new users the permissions don't work as expected.
Here is what I tried:

```

root@xx:/home# adduser forumpost
Adding user `forumpost' ...
Adding new group `forumpost' (1001) ...
Adding new user `forumpost' (1001) with group `forumpost' ...
Creating home directory `/home/forumpost' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
Sorry, passwords do not match
passwd: Authentication token manipulation error
passwd: password unchanged
Try again? [y/N] y
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for forumpost
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] y
root@xx:/home# ll
total 16
d---------  4 root      root      4096 Mai  1 19:40 ./
drwxr-xr-x 23 root      root      4096 Mai  1 18:55 ../
drwxr-xr-x  2 forumpost forumpost 4096 Mai  1 19:40 forumpost/
drwxr-xr-x  4 ts3       ts3       4096 Mai  1 19:26 ts3/
root@xx:/home# su forumpost
bash: /home/forumpost/.bashrc: Permission denied
forumpost@xx:/home$ cd forumpost
bash: cd: forumpost: Permission denied
forumpost@xx:/home$ exit
exit
root@xx:/home# uname -a
Linux schloer 2.6.32-042stab104.1 #1 SMP Thu Jan 29 12:58:41 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by TheFu on 2015-05-01
The permissions look fine to me.
Did you happen to setup home directory encryption during the installation?  If so, try logging out and logging in as "forumpost" userid. That should decrypt the $HOME.  If not encrypted, let us know and hopefully someone else will have some ideas. Perhaps the $HOME is on NFS storage and root cannot edit anything on that storage. Could be something else.

These are just a shot in the dark, but maybe .... 

Also, you might try **su - forumpost** instead. The manpage for su has details about the difference.

---

### Post by bapoumba on 2015-05-01
```
bapoumba@bapoumba-VBox-Mate-15:~$ ls -l /etc/bash.bashrc 
-rw-r--r-- 1 root root 2188 oct.  29  2014 /etc/bash.bashrc
```

```
bapoumba@bapoumba-VBox-Mate-15:~$ ls -l .bashrc 
-rw-r--r-- 1 bapoumba bapoumba 3760 févr. 28 18:17 .bashrc
bapoumba@bapoumba-VBox-Mate-15:~$ ls -l /home/test/.bashrc 
-rw-r--r-- 1 test test 3760 mai    1 21:41 /home/test/.bashrc
```

What are the permissions for you ?
I added a test user.

Edit : Sorry TheFu, did not see you posted :)

---

