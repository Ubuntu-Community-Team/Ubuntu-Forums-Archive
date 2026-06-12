---
title: "Hacked file permissions - cannot change back"
date: 2012-01-03
forum: Security
---

### Post by tjg88 on 2012-01-03
My Ubuntu server was recently hacked by a brute force attack via SSH. The hacker changed permissions on certain system files (ps, netstat, find, etc.) that I cannot change back via sudo. The hacker changed the owners to 122:114, which don't exist. Any idea how to change these back to root:root? The system is now offline, lessons learned, and we're just trying to determine what files the hacker may have added to the sytem to determine what the intentions were.

---

### Post by Lars Noodén on 2012-01-03
The way you would change them back is to boot using a rescue CD and use chown.  

However, there is no way to know what else he changed so the ***only*** safe option is to back up your data and do a clean installation, wiping all the old system files.  This is an example of where it is very good to have a separate /home directory and any other data directories.

---

### Post by mattxhand on 2012-01-03
Unfortunately there isn't a whole lot you can do. You can try to chown root:root on what you need to, but since you don't know what the intentions were your best bet is to run a backup of your home directory and wipe the system.

---

### Post by iponeverything on 2012-01-03
The immutable attribute is set. Use "chattr" - though I would recommend a reinstall. 

The files are not stock, they are part of a rootkit.

---

### Post by fdrake on 2012-01-03
> **tjg88 said:**
> My Ubuntu server was recently hacked by a brute force attack via SSH. The hacker changed permissions on certain system files (ps, netstat, find, etc.) that I cannot change back via sudo. The hacker changed the owners to 122:114, which don't exist. Any idea how to change these back to root:root? The system is now offline, lessons learned, and we're just trying to determine what files the hacker may have added to the sytem to determine what the intentions were.
this is more a cracker then a hacker! :/
you can create a user with UID=122 and group 114
```

#groupadd newgroup -g 114
#useradd john -u 122 -g 114

```
btw i would backup your data and reinstall the system. You don't know what actual those bin-commands do!

---

### Post by fdrake on 2012-01-03
> **iponeverything said:**
> The immutable attribute is set. Use "chattr" - though I would recommend a reinstall. 

The files are not stock, they are part of a rootkit.

+1 quote man chattr
> 
A file with the `i' attribute cannot be modified: it cannot be deleted or renamed, no link can be created to this
       file  and no data can be written to the file.  Only the superuser or a process possessing the CAP_LINUX_IMMUTABLE
       capability can set or clear this attribute.



---

### Post by drdos2006 on 2012-01-03
> 
[http://www.linuxhowtos.org/Tips%20and%20Tricks/chattr.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/chattr.htm)

This tip explains how to use chattr to keep important system files secure. The "change attribute" command, or chattr, can be used to add or change existing file attributes for things such as synchronous updates, tighter file security, and more. However, this command is only available on ext2 or ext3 partitions.


So judging from this information, is it reasonable to assume that  ext 4 is unable to modified in the manner that the OP is outlining ?

regards

---

### Post by dFlyer on 2012-01-03
Backup and reinstall, is the only safe bet.

---

