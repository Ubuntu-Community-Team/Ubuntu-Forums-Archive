---
title: "root user cannot change delete nor create any file"
date: 2008-07-29
forum: Server Platforms
---

### Post by maq21 on 2008-07-29
Dear All;
I have Ubuntu 6.06.1, and I'm running it as dns server, The problem that occur is that the root user cannot change create nor delete any file and the thing that make me feel in crazy is that the root user own these files but it cannot make any change by the way the permitions is -rw-r--r- for any file
plzzzzzzzz help me plzzzzzz

---

### Post by ilrudie on 2008-07-29
> **maq21 said:**
> Dear All;
I have Ubuntu 6.06.1, and I'm running it as dns server, The problem that occur is that the root user cannot change create nor delete any file and the thing that make me feel in crazy is that the root user own these files but it cannot make any change by the way the permitions is -rw-r--r- for any file
plzzzzzzzz help me plzzzzzz

Are you sure you are actually root?  Ubuntu disables the root account by default so you can't login as root unless you have made changes.  Run ```
id
``` to determine which user you are.  If you are not root you can become root by running ```
sudo su -
``` or run any command as root by using sudo.  Use gksudo if you need to run gui applications as root.

---

### Post by cdenley on 2008-07-29
Does root have write permissions for the parent directory?

---

### Post by ilrudie on 2008-07-29
> **cdenley said:**
> Does root have write permissions for the parent directory?
Not really important.  root always has write permissions.  Even when you specifically say root does not have write permissions it still does. Programs that check for permissions like vi will say that the file is read only but you can still force a write if you are root.

---

### Post by knightcoder on 2008-07-29
root = God

---

### Post by ilrudie on 2008-07-29
haha, nice avatar.  What do you call it?  Battux?  Batpenguin?

---

### Post by pauper on 2008-07-29
> **maq21 said:**
> ...The problem that occur is that the root user cannot change create nor delete any file...

Did you by any chance change file attributes?

```
man lsattr
man chattr
```

---

### Post by maq21 on 2009-09-24
Hello guys,

Sorry the issue was because of "system corruption" so as you know when that case occur you cannot do anything, so the system protect itself and no one can edit files nor create new ons. .... ;):lolflag:

---

### Post by maq21 on 2010-01-14
The real issue is when there is a lot of errors on the file system (ext3 fs) there is option on the mount is "errors=remount-ro" which will remount the file system in read only mode 
and thats it, so the solution maybe will be remount it with r/w mode (but I didnt test it so i dont recommond that except in case that you dont have any other solution) normally the solution is reinstall the os but of course after you backup your data.

---

