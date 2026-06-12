---
title: "fileserver backup question"
date: 2010-05-08
forum: Server Platforms
---

### Post by keevill on 2010-05-08
I have a samba file server on which a mix of Linux ( Ubuntu ) and WinX client machines save their data. I need to regularly make backups of the data preferably onto another hard disk or NAS. The data changes daily and increases by about 1 gb/month. Currently, it is about 40 GB. 
I would like to back up this automatically each evening preferably using the files' native format in order to expedite a fast recovery.
In other words, .xls files are backed up as .xls and .doc as .doc rather than some compression proprietary format which will require another program to facilitate a recovery.
If possible, the ability to back up open files would be handy but not essential.
Can anyone suggest a simple way to put this in place for daily nightly backup?
Thx,
-keevill-

---

### Post by HermanAB on 2010-05-08
Howdy,

Rsync is your friend.  Read the man page- it is a one liner and there are examples in the man page.  Once you figured it out, you turn your one liner into a two line bash script and plonk it in /etc/cron.daily, then make it executable.

However, if you would rather want a hugely complicated script to do the same thing, google for 'rbackup' and 'dervish'.

---

### Post by keevill on 2010-05-08
> **HermanAB said:**
> Howdy,

Rsync is your friend.  Read the man page- it is a one liner and there are examples in the man page.  Once you figured it out, you turn your one liner into a two line bash script and plonk it in /etc/cron.daily, then make it executable
Thanks for this. 1 further simple question.
 Would it be possible to initiate the backup from another ubuntu workstation?
What I mean is this: the fileserver has no monitor and resides in a server room. It would be more convenient for me to setup the backup going from say , my own machine,
Then it would mean me setting the directories on the file server to be backed up and the remote destination on the NAS from my own desk. 
Similarly, I could check the completeness of the backup from my own desk machine.
-keevill-

---

### Post by HermanAB on 2010-05-09
Install the ssh-server package, then from wherever you are:
$ ssh user@serveripaddress

or
$ ssh -C -c blowfish -X user@server gnome-panel
and go click happy.

---

### Post by keevill on 2010-05-09
But how do I install SSH server onto a NAS box ?
Not absolutely necessary to back up to a NAS but sort of convenient as I have one knocking around.
-keevill-

---

### Post by dipeshmehta on 2010-05-09
You may mount NAS share into your linux and use rsync for backup.  

