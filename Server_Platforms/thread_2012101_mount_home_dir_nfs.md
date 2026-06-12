---
title: "mount home dir nfs"
date: 2012-06-28
forum: Server Platforms
---

### Post by brunovila on 2012-06-28
I have the following structure for the home dirs of users

```
/home
  |-somedir
       |-school1
           |-user1
           |-user2
            ......
           |-userN
       |-school2
           |-userk1
           |-userk2
            ......
           |-userkN

```how can I export theese home dirs by nfs and mount them in clients with autofs?

---

### Post by SeijiSensei on 2012-06-28
If /etc/passwd has the correct home directory for each user, you could just export /home and mount it as /home on the NFS client. All those usernames would have to be unique, though, with home directory entries in /etc/passwd like 

```
user1:x:1001:1001::/home/somedir/school1/user1:/bin/bash
```

That means there cannot be an identical "user1" in another school.  If there are duplicate account names, you'll have to come up with another naming scheme so all the accounts are unique.

All the users' uid's and gid's need to match as well.  If user1 is user 1001 on the client, she should be user 1001 on the server as well.  There are ways around this, but things are a lot easier if they all match.  You can use NIS if you want to consolidate the user accounts on the NFS server.

You'll need to export /home off the server with no_root_squash enabled so you can mount it as root on the client to /home.

---

