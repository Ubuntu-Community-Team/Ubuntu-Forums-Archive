---
title: "FileZilla / SFTP permission question"
date: 2010-08-27
forum: Server Platforms
---

### Post by raccer on 2010-08-27
Hi,
(just setup 1st server, still a *nix noob)

I have openSSH up & running, can make files & directories via my putty client, yet when I log-in via FileZilla with the same account, I get permission denied if I try to write anything, so essentially my write permission is lost (going in through FileZilla)

If it matters, I'm working in the /var/www

Thanks for help w/ the basics!

---

### Post by arrrghhh on 2010-08-27
Does the user you login with own & have rights to /var/www?

You may have been making changes with the 'sudo' command in /var/www, meaning you were basically root when making those changes - not your user.

Do a ```
ls -la /var/www
``` to list permissions for that directory...

---

### Post by raccer on 2010-08-27
Yea, I was using sudo inside the putty... 
I looked up a page explaining unix permissions,
[http://www.dartmouth.edu/~rc/help/faq/permissions.html]("http://www.dartmouth.edu/~rc/help/faq/permissions.html"),
it shows I have rwx, read write execute, right?
Thus the confusion... 

```

me@ubuntu:~$ ls -la /var/www
total 12
drwxr-xr-x  3 root root 4096 2010-08-27 11:56 .
drwxr-xr-x 15 root root 4096 2010-08-25 11:58 ..
drwxr-xr-x  3 root root 4096 2010-08-27 11:51 newdir

```

PS Thanks for the reply!

---

### Post by arrrghhh on 2010-08-27
Since the directory is owned by root, and permissions of the user are the first set (rwx), group has only read and execute (r-x) and "other" - everyone else - only has read and execute.

Typically, a web server directory should NOT be owned by root.  It should be owned by www-data - however, that user should not have write permissions to that directory (I'm talking best practices here... it's by no means required, just recommended for security.  You don't want apache being able to make changes to the webroot basically.)

Quick-n-dirty solution would be to give 777 permissions - or rwx to all user/group/other.  Not exactly *best practices*, but it'll help you test.  Then you can dial back the permissions until you get them right.

---

### Post by raccer on 2010-08-27
Ok, I think I'm starting to understand...

I didn't notice the 'owner' or 'associated group' columns before on the page explaining permissions.

So ideally (best practices) a user 'www-data' would be created, not the 'owner' of all the files hosted/available via http, and files & directories (under this user) would have these permissions:

'dr-xr-xr-x  3 www-admin www-data 4096 2010-08-27 11:51 newdir'

Then another user/account, the 'owner' 
(listed above as 'www-admin') 
would have elevated permissions, and be the account used to upload/change files, etc

When you mentioned apache being able to makes changes, I don't quite get that, does apache have it own account, or is it part of a generic group?

LMK if I missed some part of what you were getting at, thanks for the detail & taking the time to explain!

---

### Post by arrrghhh on 2010-08-27
You should already have a user www-data that was created when apache was installed (I believe...)

My statement may have been a little misplaced, I think permissions where apache is installed is more important than the docroot - with that said, the only place www-data should be able to write to is your upload directory - which should be located inside your docroot.

You may want to read [this](http://httpd.apache.org/docs/2.0/misc/security_tips.html) doc on security tips related to apache.

---

### Post by maikel.b on 2010-08-27
> **raccer said:**
> Yea, I was using sudo inside the putty... 
I looked up a page explaining unix permissions,
[http://www.dartmouth.edu/~rc/help/faq/permissions.html]("http://www.dartmouth.edu/%7Erc/help/faq/permissions.html"),
it shows I have rwx, read write execute, right?
Thus the confusion... 

```

me@ubuntu:~$ ls -la /var/www
total 12
drwxr-xr-x  3 root root 4096 2010-08-27 11:56 .
drwxr-xr-x 15 root root 4096 2010-08-25 11:58 ..
drwxr-xr-x  3 root root 4096 2010-08-27 11:51 newdir

```PS Thanks for the reply!


You can add a group upload to your system

groupadd upload

add a user for the upload to /var/www this user is in my suggestion www-upload 

useradd -d /var/www -s /bin/bash www-upload

user needs a password

passwd www-upload

give password
give password

Now change the permissions on the /var/www directory

chown root.upload /var/www ; chmod 775 /var/www/

add user www-upload to the group upload

usermod -G upload www-upload

Now try with filezilla to access the /var/www root directory.

This will be one of the options you have to access the /var/www map with a user..

One thing, the user can access other directory's 2 so its a secured connection, bud this user can see more than the /var/www directory.

success!

---

