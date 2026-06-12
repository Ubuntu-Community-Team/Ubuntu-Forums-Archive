---
title: "How to copy files from Ubuntu Share to Windows 2003 share"
date: 2009-08-05
forum: Server Platforms
---

### Post by malarie on 2009-08-05
(sorry for my english, its not my main language)

Good day,


Domain : Windows 2003
Backup tool used for backups on Win2003: Symantec BackupExec 10.d SP3

I am running Ubuntu server 8.04 Hardy (no UI), as a  samba, svn, cvs, nuxeo and also as a backup server for my 3 dev linux (ubuntu) machines.

I have 3 clients that are backedup to up my Ubuntu server using a cronjob with rsync everynight.  I just found out that backupexec does not support debian based distributions, only red-hat. The Remote Backup Agents for Linux are rpms based. So i cant install the agents, and it will never be supported according to Symantec.

So now, my option is to be able to send those backup files to a Windows Share. I dont want to do this manually. I want to create a script that will copy the files over. I can use Samba, but i do not know the commands at all and im not familiar with samba.

So i guess my question is this:
Can i use samba in command line to send those files to a win2003 server? I need the process to be automatic via a cronjob, so  no propmpt for usernames and or passwords.

Thanks.

P.S: Time to RTFM as well.

---

### Post by Cheesemill on 2009-08-05
I do this at work by mounting the Windows share onto the local filesystem.
First you need the smbfs package installed:
```

sudo apt-get install smbfs

```
 
Then create the mount point:
```

sudo mkdir /mnt/winshare

```
 
Then we add the following line to the /etc/fstab file (changing //winserver/share to suite your setup):
```

//winserver/share    /mnt/winshare    cifs    exec,credentials=/etc/cifspw    0    0

```
 
Now create the password file we referenced in fstab and add the following text (substituting user and pass for the Windows credentials you're using):
```
 
username=user
password=pass

```
 
Then just set the permissions on the password file and mount the share:
```
 
sudo chmod 600 /etc/cifspw
sudo mount -a

```
 
You should be all done :)
 
You can now use any method you wish (cp, rsync etc) to copy files from the local machine to the windows share which you'll now find at /mnt/winshare

---

### Post by malarie on 2009-08-06
> **Cheesemill said:**
> I do this at work by mounting the Windows share onto the local filesystem.
First you need the smbfs package installed:
```

sudo apt-get install smbfs

```
 
Then create the mount point:
```

sudo mkdir /mnt/winshare

```
 
Then we add the following line to the /etc/fstab file (changing //winserver/share to suite your setup):
```

//winserver/share    /mnt/winshare    cifs    exec,credentials=/etc/cifspw    0    0

```
 
Now create the password file we referenced in fstab and add the following text (substituting user and pass for the Windows credentials you're using):
```
 
username=user
password=pass

```
 
Then just set the permissions on the password file and mount the share:
```
 
sudo chmod 600 /etc/cifspw
sudo mount -a

```
 
You should be all done :)
 
You can now use any method you wish (cp, rsync etc) to copy files from the local machine to the windows share which you'll now find at /mnt/winshare

<3

It worked wioth XP.

But now i am trying to make it work with Vista and it does not seem to be working.

Here is what i have in my fstab:
//192.168.10.62/Shared /mnt/windows/Penang/Shared  cifs exec,credentials=/etc/cifspw 0 0

when doing a mount -a,  nothing happens.  My Vista Firwall is disabled.

When i CTRL+C, i have the following message:

CIFS VFS: cifs_mount failed w/return code = -512

---

