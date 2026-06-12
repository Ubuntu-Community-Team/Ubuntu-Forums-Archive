---
title: "ACLs in Ubuntu 12.04 LTS?"
date: 2012-06-15
forum: Security
---

### Post by joec2000 on 2012-06-15
Hi Everyone,

I've got a server with Ubuntu 12.04 LTS with the latest updates. Using OpenLDAP (slapd) for authentication. Filesystem in question is ext4

I'm seeing strange behavior from ACLs in Ubuntu 12.04. If I grant access to a directory to a security group using setfacl, I'm noticing that users NOT in that security group also get access.

Here are two example users:

[FONT=Courier New]root@zeus:/data# getent passwd | grep joe
joe.collins:*:5002:1000:Joe Collins:/data/home/joe.collins:/bin/bash
joe.wolczanski:*:5014:1001:Joe Wolczanski:/data/home/joe.wolczanski:/bin/bash
[/FONT]
Here is the group setup (irrelevant user accounts & groups removed):

[FONT=Courier New]root@zeus:/data# getent group | grep joe
jdiadmin:*:1000:joe.collins
jdiacctg:*:1002:joe.wolczanski
[/FONT]
Notice that joe.collins is NOT a member of jdiacctg but joe.wolczanski is.

Here are the permissions on the directory I'm noticing the issue on:
[FONT=Courier New]
root@zeus:/data# ls -ltr
drwxrwx---+  2 root        root     4096 Jun 15 10:25 acctg

root@zeus:/data# getfacl acctg/
# file: acctg/
# owner: root
# group: root
user::rwx
group::rwx
group:jdiacctg:rwx
mask::rwx
other::---[/FONT]

So, joe.wolczanski is able to access /data/acctg:
[FONT=Courier New]joe.wolczanski@zeus:/data$ cd acctg/
joe.wolczanski@zeus:/data/acctg$ ls -ltr
total 0
-rw-r--r-- 1 joe.collins jdiadmin 0 Jun 15 10:25 foo
[/FONT]
But so is joe.collins.... why?
[FONT=Courier New]joe.collins@zeus:/data$ cd acctg/
joe.collins@zeus:/data/acctg$ ls -ltr
total 0
-rw-r--r-- 1 joe.collins jdiadmin 0 Jun 15 10:25 foo
[/FONT]
If I do a setfacl -b /data/acctg, then both joe.collins and joe.wolczanski immediately lose access.

Anyone have any ideas?

Thanks,

- Joe

---

### Post by joec2000 on 2012-06-20
Any ideas? Could this be a bug?

Thanks!

- Joe

---

### Post by Shilong on 2012-06-20
Using dots in usernames is not trivial - maybe try the same setup with usernames without dots. 
You could also try two users with a different first name before the dot (this is just an idea, but it looks like your settings are applied to the user "joe." or "joe" - which would of course match both users)

cheers
Shilong

---

