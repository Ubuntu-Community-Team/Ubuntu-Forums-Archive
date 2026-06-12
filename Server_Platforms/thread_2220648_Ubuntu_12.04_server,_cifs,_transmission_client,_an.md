---
title: "Ubuntu 12.04 server, cifs, transmission client, and windows NTFS shares"
date: 2014-04-28
forum: Server Platforms
---

### Post by at50bba on 2014-04-28
I have an Ubuntu 12.04 server running plex media server and would like to be able to use transmission torrent client on this headless server via browser from another PC. My plex server accesses shares from a Windows server (domain and NTFS) using cifs, with an entry in fstab. I followed the instructions [here]("https://help.ubuntu.com/community/Samba/SambaClientGuide#Connecting_using_CIFS") about samba and cifs to make that work and it has been working fine. My problem is basically that the shares are read only and I need to be able to write to this share. I have tried numerous permission changes. My path is mounted as /media/mediashare. 

The transmission page loads, and I've been using an Ubuntu 14.04 server torrent file as my test torrent. I get permission denied./media/mediashare/transmission errors 

Would someone have a suggestion for me that I can try? I can post any additional information needed.

Thanks.

---

### Post by bab1 on 2014-04-29
> **at50bba said:**
> I have an Ubuntu 12.04 server running plex media server and would like to be able to use transmission torrent client on this headless server via browser from another PC. My plex server accesses shares from a Windows server (domain and NTFS) using cifs, with an entry in fstab. I followed the instructions [here]("https://help.ubuntu.com/community/Samba/SambaClientGuide#Connecting_using_CIFS") about samba and cifs to make that work and it has been working fine. My problem is basically that the shares are read only and I need to be able to write to this share. I have tried numerous permission changes. My path is mounted as /media/mediashare. 

The transmission page loads, and I've been using an Ubuntu 14.04 server torrent file as my test torrent. I get permission denied./media/mediashare/transmission errors 

Would someone have a suggestion for me that I can try? I can post any additional information needed.

Thanks.
You can't change ownership and permissions using the command line.  The ownership and permissions are set at mount time on NTFS formatted partitions.  

Post the output of ```
cat /etc/fstab
```

---

### Post by at50bba on 2014-04-30
Thanks!

Here is cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8daf8629-edf0-4964-8f03-f93436874eb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a87e8f46-d9cd-4c8e-81ed-93f5b0b369a9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


#windows server share for media
//192.168.1.10/media  /media/mediashare  cifs credentials=/etc/samba/user,iocharset=utf8, 0 0

---

### Post by bab1 on 2014-05-01
> **at50bba said:**
> 
#windows server share for media
//192.168.1.10/media  /media/mediashare  cifs credentials=/etc/samba/user,iocharset=utf8, 0 0

I would add ```
file_mode=0664,dir_mode=07*&#8203;75
```

Is this for all your users?```
credentials=/etc/samba/user
```
You haven't set the user with something like```
uid=1000,gid=1000
```

All of the options are available at```
man mount.cifs
```

---

### Post by at50bba on 2014-05-05
Thanks bab1 for your help, sorry it takes me a few days to reply. This is just a home project in my free time.

The samba/users file does have my plexserver's username in it, I was thinking maybe I needed to add transmission's default user to it also? Or what would be the best way for me to accomplish both the plex server (read) and the transmission (read, write, create) capabilities? 

From your info above, I think you're suggesting I change my line to this:

[COLOR=#000000]*//192.168.1.10/media /media/mediashare cifs credentials=/etc/samba/user,iocharset=utf8,*[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]file_mode=0664,dir_mode=07*&#8203;75[/FONT][/COLOR][COLOR=#000000][I], 0 0
[/I][/COLOR]
Would that be correct?

---

### Post by bab1 on 2014-05-05
> **at50bba said:**
> Thanks bab1 for your help, sorry it takes me a few days to reply. This is just a home project in my free time.

The samba/users file does have my plexserver's username in it, I was thinking maybe I needed to add transmission's default user to it also? Or what would be the best way for me to accomplish both the plex server (read) and the transmission (read, write, create) capabilities? 

From your info above, I think you're suggesting I change my line to this:```


//192.168.1.10/media /media/mediashare cifs credentials=/etc/samba/user,iocharset=utf8,file_mode=0664,dir_mode=07&#8203;75  0  0 
```
Would that be correct?
There were several typos so look carefully at it now in this reply.  If you use this you will find that the owner will be root.  This is because you have not stated the ownership.  The credentials are for used for Samba authentication, not for file and directory ownership or creation.  If I was to add the ownership in it would be like this (note: UID/GID = 1000 is the user that installed Ubuntu)  
```
//192.168.1.10/media /media/mediashare cifs credentials=/etc/samba/user,iocharset=utf8,uid=1000,gid=1000,file_mode=0664,dir_mode=07&#8203;75  0   0 
```

In this manner you have explicitly declared:
[LIST]
[*]The Samba user creds are at: credentials=/etc/samba/user
[*]The character set is UTF-8
[*]The files are owned by user 1000 and the group 1000
[*]All new files will have 0664  permissions
[*]All new directories will have 0775 permissions
[*]No file system check 
[/LIST]


Add it to the fstab file and use this command to see if you can mount the share```
sudo mount -a
```

---

### Post by at50bba on 2014-05-09
Hi. I don't get much free time obviously, I appreciate your help!

So, now I can write files to the shares via with the user I created for the plexserver, the one listed in my /samba/users list. Now I think I just need to figure out the transmission user account, add it to the /samba/users file and I'll be good?

---

### Post by bab1 on 2014-05-09
> **at50bba said:**
> Hi. I don't get much free time obviously, I appreciate your help!

So, now I can write files to the shares via with the user I created for the plexserver, the one listed in my /samba/users list. Now I think I just need to figure out the transmission user account, add it to the /samba/users file and I'll be good?

So you want both users to be able to access the same files with read write (rw) permissions; right?  This is an Ubuntu file system issue rather than a Samba issue.  Either way there is a method for allowing multiple users access to a directory.

You need to use a common group that has ownership and rw permissions.  The change the group ownership and set the sgid bit so that any file in the /media/mediashare file system inherits the group ownership of the user group we use.

Is this what you want to do.  Are you documenting what we are doing so you can recreate this if needed?

---