You may check [http://www.howtoforge.com/forums/showthread.php?t=41609](http://www.howtoforge.com/forums/showthread.php?t=41609) This script works almost out of the box.  Its not exactly as you need but it should work for you. Its backups are tar. You need to untar while restoring, but I think it should not be problem.

Dipesh

---

### Post by keevill on 2010-05-10
> **dipeshmehta said:**
> You may mount NAS share into your linux and use rsync for backup.  

Dipesh


I have mounted the NAS from a Linux client and can browse etc. However when I attempt to use rsync or Grysnc ( the GUI version ) the mounted NAS is not available to select as a destination for the backup.
-keevill-

---

### Post by dipeshmehta on 2010-05-10
> **keevill said:**
> I have mounted the NAS from a Linux client and can browse etc. However when I attempt to use rsync or Grysnc ( the GUI version ) the mounted NAS is not available to select as a destination for the backup.
-keevill-

It should work simply:
```
rsync /sourcefolder/* /nas-mount
```

Dipesh

---

### Post by keevill on 2010-05-10
> **dipeshmehta said:**
> It should work simply:
```
rsync /sourcefolder/* /nas-mount
```

Dipesh
If I try that command where I attempt to backup my laptop's home folder to the 'public' folder on the NAS I get this.

rsync /home/david/* /smb://david@192.168.0.10/public/


davidvaio@davidvaio-laptop:~$ rsync /home/david/* /smb://david@192.168.0.10/public/
skipping directory Desktop
skipping directory Documents
skipping directory Downloads
skipping directory Music
skipping directory Pictures
skipping directory Public
skipping directory Templates
skipping directory Videos
rsync: mkdir "/smb://david@192.168.0.10/public" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.6]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.6]

-keevill-

---

### Post by dipeshmehta on 2010-05-10
> **keevill said:**
> If I try that command where I attempt to backup my laptop's home folder to the 'public' folder on the NAS I get this.

rsync /home/david/* /smb://david@192.168.0.10/public/


Instead, you may mount NAS volume like this:
```
mount -t cifs //192.168.0.10/public /localmountpoint -o username=david,password=secret

```

then run
```
rsync /home/david/* /localmountpoint
```

Dipesh

---

### Post by keevill on 2010-05-10
> **dipeshmehta said:**
> Instead, you may mount NAS volume like this:
```
mount -t cifs //192.168.0.10/public /localmountpoint -o username=david,password=secret

```

then run
```
rsync /home/david/* /localmountpoint
```

Dipesh

Thx for your continued help.

sudo mount -t cifs //192.168.0.10/public /localmountpoint -o username=david,password=***** then I get this error.
mount error: can not change directory into mount target /localmountpoint

---

### Post by dipeshmehta on 2010-05-10
> **keevill said:**
> Thx for your continued help.

sudo mount -t cifs //192.168.0.10/public /localmountpoint -o username=david,password=***** then I get this error.
mount error: can not change directory into mount target /localmountpoint

You need to replace *localmountpoint* to the directory name where you want to mount your NAS volume.

For example: i> create a directory named *backupdisk* on root of your file system
ii> mount with command *sudo mount -t cifs //192.168.0.10/public /backupdisk -o username=david,password=******
iii> backup your files with *rsync /home/david/* /backupdisk*

---

### Post by keevill on 2010-05-10
> **dipeshmehta said:**
> You need to replace *localmountpoint* to the directory name where you want to mount your NAS volume.

For example: i> create a directory named *backupdisk* on root of your file system
ii> mount with command *sudo mount -t cifs //192.168.0.10/public /backupdisk -o username=david,password=******
iii> backup your files with *rsync /home/david/* /backupdisk*

I am sorry to be so stupid but I have made a directory on the NAS in the Public folder called 'backup' 
I then issue  the command with the ensuing error.
What am I doing wrong here ???

sudo mount -t cifs //192.168.0.10/public /backup -o username=david,password=******
[sudo] password for davidvaio: 
mount error: can not change directory into mount target /backup

---

### Post by dipeshmehta on 2010-05-10
> **keevill said:**
> ...I have made a directory on the NAS in the Public folder called 'backup'...

You need to create folder named backup in your linux file system, not on NAS

---

### Post by keevill on 2010-05-10
> **dipeshmehta said:**
> You need to create folder named backup in your linux file system, not on NAS

Where ? I tried 'media/data/backup' but got a the command help dialogue. 
You mean make a folder on the local linux machine called 'backup' and then try to load it via that command ?
-keevill-

---

### Post by dipeshmehta on 2010-05-15
Sorry, I was out of town for couple of days, and couldn't check your last post.

Please inform about latest situation, it is done? 

Dipesh

---

### Post by keevill on 2010-05-20
> **dipeshmehta said:**
> Sorry, I was out of town for couple of days, and couldn't check your last post.

Please inform about latest situation, it is done? 

Dipesh

Hi,
I too was away for a few days = sorry but I am still at the same point as I posted just above. Need a final pointer or two to get this to work.
Thx,
-keevill-

---

### Post by Roadfighter on 2010-05-24
[COLOR=Blue]Hello,

I also was looking for a way to backup files to my Synology Diskstation, and i stubled on to this thread. And i followed the steps by [B][COLOR=Black]dipeshmehta.[/COLOR]
[/B]And it didn't work for me to. So i Googled some more and found an other[/COLOR][COLOR=Blue][COLOR=Red]***_[forum link]("http://ubuntuforums.org/showthread.php?t=288534")_*** [/COLOR]and i followed these instructions and then the cifs command works.
I hope it helps.[/COLOR]

---

### Post by jerome1232 on 2010-05-24
If you mounted the share using gnomes gui it will be mounted somewhere under ~/.gvfs, so check there, you can rsync to the folder under .gvfs that corresponds to your share.


If that nas uses microsoft filesystems then you can't simply rsync to it if the permissions on the files need to be preserved, your going to have to tar them before they hit the MS Filesystem IF you want the permissions preserved.

edit: Blue text makes me blind, I glanced over that and didnt' realize you were saying that you had found an answer. Glad you got it working.

---

