---
title: "access to files on external drive"
date: 2009-02-04
forum: Security
---

### Post by amkei on 2009-02-04
Hi guys,

you won't believe me, but there are still people that have never started a thread (like me). So far I got all the answers I needed by searchin. So please be patient for any mistakes.

My question is a general one:

Let's say I save my personal files on an external ext2/3 formated disc. Then I will be owner and have the rwx permissions.

How far is there a protection of my files when connected to another linux machine?

Of course, root can always do everything. But what happens if a user with rwx permissions on the mounted disc wants to access them? 
And can I access my files on the other machine if I have the same user-account there?

thx
cheers

---

### Post by jerome1232 on 2009-02-04
It goes like this every user has a uid, in Ubuntu the first user is 1000, second user 1001, third 1002 and etc...

When you hook it up to another Linux machine and if that machine has a user with the uid of 1000, that will be the user that has "ownership".

At least that is my Understanding of how it works.

---

### Post by amkei on 2009-02-06
Ok. thanks for the info.

---

### Post by cjacobsen on 2009-02-06
With dual user accounts it should work fine; same user name and password on both computers.

---

### Post by e1mer on 2009-02-06
It's not enough to have the same username on both boxes.

In fact it's not even necessary.

The key is that the mount command (or the /etc/fstab ) specify the
uid of the mounted filesystem.

Unfortunately, looking at the man page for mount, it does not look like
the -ouid=nnn,-gid=nnn option flags apply to the ext3 file system.

You could mount the device read only, then copy an encrypted (GPG) tarball
to your directory to access the data, but if you mount it rw, then it's either open to everyone, or only open to root.

---

