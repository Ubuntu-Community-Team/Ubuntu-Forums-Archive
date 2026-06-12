---
title: "Automatic incremental backup?"
date: 2007-10-24
forum: Server Platforms
---

### Post by hcker2000 on 2007-10-24
I found this thread 

[http://ubuntuforums.org/showthread.php?t=317630](http://ubuntuforums.org/showthread.php?t=317630)

I was wondering a few things.

1. is this only going to copy new and/or modified files?
2. if I uncomment the DO_DELETE it will remove files I have deleted when it backs up right?
3. Is there any way to add a check to this to see if a samba mount is mounted and if not try and mount it?

---

### Post by Gen2ly on 2007-10-24
> **hcker2000 said:**
> I found this thread 

[http://ubuntuforums.org/showthread.php?t=317630](http://ubuntuforums.org/showthread.php?t=317630)

I was wondering a few things.

1. is this only going to copy new and/or modified files?

rsync will copy both the modified and the new files, this is the definition of incremental backups.

> 2. if I uncomment the DO_DELETE it will remove files I have deleted when it backs up right?

From what I gather this is for deleting the source files?  I never used it though.

> 3. Is there any way to add a check to this to see if a samba mount is mounted and if not try and mount it?

I know that Samba shares can be mounted just like any other drive, if you are wanting to backup anything other than your $HOME than this might be a better way to do it and put it in the exclude list.

Samba shares are put in a (virtual filesystem?) so this shouldn't be much of an issue anyhow.

---

### Post by hcker2000 on 2007-10-24
I am looking to backup my web site which is in /var/www/ and I need to back up the whole thing recursively but of course I only need to grab and back up changed/new files.

My file/backup server is a windows box. I have samba set to mount the windows share to /mnt/fileserver/ on start up.

What I was hoping to find out is if there is a way to check /mnt/fileserver/ to see if there are any files in it. If there are no files in it then the share didnt mount when I booted my linux box.

The only time it would not be mounted is if there is a network issue or if the windows box is off when I start the linux box.

In those situations where the script finds that /mnt/fileserver/ directory is empty I would like it to issue the command to mount the windows share.

Is that doable with out changing the script much?

---

### Post by NIT006.5 on 2007-10-24
Uncommenting DO_DELETE will add "--delete --delete-exlcuded" to the rsync command.

The --delete option will delete files in the destination directory IF they do NOT exist in the source directory. i.e. if they have been deleted from source, they will be deleted from the backup when rsync runs.

The --delete-excluded option will delete files in the destination directory IF they have been listed in your exclude file. i.e. the files will be excluded by the --exclude-from option, but if they ALREADY existed in the destination directory, the --delete-excluded option will remove them. 

Hope that helps.

---

### Post by NIT006.5 on 2007-10-24
By default, rsync will only transfer the new/changed files (and only the "parts" of changed files that have actually changed, not even the entire file, which is why it's so efficient and faster than a straight copy).

I'm not sure how to "check" if the share is mounted or not from the script, but you could safely add the command

*mount -a -t smbfs*

at the start of the script. This would mount all samba shares specified in /etc/fstab. If they're mounted already, then it will have no effect, which is fine too.

---

### Post by hcker2000 on 2007-10-24
Thanks that does help.

Now I just need to find out about adding the if statement to determine if /mnt/fileserver/ is empty and if so mount /mnt/fileserver/ then do the backup.

Also does the file I put the script in need to be .sh or any thing?

---

### Post by NIT006.5 on 2007-10-24
As I said in the previous message, I personally wouldn't worry about any if statements to check - just tell it to mount all smbfs file systems as specified in fstab. If it's mounted already, there's no harm.

As far as I know, the actual file extension doesn't matter as long as the file is executable. I generally always use .sh extension for scripts though, just to be "neat and tidy". To make it executable, just do:

*chmod +x filename.sh*

---

### Post by hcker2000 on 2007-10-24
Thanks I will give it a go and see how it turns out.

---

### Post by hcker2000 on 2007-10-24
Wait I just noticed some thing. There is no way to specify the destination directory. I am guessing it uses the current directory as the destination?

Is there any way to point it to /mnt/fileserver/ ?

---

### Post by NIT006.5 on 2007-10-24
> **hcker2000 said:**
> Wait I just noticed some thing. There is no way to specify the destination directory. I am guessing it uses the current directory as the destination?

Is there any way to point it to /mnt/fileserver/ ?

It is actually specifying the destination direction as the current directory. i.e. the "." period in this part of the script:

$SRC . > $LOG

You would just edit this to

$SRC /mnt/fileserver/ > $LOG

Or if you really wanted to, you could define another variable such as:

DEST=/mnt/fileserver/ (put this at the top of the script where SRC is defined)

Then change that line to:

$SRC $DEST > $LOG

**Note:** Be careful of trailing slashes on source and destination because they DO make a difference. I can't remember for sure, but I think it works something like this:

for example, if you specify /home as the source (no trailing slash) I'm pretty sure it will copy the directory itself, so you would end up with /mnt/fileserver/home containing what's copied.

If on the other hand, you specified /home/ WITH the trailing slash, I think it would copy the files contained in /home but not the actual directory. I'm not 100% sure on that, but you will soon see one way or another. 

Good luck.

---

### Post by hcker2000 on 2007-10-24
yea now I am trying to figure out how you can assign a directory with spaces in it to a variable.

I tryed

TEST=`/home/me/test this/`
TEST=/home/me/test\ this/
TEST="/home/me/test this/"

None of those work in the script.

---

### Post by NIT006.5 on 2007-10-24
1. Using /home/me/test\ this/ won't assign the value to the variable correctly because of the space. So it probably ends up looking for /home/me/test\

2. Generally, you can assign *variables* with spaces, using double quotes. However, when you're trying that, it's working in the variable itself BUT when the command runs, there are no quotes and you end up with a space in the file path of the command. i.e. /home/me/test this/

I would suggest trying a combination therefore:

TEST="/home/me/test\ this/"

so that the path passed to the command is actually **/home/me/test\ this/**

I think that should work.

---

### Post by hcker2000 on 2007-10-24
Here is the working code just in case any one else needs it.

```

#!/bin/sh

EXCLUDES=exclude.list
touch $EXCLUDES

SRC=/var/www/
DST="/mnt/hcker2000t2/BackUp/Web Site/10-24-07/"
DT=`date`
LOG=/tmp/backup.${DT}.log
# -- Uncomment this line when you know what you do - 
# This will delete the files you've been delete on the source as well.
DO_DELETE="--delete --delete-excluded"

echo "Starting backup of $SRC at $DT. "
rsync -Cav $DO_DELETE             \
      --exclude-from="$EXCLUDES"  \
      $SRC "$DST" > $LOG
DT=`date`
echo "Done at $DT"

```

---

### Post by NIT006.5 on 2007-10-25
Glad you got it sorted. Never thought of putting the variable name in quotes - that does make it simpler. Well done :)

---

