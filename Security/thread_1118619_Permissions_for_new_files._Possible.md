---
title: "Permissions for new files. Possible?"
date: 2009-04-07
forum: Security
---

### Post by philsson on 2009-04-07
Hopefully a easy thing.

Background
I run a DRBL server to create image files (ghost files) through clonezilla of some clients. These clients boot from network (PXE through my DRLB server) booting the Server's ubuntu enviroment and saving the image files with **root **permission to /home/partimag/.

Everything works fine besides other users arent avaible to use these images because of their permissions (created from root acount through clonezilla). I would like to give all the new files in this particular DIR the 777 permissions. I do this by "chmod -R 777" but everytime I create a new image... 

Is there any way of getting new files into this particular Dir to gain the privilegies of the main directory?

Thanks in advance

/Philip

---

### Post by cdenley on 2009-04-07
[http://ubuntuforums.org/showthread.php?t=939377](http://ubuntuforums.org/showthread.php?t=939377)

---

### Post by philsson on 2009-04-07
> **cdenley said:**
> [http://ubuntuforums.org/showthread.php?t=939377](http://ubuntuforums.org/showthread.php?t=939377)

Thanks for the fast reply. I have some services running on the server now so I will try this tomorrow morning. ACL will not make any damage to my softraid I hope?

Copy of my new fstab with the new changes
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=2b3ba369-2f77-476b-be76-01450565e183 /               ext3    relatime**,acl**,errors=remount-ro 0       1
# /dev/md1
UUID=0c4dd6b7-ccbb-47e0-aaf3-6352c988e0ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by cdenley on 2009-04-07
Should work fine.

---

### Post by philsson on 2009-04-08
> **cdenley said:**
> Should work fine.

The machine booted just fine. Now I've tried also to create files from root account and edit / delete these from normal user through Samba network and it also works just fine. Last to go now is the Image file. Thank you very mutch :-({|=

---

### Post by philsson on 2009-04-08
Permissions for created Images didn't work.. :(
Creating an image from clonezilla gave the files wrong permissions. Wonder why

Example of an created file

-rw-rw-r--+ 1 root partimag          4 2009-04-08 10:33 disk

Besides imageing wich was the main point the rules we just set upp worked perfectly.

Any idea of why CloneZilla denies read and write permissions for other users?
Only differens imaging now is that I have write permissions in the directorys and I can change directorys name but the files inside of them are protected.:-k


EDIT:
The users that should be able to edit everything in this DIR are members of "partimag" as group, the DIR's name is also "partimag"
Commands I've run

```
sudo chgrp partimag partimag
sudo chmod g+s partimag
sudo setfacl -d -m u::rwx,g::rx,o::rx,mask::rwx partimag
sudo setfacl -d -m g:partimag:rwx partimag
```

Maybe the problem lies with how the DRBL server saves the files, and that my further research should continue there. Or should these rules we made force the permissions of files created in this Dir?

---

### Post by cdenley on 2009-04-08
> **philsson said:**
> Permissions for created Images didn't work.. :(
Creating an image from clonezilla gave the files wrong permissions. Wonder why

Example of an created file

-rw-rw-r--+ 1 root partimag          4 2009-04-08 10:33 disk


What permissions were you hoping for?

---

### Post by philsson on 2009-04-08
> **cdenley said:**
> What permissions were you hoping for?

I was hoping for full permissions for all users of the group "partimag", but the files created by clonezilla doesn't even have read permissions for other users than root itself. Guess it will be a setting in CloneZilla to save the files with these permissions. Besides CloneZilla every file or directory I create gains full permissions by all users in that cataloge as I wanted it. Tried to google it up but it seems to be a minor problem wich I did not find mutch about. :(

Can I force permissions on new files in a certain Dir?
I'm really bad at this subject.

---

### Post by cdenley on 2009-04-08
> **philsson said:**
> I was hoping for full permissions for all users of the group "partimag", but the files created by clonezilla doesn't even have read permissions for other users than root itself. Guess it will be a setting in CloneZilla to save the files with these permissions. Besides CloneZilla every file or directory I create gains full permissions by all users in that cataloge as I wanted it. Tried to google it up but it seems to be a minor problem wich I did not find mutch about. :(

Can I force permissions on new files in a certain Dir?
I'm really bad at this subject.

The output you posted indicates the group "partimag" has read and write permissions for the file "disk". Isn't that what you wanted?
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I just noticed you are using samba to access files. I think it's a little easier to force permissions using samba. Did you configure your share in /etc/samba/smb.conf, or is it a usershare? Samba has it's own permissions, so your unix permissions may be correct but your samba permissions wrong.

---

### Post by philsson on 2009-04-09
> **cdenley said:**
> The output you posted indicates the group "partimag" has read and write permissions for the file "disk". Isn't that what you wanted?
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I just noticed you are using samba to access files. I think it's a little easier to force permissions using samba. Did you configure your share in /etc/samba/smb.conf, or is it a usershare? Samba has it's own permissions, so your unix permissions may be correct but your samba permissions wrong.


You were absolutely right. The file permissions say that I have read and write permissions for the owner and group. Still I can't read or write to these files. I checked the permissions of the directory the files lies in (that clonezilla creates) and it say's "drwxr-sr-x+", what does that say? I should have at least read permissions to files in that DIR? And what does the "s" stand for?... sorry for these lots of questions.

---

### Post by cdenley on 2009-04-09
> **philsson said:**
> You were absolutely right. The file permissions say that I have read and write permissions for the owner and group. Still I can't read or write to these files. I checked the permissions of the directory the files lies in (that clonezilla creates) and it say's "drwxr-sr-x+", what does that say? I should have at least read permissions to files in that DIR? And what does the "s" stand for?... sorry for these lots of questions.

```

drwxr-sr-x+

```
That means anyone can access/read the directory, but only the owner can create/delete files or directories in the folder. Also, since the set-group-ID bit is set, any files created in that directory will have the same group owner as it's parent directory.
```

man chmod

```

---

### Post by philsson on 2009-04-09
> **cdenley said:**
> ```

drwxr-sr-x+

```
That means anyone can access/read the directory, but only the owner can create/delete files or directories in the folder. Also, since the set-group-ID bit is set, any files created in that directory will have the same group owner as it's parent directory.
```

man chmod

```

That explains it very well, but why do CloneZilla create cataloges with these atributes? I think its something I would have to search more about. A configuration of the DRBL service.

Any other file or directory created by root account gains the attributes I wanted, wich are read and write to all users in group partimag.

---

