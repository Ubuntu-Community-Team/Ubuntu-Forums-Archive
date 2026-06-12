---
title: "n00b question- give bash more permission?"
date: 2009-09-23
forum: Security
---

### Post by davea0511 on 2009-09-23
Sorry for the n00b question but even after hours of searching I can't seem to figure out what's probably obvious to everyone else.

I'm making a bash script that will let somebody refresh the content on a kiosk by plugging in a thumbdrive and rebooting the machine.  Unfortunately bash script gives me a "permission denied" for many file operations.

Part of the problem is that Ubuntu is making everything on my thumbdrive that way.  I've tried chmod to no avail, they still end up with 700 permissions:
```
###at bash prompt:
 sudo chmod 777 /media/disk/*
 ls -l /media/disk
====
###Output:
 -rwx------ 1 user root 12697697 2006-10-25 08:42 Cpanels.swf
 -rwx------ 1 user root     8574 2009-09-22 17:29 kioskLogistics.sh
 -rwx------ 1 user root     4788 2009-09-22 12:26 kioskLogistics.sh~
 -rwx------ 1 user root 18604854 2009-09-22 04:30 kiosk.swf

```
So if I start with read-only files, I'm going to have all kinds of problems once I copy them to the HD to manipulate with bash scripting because I'm stuck with the read-only, yes?  I can't delete them or write over them.

Anyone show compassion to a n00b here?  Does it have something to do with FSTAB (of which I really know practically nothing) to get the thumbdrives to mount not as -ro?  O thought I could mount it myself as -rw but I get permission errors when I do that by bash.  Even then, if they 755 bash script can't delete or write over them can it, unless it's root?

Again, I'm a newbie ... so if you just want to point me in the right direction that's cool.

---

### Post by davea0511 on 2009-09-23
Another problem I noticed, and this also happens at the bash prompt as wll as in a script even if I'm su ... if I copy a 777 permissions file to another folder (a 777 permissions folder), it copies over as 755 permissions (-rwxr-xr-x).  Now that becomes a problem doesn't it if I'm doing bash scripting, because a bash script then cant write over it or delete an 755 file can it?

So bash script executes file io commands with the same permissions as world (public, whatever you call it)?  Can that be changed?

---

### Post by Lars Noodén on 2009-09-24
It's hard to guess without knowing more details, but some of the operations might need root access.  Is that correct?  If so be careful.  Try setting up access in /etc/sudoers for the programs needed.  

Assigning group-level access makes the task easier to manage and test, because the system already has easy ways to manage group membership.  

For example:
[indent]
# *Any user in the group network can run any program*
# *listed in the short cut 'NETWORK' without a password*
# *using any combination of parameters*
Cmnd_Alias  NETWORK=/usr/local/bin/nmap, \
		/usr/local/bin/tcpdump, \
		/usr/local/bin/scanssh
%networkers ALL = NOPASSWD: NETWORK
[/indent]

You'll probably want to use mount, rsync and a few others.  You'll probably want to limit the parameters used or even limit sudoers to specific scripts.  

There aren't any really great sudoers tutorials out there.  But if you have basic regex (regular expressions) mastered and can do some trial and error, sudoers should be easy.

Is that in the right direction?

---

### Post by jpkotta on 2009-09-24
Yes, it all has to do with /etc/fstab.  Your thumbdrive is probably a FAT filesystem, and FAT cannot store permissions, which is why the chmod command does nothing.  For filesystems that don't support unix permissions, Linux will set the permissions for all files and directories when the fs is mounted.  The relevant mount options are fmask and dmask, which mask out the permission bits that you *don't* want set.  To get permissions of 755 on directories, you need dmask=022.  Here is the fstab entry I use:
```
/dev/sdc1                                 /media/removable vfat   rw,user,noauto,fmask=177,dmask=077 0 0
```  The "user" option means make the user who ran the mount command owner of the files.

I don't know how to make that all work with automounting.

Your copying problem is different.  That is probably caused by the default permissions being applied.  The default permissions are set by the umask command, which works the same way as the mask options above.  Put e.g. ```
umask 0022
``` for default permissions of rw-r--r-- (x bit is ignored for files).

---

### Post by Sarmacid on 2009-09-24
To understand permissions in linux you should take a look at this [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by davea0511 on 2009-10-09
Thanks for the help!  It just suddenly started working for me.  Not sure what I changed, but having your info on hand will be useful if I see it again!

---

