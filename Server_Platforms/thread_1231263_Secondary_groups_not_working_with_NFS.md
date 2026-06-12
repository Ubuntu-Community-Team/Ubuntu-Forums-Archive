---
title: "Secondary groups not working with NFS"
date: 2009-08-04
forum: Server Platforms
---

### Post by velmont on 2009-08-04
Hello,

I´m using LDAP for groups and NFS for home dirs. My problem is as follows:

I only have a few groups, so it's not the problem everyone else had. When I've mounted a disk over NFS, I need to have my primary group in order to read in the groups I'm a member of. Secondary groups is not working.

```
root@machine:/home/user# smbldap-groupshow secret
...
gidNumber: 1504
displayName: secret
memberUid: user,anotheruser

root@machine:/home/user# su - user

user@machine:~$ groups
users secret

user@machine:~$ ls -ald ../secret/
drwxr-x--- 12 anotheruser secret 4096 2009-07-27 15:39 ../secret/

user@machine:~$ cd ../secret/
bash: cd: ../secret/: Permission denied

user@machine:~$ ls ../secret/
ls: cannot open directory ../secret/: Permission denied

```

But it works if I change the group to primary by hand with newgrp:

```

user@machine:~$ newgrp secret
user@machine:~$ cd ../secret/
user@machine:/home/secret$ ls
Nice secrets.txt

```

But my users cannot be expected to do this!

The server where the real files are held (the NFS server) do not know anything about users. And it shouldn´t, it´s only job is to export files via NFS and do backups.

---

### Post by velmont on 2009-08-05
This was probably wrong forum (as usual). As I get no answers. I should do it in the main support forum.

Here's the problem in text:

I only have a few groups, so it's not the problem everyone else had. When I've mounted a disk over NFS, I need to have my primary group in order to read in the groups I'm a member of. Secondary groups is not working.

---

### Post by aduran on 2009-08-24
Hi. I have been fighting with this all day long, and now *it seems* is working.
I had the exact same problem like you, and could not find any pointers on the net.

What i have done: remove the --manage-gids option in /etc/default/nfs-kernel-server

Now it seems to work fine, but i just did it right now, so i have not tested very much.

If you try this, please tell me if it worked for you.

Good luck!

---

### Post by velmont on 2009-08-24
You're my hero! I tested it as soon as I read your email. That stupid fix everyone on the internet is whining about (cannot have more than 16 groups) actually breaks the group functionality on our machines. Rather strange.

Thank you for giving me the pointer. I've spent so much time barking up the wrong tree here.

We'll get to secure file access in a good way again. Of course, I've also just tested it, but it actually did what it should.

---

### Post by aduran on 2009-08-25
hehe, great! We'll see if it keeps working :)

When i was searching on the net i found this bug report:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1616430.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1616430.html)

I guess it was you who filed it,  so maybe you could add the new info for the maintainers. Thanks.

Best regards,
Antonio

---

