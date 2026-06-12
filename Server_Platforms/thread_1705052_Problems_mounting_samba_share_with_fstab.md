---
title: "Problems mounting samba share with fstab"
date: 2011-03-11
forum: Server Platforms
---

### Post by rodney757 on 2011-03-11
I am trying to set it up so that my samba share is automatically mounted when I log in.

I added this to my /etc/fstab:

```
//192.168.1.2/media /home/rj/Server/media cifs credentials=/root/smb/credentials,rw,iocharset=utf8,uid=1000,gid=1000 0 0


```

When I type :

```
sudo mount -a
```

I get :

```
wrong fs type, bad option, bad superblock on //192.168.1.2/media,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg | tail gives me :

```
[ 1603.542098] CIFS VFS: No username specified
[ 1603.542113] CIFS VFS: cifs_mount failed w/return code = -22

```

my /root/smb/credentials file looks like :

```
username=(myusername)
password=(mypassword)
```

Where (myusername) and (mypassword) are my actual username and password

However if I replace the credentials=/root/smb/credentials line in /etc/fstab with username=(myusername),password=(mypassword) it will mount the share. So something with the /root/smb/credentials file isn't right.

Thanks for the help.

---

### Post by rodney757 on 2011-03-12
Anyone know how I can go about fixing this? Thanks

---

### Post by rodney757 on 2011-03-13
Has anyone had this problem before?

---

### Post by volkswagner on 2011-03-13
Well I have been wanting to do this..

I'm gonna work through it with you to see if we get any differences.

I noticed some how to's use .credentials for file name..... are you missing the "." for file name?

What are the permissions for /root/smb/credentials?

Most how to's put the .credentials directly in /root... any reason why you added the sub directory smb?

Do you have your domain/workgroup listed in the credentials file?

According to man page credentials can be listed like..
```
username=value
      password=value
      domain=value

```

are we running same version?
```
mount.cifs -V
mount.cifs version: 1.12-3.4.7
```



EDIT; I had no problem using this setup "credentials=/root/smb/credentials", with the file formatted like above.

---

### Post by rodney757 on 2011-03-14
> **volkswagner said:**
> Well I have been wanting to do this..

I'm gonna work through it with you to see if we get any differences.

I noticed some how to's use .credentials for file name..... are you missing the "." for file name?

What are the permissions for /root/smb/credentials?

Most how to's put the .credentials directly in /root... any reason why you added the sub directory smb?

Do you have your domain/workgroup listed in the credentials file?

According to man page credentials can be listed like..
```
username=value
      password=value
      domain=value

