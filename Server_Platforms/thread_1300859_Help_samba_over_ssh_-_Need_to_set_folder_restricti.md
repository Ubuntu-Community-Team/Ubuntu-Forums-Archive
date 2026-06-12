---
title: "Help samba over ssh - Need to set folder restrictions"
date: 2009-10-25
forum: Server Platforms
---

### Post by photoman355 on 2009-10-25
Hi 

I'm setting up my first server so hoping someone can help out a noob.  

I have unbuntu server 8.04lts with samba, openssh, and webmin installed.  Both samba and openssh are working but when I connect to the server remotely over ssh the folder permissions which were set in samba for my wired network no longer apply and users have access to the full directroy.  

What's the best way of restricting user access to certain folders?

---

### Post by Lars Noodén on 2009-10-25
In the shell, look at how the filesystems are mounted and what file systems are being used.  You can use [FONT="Courier New"]mount[/FONT] to see that.

You'll want their home directories in the smbfs mount and not one of the ext mounts.

---

### Post by photoman355 on 2009-10-25
Sorry I should add some more info here.

I have 2 mirrored hard drives mounted.  One drive is for OS/Progs, the other is for docs etc.  On the docs drive my shares are distributed to various users so I have eg a docs share which is accessible by all users and an office share which is only accessible by a select few.

Under samba in my wired network its fairly easy to restrict a users access to these files, however I don't know the best way to setup similar restrictions for users connecting over ssh.

It would be nice if there was a way of pulling over the samba permissions but it seems like ssh permissions have to be configured separately?

---

### Post by Lars Noodén on 2009-10-25
Not really.  

What does it say when you run mount:
```

 mount

```

That will show you where your smb file system is mounted, if it is mounted.

---

