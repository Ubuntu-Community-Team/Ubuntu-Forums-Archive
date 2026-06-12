---
title: "rsync not found"
date: 2008-11-03
forum: Server Platforms
---

### Post by cmittle on 2008-11-03
This is a script I have written to run rsync to backup all of the stuff on my server to another drive mounted in the same computer.
```
#!/bin/sh
progname=${0##*/}
toppid=$$
#above used to grab the name of the script and associated
#process id



#Folders to exclude
EXCLUDES=/media/200gdisk/rsync/exclude.txt
#Folders to include
INCLUDES=/media/200gdisk/rsync/include.txt


##Define backup path
PATH=/media/200gdisk/rsync/test



#####Rsync options to be used
#-n dry run
#-a archive; tells rsync to retain permissions and ownership and recursive
#-v verbose
#-z compress
#--progress tells user how many files are left to be copied
#--delete any files on the receiving side if they do not exist
	#on the sending side
#-t transfers modification timestamp with files
#--include-from=FILE points to include file; this is read as exception to excludes..maybe
#--exclude-from=FILE points to exclude file

OPTS="-nvazt --progress --delete --include-from=$INCLUDES --exclude-from=$EXCLUDES "

#Display statement
echo "Preparing to backup with..."

#Echo command that will run and sleep for 20 seconds
echo rsync $OPTS / $PATH
#sleep 20

#Run actual command
rsync $OPTS / $PATH

```


When I run this script I get the following;

```
Preparing to backup with...
rsync -nvazt --progress --delete --include-from=/media/200gdisk/rsync/include.txt --exclude-from=/media/200gdisk/rsync/exclude.txt / /media/200gdisk/rsync/test
/media/200gdisk/rsync/server_backup.sh: 42: rsync: not found
```

Can someone please help me determine what I am doing wrong here?

Thanks,
Cory

---

### Post by CrucifiedEgo on 2008-11-03
FWIW, rsync isn't in the base install on my 8.04.1 server.  Make sure that you have rsync installed and in your path somewhere:
```
which rsync
```
and if not, install it using apt.  If you're planning to cron it, make sure you're using the full path(from the which command above) when calling the executable.

---

### Post by beercz on 2008-11-03
you could also try

> locate rsync

---

### Post by CrucifiedEgo on 2008-11-03
that assumes that the locatedb is current (updatedb is the command to do that) -- although, it will find it if he's got a compiled version in, say, /opt that isn't in the path.

---

### Post by y@w on 2008-11-03
On my install it is located at /usr/bin/rsync.

You'll have to reference it absolutely. The script didn't run on my system until I put in the absolute path.



edit: Oops, read it wrong..

---

### Post by cmittle on 2008-11-03
I changed the script to reference it's absolute location /usr/bin/rsync and the dry run indicates that it worked.  I am quite suprised at the amount of files ~117,000 files according to what the dry run told me.  Maybe I'm not excluding enough directories.  Here are my exclude and include files.

Include
```
/var/
/home/
/usr/
/etc/

```
Exclude
```
/var/cache/
/var/tmp/
/bin/
/boot/
/cdrom/
/dev/
/initrd/
/initrd.img*
/lib/
/lost+found/
/media/
/mnt/
/opt/
/proc/
/root/
/sbin/
/srv/
/sys/
/tmp/
/vmlinuz*

```

Any suggestions?

Cory

---

### Post by Vegan on 2008-11-03
I tried rsync from my login directory, works for me, mind you I have Samba installed so that is likely how it came to be on the path.

---

### Post by MJN on 2008-11-04
> **cmittle said:**
> Any suggestions?Suggestions for what?
 
If the paths you want to backup happen to have 117,000 files in them then that's that!
 
Remember that after the first run rsync will only be required to backup files that have changed hence it is unlikely that it will need to redo all 117,000 every time.
 
Mathew

---

### Post by cmittle on 2008-11-04
Any suggestions on directories that I'm including that maybe I shouldn't be?

---

### Post by MJN on 2008-11-04
It's entirely up to you, but I think you've got the most important bases covered - logfiles and other variable data, user files and configuration.
 
I'm not sure if you'd need to backup /usr/ though.
 
All that said, are you short of space or something on your backup medium? I backup the entire drive (it takes ~6 minutes every night) then I have a near mirror-image of my entire system should the worst happen (and it did once!).
 
Mathew

---

### Post by cmittle on 2008-11-04
My backup disk is an entirely empty 200gig hard drive.  What backup program do you use?

---

### Post by MJN on 2008-11-04
Rsync!

---

