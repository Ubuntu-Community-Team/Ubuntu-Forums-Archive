---
title: "Permissions on new files in a folder"
date: 2010-10-06
forum: Security
---

### Post by K.Kong on 2010-10-06
How do I make all new files created in future in a folder to have Read permission for others?
 
I followed the instructions here: [http://library.gnome.org/users/user-guide/stable/nautilus-permissions.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-permissions.html.en), ie, in the folder Properties, Permissions tab, under the Others section I select Read-only for File access and then click Apply Permissions to Enclosed Files. This works only for the current files. I want all new files in that folder to have read access by everyone.
 
Another thing I note is that after I clicked Apply Permissions to Enclosed Files, the File access option automatically changed back to ---. What does this mean? 
 
Thanks.

---

### Post by mikewhatever on 2010-10-07
Is that a network folder (samba?) or a shared folder on the local hard disk? In both cases, what you are looking for in not the folder access rights, but something called the file creation mask. The default creation mask for Samba is, I think, 700 (rwx------), while the default creation mask for users is 755 (rwxr--r--).
Long story short, it's probably a samba folder, so look for default creation mask in /etc/samba/smb.conf, or change it per folder, also in /etc/samba/smb.conf.

---

### Post by bluefrog on 2010-10-07
your user do not have the right to change those permissions. hence the fact they are coming back (in fact never changed) to "normal".

you have to look either at the setbitGUID or acl to obtain what you want.

---

### Post by K.Kong on 2010-10-07
Thanks for all the responses.
 
The folders I am interested in sharing are /var/spool/asterisk/monitor and /var/logs/asterisk/cdr-csv.  Aren't these file system folders?
 
Anyway, I have Samba installed and I have made these two folders available readonly to guests.  My purpose is that other PCs on the LAN can read files in these two folders easily. 
 
Right now, when asterisk (a PBX software) creates the logs and recording files, they are -rwx-------.  I have to log in and manually do a chmod every time I need to access the files from another PC.
 
I would think such a requirement is something users need to do all the time.  So, what's the easiest solution?  
 
Thanks

---

### Post by K.Kong on 2010-10-15
Any help out there?  Thanks.

---

### Post by AlphaLexman on 2010-10-15
Have you tried changing the permissions of the parent folder to 'rw'?

---

### Post by endotherm on 2010-10-15
one thing to try, is to put everyone in a group (mabey users?)
then change the owner-group for the folder that you want them to access so it looks like 
<your user>:users

```
sudo chown <your user>:users <pathtodir>
```then set GID on the folder, so that all new files are owned by <owner>:users
```
sudo chmod u+s <pathtodir>
```then just make sure your permissions allow write to the group
```
sudo chmod -R ug+r <pathtodir>
```

---

### Post by bodhi.zazen on 2010-10-15
> **K.Kong said:**
> How do I make all new files created in future in a folder to have Read permission for others?
 
I followed the instructions here: [http://library.gnome.org/users/user-guide/stable/nautilus-permissions.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-permissions.html.en), ie, in the folder Properties, Permissions tab, under the Others section I select Read-only for File access and then click Apply Permissions to Enclosed Files. This works only for the current files. I want all new files in that folder to have read access by everyone.
 
Another thing I note is that after I clicked Apply Permissions to Enclosed Files, the File access option automatically changed back to ---. What does this mean? 
 
Thanks.

This is a bit of an old thread, but I think you will want to set a umask.

umask governs the permissions of files you create.

[http://linuxzoo.net/page/sec_umask.html](http://linuxzoo.net/page/sec_umask.html)

This will only work on Linux native file systems. You set ownership and permissions on FAT and NTFS partitions at the time you mount and they can not be changed.

Network shares also vary by protocol (samba, nfs, etc) and server (OS) and file system (as with FAT and ntfs above).

---

### Post by K.Kong on 2010-10-16
Thanks.  I read [[COLOR=#000000]http://linuxzoo.net/page/sec_umask.html[/COLOR]]("http://linuxzoo.net/page/sec_umask.html") and have the following questions:
 
a. Is umask a system-wide setting?  What I want for those two folders is 022.  If I run umask 022, does it mean that all files in every folder in the system from now on will be -rw-r--r--?
 
b. The article also says umask works only for the session in which it is set.  My PBX software, asterisk, presumably runs with the asterisk account.  So does it mean I have to set it in the login profile of the asterisk account too?

---

### Post by bodhi.zazen on 2010-10-16
> **K.Kong said:**
> Thanks.  I read [[COLOR=#000000]http://linuxzoo.net/page/sec_umask.html[/COLOR]]("http://linuxzoo.net/page/sec_umask.html") and have the following questions:
 
a. Is umask a system-wide setting?  What I want for those two folders is 022.  If I run umask 022, does it mean that all files in every folder in the system from now on will be -rw-r--r--?
 
b. The article also says umask works only for the session in which it is set.  My PBX software, asterisk, presumably runs with the asterisk account.  So does it mean I have to set it in the login profile of the asterisk account too?

umask will affect any file or directory you create.

You can set a umask value per user (in ~/.bashrc) or system wide. 

If you want to change this behavior for a single file or directory (group of files) IMO it is easiest to do so via a cron task.

[http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)

---

### Post by K.Kong on 2010-10-16
Thanks.
 
The /home/asterisk/.profile already had #umask 022.  So I simply uncommented it.  Rebooted the computer.  But new recording files created by (presumably) asterisk in the following **monitor** folder in /var/spool/asterisk:
 
drwxrwxr-x 2 asterisk asterisk 65536 2010-10-16 21:22 **monitor**
 
still are -rw-------
 
**fdisk -l** on my computer is as follows if it is any helpful:
 
Disk /dev/sda: 34.4GB, 34359738368 bytes
255 heads, 63 sectors/track,  4177 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x000554bd
 
   Device Boot      Start      End      Blocks  Id System
/dev/sda1   *             1    4000  32125952 83 Linux
/dev/sda2            4000     4178   1425409   5 Extended
/dev/sda5            4000     4178   1425408 82 Linu swap / Solaris

---

### Post by Morbius1 on 2010-10-16
> I want all new files in that folder to have read access by everyone.> Anyway, I have Samba installed and I have made these two folders  available readonly to guests.  My purpose is that other PCs on the LAN  can read files in these two folders easily. > But new recording files created by (presumably) asterisk in the following monitor folder in /var/spool/asterisk:
 
drwxrwxr-x 2 asterisk asterisk 65536 2010-10-16 21:22 monitor
 
still are -rw-------The question I have for you is who owns the files within /var/spool/asterisk/monitor?

If it's asterisk then there may be a samba way around this issue.

You create a guest share and then force every guest to be asterisk by using the "force user" option in the share definition.

For example. If you are using Classic-shares then a read only guest accessible share definition would look like this:

> [monitor]
path = /var/spool/asterisk/monitor
writeable = no
browseable = yes
guest ok = yes
[COLOR=Blue]force user = asterisk[/COLOR]When the remote guest user access the share his identity ( nobody ) will be converted to asterisk - at least for that share. "asterisk" may have r/w permissions on the directory itself but samba will prevent the remote user from doing anything other that read.

BTW, "force user" refers to the "UNIX user" not a samba user. SO it's the local user - there is no need to create a samba password for asterisk for this to work.

---

### Post by K.Kong on 2010-10-17
Morbius1, you are my savior!  
 
The option of forcing nobody to asterisk in the Samba share works!
 
Thank you very much.

---

