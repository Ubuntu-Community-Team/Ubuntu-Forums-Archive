---
title: "group ownership permissions"
date: 2006-09-17
forum: Server Platforms
---

### Post by dnel on 2006-09-17
Hi, I am having some difficulty with file permissions which I admit I don't know too much about.

The situation is, I have a folder which holds music files and I want anyone in the 'audio' group to have read and write access to.

To do this I have changed the ownership of all files and directories to root:audio and get the permissions to include group write. Whether this is the best way of doing this I don't know, perhaps someone could enlighten me otherwise?

The problem is that when I create a new file I want it to inherit the permissions of the parent folder but when I create a new file/directory it gives it the user group by default. 

The folder is contained within a hard disk which houses other folders so it won't be possible to set this via fstab for the whole disk.

Can anyone help me with this?

TIA
Dave

---

### Post by kidders on 2006-09-17
The SGID bit holds the answer :-) If you google "advanced linux permissions", you might get hold of some commentary about it. Basically, once you set it on a directory, any files added to it will have the directory's own group setting forced upon them.

---

### Post by dnel on 2006-09-17
> **kidders said:**
> The SGID bit holds the answer :-) If you google "advanced linux permissions", you might get hold of some commentary about it. Basically, once you set it on a directory, any files added to it will have the directory's own group setting forced upon them.

Brilliant! Thanks for the fast reply. I googled it and it came up with some info then all I did was run

```
chmod g+s audio/
```

and it worked first time :)

---

### Post by kidders on 2006-09-17
Glad to hear it :-)

---

