---
title: "Help with md0 ownership"
date: 2007-11-24
forum: Server Platforms
---

### Post by ToyotaDiesel on 2007-11-24
I have a raid (md0) that I am trying to share via samba.  Samba seems to be configured fine, as I can share home directories, and can read/write just fine.  

My troubles come when I try to write, via samba, to my raid.  I can read, but not write.  I think my troubles lie in ownership/permissions.
I have created a folder in the raid, then manually changed the user/group from root to my username (via webmin) and I can successfully write to that folder in the raid via samba, but there is still something a miss since I cannot write to the root of the raid from a samba client, but I can write to it locally.

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=29338f5c-bb68-42f6-80a2-5880dab17979 /               ext3    defaults,erro$
# /dev/sda5
UUID=879c60fd-bb1b-4cab-9029-be0e82373ce5 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


/dev/md0  /vault  ext3  suid,user,dev,sync,exec  0  1


I've attached a screenshot of the tree in "file manager" from webmin.  (how can I see folder permissions via command prompt?)

What I'm trying to share is the "vault" mount, which is my md0.  The folder /vault/temp is the folder that I manually changed the group/user on, which allowed me to be able write to that folder from a samba client.  

What am I missing?  I know it is permissions to the vault mount, I just don't know where. 

TIA

---

### Post by koenn on 2007-11-24
I can't read webmin very well, but it looks asif /vault is owned by root:root. That may be the source  of your problem, but webmin doesn't show 'others' permissions so can't tell for sure. 

try
```
ls -al /vault  ## or ls -Ral /vault 
```
to list ownership and permissions 
also look at what smb.conf has re. valid users etc. 

my approach is usually to be rather pemissive in smb.conf and use filesystem permissions to manage file/directory access

---

### Post by ToyotaDiesel on 2007-11-24
Thanks.  I do believe the root:root ownership is the cause of my write issue.  I'll post the results and my smb.conf in a second, but I have a few questions first.

When would the root:root ownership have been applied?  In the mount options?  During the format?  

Also, how can I give it group ownership to another group.  I will admit, I don't have a solid understanding of group ownership / permissions in linux.  Thanks

---

### Post by ToyotaDiesel on 2007-11-24
Ok, looks like I've got it.  I found this post:

[http://www.linuxquestions.org/questions/showthread.php?p=2908117#post2908117](http://www.linuxquestions.org/questions/showthread.php?p=2908117#post2908117)

Which outlined changing ownership of the mount.

---

### Post by koenn on 2007-11-24
you probably created the directory/mount point /vault as root, so root owns it. 
you can change ownership with chown, modify permissions with chmod, and check the results with ls -al

the hard part is deciding what user/group should own /vault, and what permissions you need for "others". That depends on what you want to use the share for. 

After that, using chmod or chown is quite simple.

---

