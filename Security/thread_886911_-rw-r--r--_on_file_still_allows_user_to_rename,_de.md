---
title: "-rw-r--r-- on file still allows user to rename, delete, and move the file"
date: 2008-08-11
forum: Security
---

### Post by kevinfishburne on 2008-08-11
I have the following scenario:

```
/media/Data              drwxr-xrwx root root
/media/Data/Instructions -rw-r--r-- root root
```

I have a user in its own group and not a member of the root group. I need this user to be able to create and delete files in the /media/Data directory, but only have read access to the Instructions file contained within it.

With the above permissions the user is able to read, rename, move and delete the Instructions file, but can't modify its contents. Although the user can't modify the file's owner, group, or permissions, when the user moves it to the trash, for example, then moves it back, it becomes owned by the user and is in the user's group. The user then has full permissions on the file of course.

What appears to be happening is that move/rename/delete permissions are being inherited from the parent directory, and write permissions are taken from the file's explicitly set permissions. This is further supported by the fact that the user can't modify the /media/Data directory even though its permissions for 'others' are set to rwx.

Is there some other factor at work that I'm not aware of, and is it possible to set up permissions to accommodate the scenario I described? Also any reference on Unix/Linux permissions that doesn't read like source code comments would be appreciated.

---

### Post by hyper_ch on 2008-08-11
> **kevinfishburne said:**
> What appears to be happening is that move/rename/delete permissions are being inherited from the parent directory, and write permissions are taken from the file's explicitly set permissions.
That's how it works...


> **kevinfishburne said:**
> This is further supported by the fact that the user can't modify the /media/Data directory even though its permissions for 'others' are set to rwx.
because the top directory is "/" which is owned by root and non-root users have no access to it.

---

### Post by The Cog on 2008-08-11
Your problem is that renaming and deleting a file is actually an operation on the parent directory (to which the user has write access), and not an operation on the file itself. I don't know what youcould do about that. You could try looking at the command chattr which I think has more advanced access control than the normal ones. Or setting the sticky bit on the directory might be enough (chmod +s <dirname>) - that makes sure only the owner can delete the file, but I'm not sure about renaming.

---

