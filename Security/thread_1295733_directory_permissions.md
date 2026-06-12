---
title: "directory permissions"
date: 2009-10-19
forum: Security
---

### Post by whaase on 2009-10-19
I'm hoping someone can help me. I come from a Windows enviornment and I having problems trying to figure out linux and permissions.

I'm used to being able to select a directory, setting individual permissions for any user(s). I'm not sure if I can do this in linux?

Eg. I have a directory called Media that I share out. I want account A to be able to read/write and delete files. User B can only Read. User C can read/write but not delete. Can this be done on a per user level?

Thanks!

---

### Post by madverb on 2009-10-19
If you want to do it via a GUI you can run the following command:
```
gksu nautilus
```
then you can change the permissions on any folder. Just be careful though.

---

### Post by whaase on 2009-10-19
> **madverb said:**
> If you want to do it via a GUI you can run the following command:
```
gksu nautilus
```
then you can change the permissions on any folder. Just be careful though.

I don't have a gui. Its on a server running 8.04.3 LTS

---

### Post by vipulkelkar on 2009-10-19
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Have a look at this if it helps

---

### Post by whaase on 2009-10-23
Thanks. Looks like the short answer in no.

---

### Post by edenCC on 2009-10-23
Yep, you can not do that normally, because creating new files and deleting a files are both needs write permission to its parent directory.

If you can pre-create some files, then User C can read/write but not delete.

---

### Post by rookcifer on 2009-10-24
Yes, **you can** do these things very easily.  You, and others here, are forgetting about the [sticky bit.]("http://en.wikipedia.org/wiki/Sticky_bit")

First make user 'A' own the directory *and* all files in it:

```
chown -R usera /media
```

You want user A to own the directory because he is the one that will be wielding the most power over it (rwx) and can also delete files.

Now create a group (we will call it media -- just make sure the group name is not already in use on the system.  If you don't want to create a new group, then just pick a group to add the /media directory to.).

```
sudo groupadd -rf media
```


Now, put the /media directory in the "media" group:

```
sudo chgrp media /media
```

Now add **user C** to the media group:

```
sudo gpasswd -a userc media
```

Now, here's what we have so far:

User A is the owner of the /media directory, meaning he can do *anything* he wants to it or its files.  We have a new group called "media" which is the name of the group the directory /media will be in.  User C is also a member of this group.  User B is *not* a member of the group.

Now let's set the actual permissions for the owner, group members, and those not in the group (the Unix "ugo" permissions system):

```
sudo chmod -R 1774 /media
```

The above command means that the owner can do anything -- read/write/delete/execute.  The group members (user C) can only read/write/execute -- *they cannot* delete.  And for those people not in the media group, they can only read (now you see why I did not add user B to the group).

If I were you, I would make a test directory and try this and make sure each user can only do what he is supposed to do.  And in the future, any users you want to be able to read/write but not delete, you simply add them to the group.  And any users you only want to have read access, well, you don't have to do anything because *every *non-group user on the system has read access.

The only possible issue you might have is if you want to allow more than one user (the owner) to delete files.  Only one person can own a file (well 2 if you include root but he doesn't count).  So, you will be limited to only having one person (other than root) be able to delete files.

EDIT:  If you really want to dive deep into permissions, you need to check out ACL's, which provide far more power than the older "ugo" paradigm.  However, I think the standard ugo can do exactly what you need in this case.

---