```

are we running same version?
```
mount.cifs -V
mount.cifs version: 1.12-3.4.7
```



EDIT; I had no problem using this setup "credentials=/root/smb/credentials", with the file formatted like above.

I tried checking *mount.cifs -V* and it wasn't installed. I installed it and now it will mount using *credentials=* in the */etc/fstab* file.

I actually have my credentials file in */root/smb/credentials* now. The reason it was there was because I was testing to see if it would work if it were in my home folder, since it wasn't working in the */root/smb/* dir.

Its interesting that everything would mount fine before installing *mount.cifs* if I replaced: 

```
credential=/path/to/credentials_file
``` 

in */etc/fstab* with: 

```
username=<username>,password=<password>
```. 

I guess *mount.cifs* has to do with using a credentials file?

Anyway's thanks for the help.

---

### Post by eyekode on 2011-07-30
Thanks for posting this. I was having the same problem and this fixed it as well. Not sure why cifs-utils is not automatically bundled with the rest of the cifs support.

---

### Post by ottabaub on 2011-09-13
I had the same problem with the same error. I found that even if you have Samba installed you need to install smbfs.

sudo apt-get install smbfs

That did the trick. No more errors on *sudo mount -a* and my drive is mounted.

This is a very good document:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by bayvista on 2012-12-07
Thanks for that. I can now mount my Samba share in Ubuntu. However I cannot write to it?? Any ideas?

---

### Post by volkswagner on 2012-12-07
> **bayvista said:**
> Thanks for that. I can now mount my Samba share in Ubuntu. However I cannot write to it?? Any ideas?


Did you copy the mount command from the original post?  Perhaps your userID is not the same.  If you are not the first installed user, you wont have uid=1000 as in the OP.

```
uid=1000,gid=1000
```

You can find your UID from /etc/group

```
cat /etc/group | grep yourusername:
```

Where is the share located, on a windows machine or a Linux box?

What are the permissions and the owner:group for the share?

```
ls -l /share/mountoint
```

---

### Post by bayvista on 2012-12-09
Thanks for your prompt reply. My Windows machine is a WD MyBookWorld NAS storage. I can talk to it from a Windows PC running their proprietary software called  WD Discovery. I have installed it on my home network and can attach it to my 2 Ubuntu PCs using both Places/Network and fstab. I can read and write to the 'Shared' folders and have successfully used rsync to copy folders from both PCs.

I have always used rsync for backup and want to continue doing this. I can rsync my home folder OK but cannot rsync my wife's home folder. She is user 'pam'. I have tried using Webmin to setup a shared 'backups' folder. This works OK but only I can access it. When I try to copy her folders, I get 'Error while copying. You do not have permissions'

I tried following your notes. My UID is 1000, Pam's is 1001. Our GID is 1000. Confirmed by the cat command. Could not understand the 'ls' command. If the share is called 'Shared Pictures' and it is mounted on /media/hp-nas, surely the command is "ls -l  /media/hp-nas/'Shared Pictures'?". This works fine. I have pasted the output fo your comments.

drwxrwxrwx  5 99 david     0 Mar  7  2012 acting
drwxr-xr-x  3 99 david     0 Dec  5 17:00 Albert
drwx------  3 99 david     0 Dec  5 17:05 Books
drwx------  2 99 david     0 Dec  9 16:37 Concord houses
drwx------  4 99 david     0 Dec  5 16:53 Condoblin
drwx------  2 99 david     0 Dec  9 16:52 council
drwxrwxrwx  3 99 david     0 May  7  2009 davids 60th
drwx------  5 99 david     0 Dec  5 16:39 dilys
drwx------  3 99 david     0 Feb 22  2011 Downloaded Albums
drwxrwxrwx  8 99 david     0 Dec  9 16:38 Family Days
drwx------ 33 99 david     0 Dec  5 17:17 Family History - Pam
drwx------  2 99 david     0 Oct  4  2011 For filing
drwx------  3 99 david     0 Dec  5 16:52 Groups
drwxrwxrwx 11 99 david     0 Dec  5 17:24 Holidays & Outings
drwxr-xr-x  3 99 david     0 Jul 13  2011 Important Documents
drwxrwxrwx  4 99 david     0 Mar  7  2012 Norman St
drwx------  2 99 david     0 Mar  7  2012 Pam's 70th
drwx------ 21 99 david     0 Aug 28 16:12 Picasa Exports
-rwx------  1 99 david 18569 Feb 12  2010 Picasa.ini
drwx------  5 99 david     0 Dec  5 17:21 Scrolls and Bushcare
drwxrwxrwx  3 99 david     0 Mar  7  2012 Wildlife
david@hp-desktop ~ $
 

Many thanks. I'll keep plugging away.

---

### Post by volkswagner on 2012-12-09
> **bayvista said:**
> ...My Windows machine is a WD MyBookWorld NAS storage. I can talk to it from a Windows PC running their proprietary software called  WD Discovery. I have installed it on my home network and can attach it to my 2 Ubuntu PCs using both Places/Network and fstab. I can read and write to the 'Shared' folders and have successfully used rsync to copy folders from both PCs. 
Does the MyBook allow you to setup users and passwords along with groups?


> **bayvista said:**
> I have always used rsync for backup and want to continue doing this. I can rsync my home folder OK but cannot rsync my wife's home folder. She is user 'pam'. I have tried using Webmin to setup a shared 'backups' folder. This works OK but only I can access it. When I try to copy her folders, I get 'Error while copying. You do not have permissions'  

Please explain how you are accessing the MyBook.  Do you and your wife have separate machines?  Are you using a separate mount command for each user?  Whey you try to copy pam's files, are you doing this while logged in as pam?

What machine are you administering using Webmin?  Are you running SAMBA on a second machine and mounting your MyBook/NAS to that?  Sorry, I'm just very confused on your setup.

> **bayvista said:**
> I tried following your notes. My UID is 1000, Pam's is 1001. Our GID is 1000. Confirmed by the cat command. Could not understand the 'ls' command. If the share is called 'Shared Pictures' and it is mounted on /media/hp-nas, surely the command is "ls -l  /media/hp-nas/'Shared Pictures'?". This works fine. I have pasted the output fo your comments.  
So pam is a member of the david group?
I should have given you the command:
```
ls -al
```

The -a will show the permissions for the parent folder which would help here.
Those permissions look a little funky to me.  What I see is all files and directories are owned by user=99 and have group=david.  The majority also only have rwx permissions for user 99.

I'm not sure if the user=99 is coming from the NAS or if it is due to how you mounted it or something else.

---

### Post by bayvista on 2012-12-10
> **volkswagner said:**
> Does the MyBook allow you to setup users and passwords along with groups? [COLOR="Blue"]Yes[/COLOR]

Please explain how you are accessing the MyBook.  Do you and your wife have separate machines? [COLOR="Blue"]Yes [/COLOR] 

Are you using a separate mount command for each user?  [COLOR="Blue"]No. I have one entry in fstab on both machines . This is:

//hp-nas/backups /media/hp-nas-backups cifs iocharset=utf8,credentials=/home/david/smbpw.txt,gid=1000 0  0[/COLOR]

Whey you try to copy pam's files, are you doing this while logged in as pam? [COLOR="Blue"]Yes[/COLOR]

What machine are you administering using Webmin? [COLOR="Blue"]I use Webmin on my PC. I'm not sure but think that it will administer the NAS using Samba Shares.[/COLOR]

 Are you running SAMBA on a second machine and mounting your MyBook/NAS to that? [COLOR="Blue"]Yes. The NAS is mounted on my PC and Pam's PC through fstab.[/COLOR] Sorry, I'm just very confused on your setup.


So pam is a member of the david group?  [COLOR="Blue"]Yes[/COLOR]
I should have given you the command:
```
ls -al
```

The -a will show the permissions for the parent folder which would help here.
Those permissions look a little funky to me.  What I see is all files and directories are owned by user=99 and have group=david.  The majority also only have rwx permissions for user 99.

I'm not sure if the user=99 is coming from the NAS or if it is due to how you mounted it or something else.

[COLOR="Blue"]Here is the ls command for the folder causing problems. I can write to this, bur Pam cannot.

david@hp-desktop ~ $ ls -al /media/hp-nas/backups
total 0
drwxr-xr-x  3   99 david 0 Dec 10 19:08 .
drwxrwxr-x  9 root david 0 Dec  9 17:47 ..
drwxr-xr-x 57   99 david 0 Dec  9 16:13 david
david@hp-desktop ~ $ 
[/COLOR]

Many thanks

---

### Post by volkswagner on 2012-12-10
According to the permissions on /media/hp-nas/backups, david does not even have permission to write.  It seems your user or david is part of the 99.  You need to get pam added to 99 as well.

---

