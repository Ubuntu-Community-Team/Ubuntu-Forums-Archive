---
title: "Default 'Group' permissions on files copied from FAT32 ?"
date: 2008-03-09
forum: Security Discussions
---

### Post by bsmith1051 on 2008-03-09
When I copy the images from my digital camera they always default to Group=No Access permissions.  How can I make them default to Group=Read+Write?

I'm assuming the issue here is that the camera's memory card is FAT32 and has _no_ Group permission defined.  So where does the default No Access permission come from?

Alternatively, does the built-in Import Photos allow you to change the permissions?  I personally dislike it (at least as it currently exists in Ubuntu 7.04) and have been doing the import manually.

---

### Post by Mr. C. on 2008-03-09
I followed up in your other thread as well.

FAT32 does not have the same permissions model as typical *nix file systems.  You have to mount the vfat file system with options that *simulate* these permissions.  See **man mount**, and search for vfat, in particular, you want the options (uid, gid, and consider also umask, dmask, and fmask):

> 
uid=value and gid=value
    Set the owner and group of all files. (Default: the uid and gid of the current process.) 

umask=value
    Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current process. The value is given in octal. 

dmask=value
    Set the umask applied to directories only. The default is the umask of the current process. The value is given in octal. 

fmask=value
    Set the umask applied to regular files only. The default is the umask of the current process. The value is given in octal.


Mount the fat file system using **-o gid=*GID***, where GID is replaced with an appropriate GID common to the users in questions.

---

### Post by bsmith1051 on 2008-03-09
thanks for the detailed response.  But is there some way to make this the default on the automount?  If I have to do something manually I might as well just keep doing what I'm already dong.

---

### Post by Mr. C. on 2008-03-10
See response in your duplicate thread:

[http://ubuntuforums.org/showthread.php?p=4489417#post4489417](http://ubuntuforums.org/showthread.php?p=4489417#post4489417)

---

### Post by bsmith1051 on 2008-03-10
what duplicate thread?  That other thread is someone else's and with a more general question.  I initially tried to see if there was a simple clarification for that thread's discussion and, when it seemed there wasn't, I started a new thread specific to my question.  So let's just pretend it doesn't exist, ok?
_____________

If I'm understanding correctly, I need to do add an entry to my /etc/fstab that matches the label for my USB device and then specify the correct umask and gid?  Currently, the 'mount' option for my USB flash-drive is like this:
```
> mount
/dev/sda1 on /media/LEXAR MEDIA type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```
given that, what should the new entry in fstab read?  I'm assuming I need to use 'umask=002' so that both my wife and I have full 'rw' rights, and the group-owner can be either one of us (we're both members of the other's Group).

OR...

Would this only work if I was permanently mounting the USB device (obviously, I'm not).  In addition, I was really hoping to change the general default umask (and gid?) for any/all external devices.

---

