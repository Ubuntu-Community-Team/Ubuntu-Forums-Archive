---
title: "Problems with chown"
date: 2006-10-02
forum: Server Platforms
---

### Post by Keymaster on 2006-10-02
When I change the owner of a file to root:root, and the permissions to 744 (this is a text file, but it does this with all files) the file can still be sent to the trash, and then deleted from there by other users.  I don't understand why this is happening.  It just started happening last night, and is still happenening even after formatting the harddrive, and reinstalling ubuntu.  I am using Ubuntu 6.06.  It even does this from the Live CD, and this is a major problem for me.  Also sometimes the changes that do go through on the permissions don't show up right away, and it appears to be unchanged.  I have tried verbose to see what is going on, and all the commands (chown, and chmod) do take effect, but the users (not the ones I chowned it to) can still send the file to the trash.  Please help me ASAP!  Thanks

---

### Post by wieman01 on 2006-10-03
If you want to secure a file then you need to change the "group" as well:
> sudo **chgrp** root <your file>
> sudo **chown** root <your file>

---

### Post by Keymaster on 2006-10-03
yes but chown can do both by using
```
chown user:group objecttobechanged
```
The problem is that even after successfully changing the permissions, owner, and group (and it reports them changed) Others can still delete that file.

---

### Post by skymt on 2006-10-04
Here's the solution: make the directory "sticky". When a directory is "sticky", only the owner of a file or the owner of the directory can delete or move a file.```
chmod +t /path/to/directory
```

---

### Post by Keymaster on 2006-10-04
The directory is the desktop of the account "guest"  The file I want to protect is "Read Me Now" that way guests can see a read me with some info in it, but can't change/delete it.  That way other guests can see the same info.  If I change the directory to sticky, can't the guest account change it back?  Also if I change the owner of the Desktop directory, won't Ubuntu say there is a problem with the account?

---

### Post by skymt on 2006-10-05
> **Keymaster said:**
> The directory is the desktop of the account "guest"  The file I want to protect is "Read Me Now" that way guests can see a read me with some info in it, but can't change/delete it.  That way other guests can see the same info.  If I change the directory to sticky, can't the guest account change it back?  Also if I change the owner of the Desktop directory, won't Ubuntu say there is a problem with the account?

My advice? Try it. See if it works. If it doesn't, change it back and find another way.

chown the Desktop directory to another user (maybe root), and give the guest user rwx permissions. It should work.

---

