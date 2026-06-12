---
title: "modify permission on jail user"
date: 2010-12-03
forum: Server Platforms
---

### Post by Rick Z on 2010-12-03
Does anyone know how to modify permission on jail user.  current jail user added to its /home/jail/*

How can I assign jail user(s) enough permission to access /opt, /var, or any other directories other than /home/jail/* ?

---

### Post by bab1 on 2010-12-03
> **Rick Z said:**
> Does anyone know how to modify permission on jail user.  current jail user added to its /home/jail/*

What permissions are you referring to?  Directory and file are modified by chmod, chgrp and chown.> 

How can I assign jail user(s) enough permission to access /opt, /var, or any other directories other than /home/jail/* ?

Wouldn't that defeat the purpose of the chroot jail?  If you allow the user to traverse the / directory they could go anywhere.  I am assuming presently the lowest level in the file system your jailed user can go is /home/jail/<users_home_dir>.

---

### Post by Rick Z on 2010-12-03
Agree with the statement.  How can I create a user only able to access its /home directory and a /opt or /var directory only?

Instead using jail user, would local user be sufficient enough?  if I just add this user to particular /opt/xxx group?

---

### Post by bab1 on 2010-12-03
> **Rick Z said:**
> Agree with the statement.  How can I create a user only able to access its /home directory and a /opt or /var directory only?

With judicious permissions on the file system and limiting the user to as few groups as possible.  Linux in general has these permissions already set up.> 

Instead using jail user, would local user be sufficient enough?  if I just add this user to particular /opt/xxx group?

By local user I assume you mean a user added to a local host's authorized users (adduser).  On my Ubuntu server the /opt filesystem is owned by root:root (755) .  This means that a mortal user has the read and execute rights already with the "world" rights (other).

Functionally this means that if you (as root) install an app at /opt/new_app, any user should be able to use it, but not alter or remove it.

Is that what you are looking for?

---

### Post by Rick Z on 2010-12-04
To make the long story short... under /opt/xxx directory and its sub-directories there're data and logs that user (jail user) need to be able to modify it (mostly read, archive).

I guess use useradd should have enough permission to achieve this task.  I am wondering if there's any way to modify it where user (abc) can only access to /opt/xxx and no other directories (including its /home direct).

---

### Post by jbrown96 on 2010-12-04
Setup chroot for the users normally. You will need to bind /opt inside the jail. basically you will need to do mount -o bind /opt/ /home/jail/opt.

I agree with bab1 that this is teetering on undermining the purpose of jails. They are designed to remove access to the outside filesystem hierarchy. However, the bind option for mount is the way around it. You might have luck seeing how to bind /dev and /proc, as those are typically "binded" in chroots (not that they should be in your case, just an example). They are lots of tutorials on binding /dev and /proc, modify for your needs.

---

### Post by bab1 on 2010-12-04
> **jbrown96 said:**
> Setup chroot for the users normally. You will need to bind /opt inside the jail. basically you will need to do mount -o bind /opt/ /home/jail/opt.

I agree with bab1 that this is teetering on undermining the purpose of jails. They are designed to remove access to the outside filesystem hierarchy. However, the bind option for mount is the way around it. You might have luck seeing how to bind /dev and /proc, as those are typically "binded" in chroots (not that they should be in your case, just an example). They are lots of tutorials on binding /dev and /proc, modify for your needs.

You are right **brown96**.  That will work. The problem I have with that is more "best practices" and the OP's limited understanding of Linux in general.

There have been many times were a Sys Admin has "fixed" a problem in a unique way, not documenting what they have done only to have a reboot or upgrade break the fix.  This has happened to me.  The Sys Admin had moved on and I was tasked with curing the problem.  :-(

To the OP.  Think of where the data is located relative to here: **/**.  Think of it as a path as in: **/data/[COLOR="Red"]private[/COLOR]/[COLOR="Blue"]public[/COLOR]**.  The user has to traverse this path.  You can't jump to the public directory.  If you cant get past the /data/private how are you going to going to see the /data/private/public directory.  The problem can be resolved by designing the file system with this in mind.  This will work /data/[COLOR="blue"]public[/COLOR]/[COLOR="Red"]private[/COLOR].  All users would be served  The public directory is open to all and the private directory access is only needed by those you feel need it.  You can't expect someone to have access to a house in the middle of the block but not let them walk down the street to get there.

The method **jbrown96** is suggesting will work.  It is just out of the box thinking (pun intended).  FYI:  /opt is not where you would normally store data in a Linux file system.

---

### Post by Rick Z on 2010-12-05
Thank you for the post!  I would give that a try and see if that works.

---

### Post by jbrown96 on 2010-12-05
> **bab1 said:**
> You are right **brown96**.  That will work. The problem I have with that is more "best practices" and the OP's limited understanding of Linux in general.

There have been many times were a Sys Admin has "fixed" a problem in a unique way, not documenting what they have done only to have a reboot or upgrade break the fix.  This has happened to me.  The Sys Admin had moved on and I was tasked with curing the problem.  :-(

To the OP.  Think of where the data is located relative to here: **/**.  Think of it as a path as in: **/data/[COLOR="Red"]private[/COLOR]/[COLOR="Blue"]public[/COLOR]**.  The user has to traverse this path.  You can't jump to the public directory.  If you cant get past the /data/private how are you going to going to see the /data/private/public directory.  The problem can be resolved by designing the file system with this in mind.  This will work /data/[COLOR="blue"]public[/COLOR]/[COLOR="Red"]private[/COLOR].  All users would be served  The public directory is open to all and the private directory access is only needed by those you feel need it.  You can't expect someone to have access to a house in the middle of the block but not let them walk down the street to get there.

The method **jbrown96** is suggesting will work.  It is just out of the box thinking (pun intended).  FYI:  /opt is not where you would normally store data in a Linux file system.

Actually that's incorrect. By binding mount points, it is possible to allow access to a particular sub-directory, without granting access to its parent. For example, if I want to give a user access to directory 'C' that's located at /A/B/C, normally that would involve granting o+rw permissions to /A/B. However let's say that the user is confined to a chroot that's at /1/2/. I can then do ```
mount -o bind /A/B/C /1/2/
``` The chrooted user will be able to see C at his root dir: /C, but won't know anything about /A or /A/B.

---

### Post by Rick Z on 2010-12-06
This works out perfect with our environment.

Thank you all!!!

---

### Post by Rick Z on 2010-12-06
How should I edit the /etc/fstab?

here is what it shows on the /etc/mtab

/opt/xxx /home/jail/home/abc/xxx none rw,bind 0 0

---

