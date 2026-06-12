---
title: "Move All But 5 Newest Files When Filenames Have Sapces"
date: 2019-05-06
forum: Server Platforms
---

### Post by damo12 on 2019-05-06
Hi,

In our office we use a Sage accounting package on a Windows machine which automatically backs up to a share on a headless Ubuntu server.  The filename of each backup is: "*SageAccts Company Name Ltd 2019-04-29 16-47-04.001*".

I have a script which runs each night carrying out various backups.  As part of this script, I would like to move the oldest Sage backups to another location leaving only the 5 newest backups in the original folder.  After some searching and trial and error, the code I have is:
```
ls -t "/media/server/Accounts/Sage Backups/" | tail -n +5 | xargs mv -v -f  "media/server/Accounts/Sage Backups" "media/archive/Accounts/Old Sage Backups/temp"
```


When I try to run this, I receive the error message:
```
mv: target '16-47-04.001' is not a directory
```


I have tested the first part of the code:
```
ls -t "/media/server/Accounts/Sage Backups/" | tail -n +5
```

and that is working fine listing everything except the newest 5 files.

I know that I am receiving this message because the filename has spaces in it but I cannot find a way around this issue.

Any help you can offer would be greatly appreciated.

---

### Post by TheFu on 2019-05-06
There are lots of different ways to handle this.
Using 'ls' in a script is dangerous. Shell scripts have built-in file "globbing" capabilities which handle filenames with spaces correctly.

Anyways, it appears that you don't really understand directory paths.  
Every program running on any Windows or Unix computer has a PWD - present working directory.  This can also be called CWD - current working directory.  In the script above, the mv command is using relative paths, not absolute paths.  Scripts should almost always use absolute paths, so they don't fail if the CWD isn't where we think it is.

/root/ and root/ are different unless our PWD is /.
/media/archive and media/archive are different unless our PWD is /.  When you login to a Unix system, open a terminal, your PWD will be ~/  which is also called $HOME. It is often /home/{userid}, but can be setup to be anywhere.
These are all the same:
```
/home/thefu == $HOME == ~/
$ pwd 
```
**cd ~** is the same as **cd $HOME** is the same as **cd /home/thefu**
If my PWD is /tmp, then any scripts I've written that use relative paths will fail. If those scripts use absolution paths, paths that always begin with a /, then they will work.

While I wouldn't use **ls -t** in a script, ever (it is very dangerous), this should fix it:

```
ls -t "/media/server/Accounts/Sage Backups/" | tail -n +5 | xargs mv -v -f  "/media/server/Accounts/Sage Backups" "/media/archive/Accounts/Old Sage Backups/temp"
```
I've made some assumptions.  
I would probably solve this using **rsync** since there is little to be lost by having 2 copies of backups.  Then I'd use a 'find' command to remove and backup files older than, 90 or 180 days. Something like this (I didn't test it):
```
#!/bin/bash
SOURCE="/media/server/Accounts/Sage Backups"
TARGET="/media/archive/Accounts/Old Sage"
BCK_TIME=180

if [ ! -d $SOURCE ] ; then
   echo "Directory doesn't exist: $SOURCE"
   exit 1;
fi

if [ ! -d $TARGET ] ; then
   echo "Directory doesn't exist: $TARGET"
   exit 2;
fi
/usr/bin/rsync -avz $SOURCE/ $TARGET/
if [ $? != 0 ] ; then
   echo "rsync failed: $?"
   exit 3;
fi
/usr/bin/find  $TARGET -type f -atime +$BCK_TIME -print
# /usr/bin/find  $TARGET -type f -atime +$BCK_TIME -delete   # uncomment this line if the command above is working well
if [ $? != 0 ] ; then
   echo "find cleanup failed: $?"
   exit 4;
fi
exit 0

```

As for keeping local backups, rsync mirrors files, it doesn't move them, keeping 2+ copies is an important idea for backup of really important data. Really, to have a proper business backup, the files need to be in 3 different physical locations on at least 2 different types of media.  You could add another 'find' command with the SOURCE to delete old files.

With my script (which I didn't actually test), you can set it up to run from cron safely because of the way it is written using full paths, not relative paths.

I'm not a fan of directories with spaces or files with spaces.
I'm not a fan of having permanent storage mounted under /media/ or anywhere the OS automatically mounts things.  Important storage deserves to be mounted to somewhere I control without risk of the OS doing some funky mounting over it.  I'm kinda surprises there are permissions issues.

---

### Post by sisco311 on 2019-05-07
+1 for rsync / find combination.

Please check out: [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs) to get an idea why you shouldn't use ls in scripts.

Also check out BashFAQ #3 for some examples for listing the oldest/newest files from a directory based on mtime.

But let's have a bit of fun. I would put the files in an array. Assuming that the date in the filenames is the creation date you can simply use a glob:
```
unset files
files=("./SageAccts Company Name Ltd "*)
```

Now lets check how many files we have:
```
nr="${#files[@]}"
echo "$nr"
```
If we have more that 5 move the old ones:
```
if ((nr > 5))
then
  echo mv -v -b "${files[@]:0:nr-5}" path/to/dest
fi
```

---

### Post by damo12 on 2019-05-07
Thanks sisco311,

That works great, makes perfect sense and I can adapt it as required.


TheFu, thanks for your reply.  Although I have been using Ubuntu for a number of years, I only use it rarely and have very limited knowledge hence my confusion over directory paths.

Regarding backups, this is a very small part of the daily and weekly backups which are quite comprehensive.  For the purposes of asking the question, I shortened the directory names.  Both directories are located on the "server" drive mounted at /media.  Each night, there is an automated rsync "copy" script which copies everything to a second drive.  As part of this script, all mission critical files are backed up to cloud storage using Rclone ([https://rclone.org]("https://rclone.org/")).

The main reason for initiating this script is to prevent the cloud storage being filled with a lot of accounts backups which are quite large.  Currently, we have to manually delete older files from this storage.  Only the last 5 are deemed to be mission critical as each one is an evolution of the previous one.

Once every week, there is an additional rsync "copy" script which copies everything to an external USB drive, there are 4 of these drives kept off-site and rotated in turn.

As part of my aim to always improve the strength of the backups, I plan to create regular tarballs containing the really important files (accounts, database etc).  To automate this, I need to be able to select the just the newest file.

I appreciate your dislike of directories and filenames with spaces however Sage automatically generates the filename meaning that the user would have to manually modify it every time a backup is created which increases the risk of something going wrong.  When it comes to the directory names, the users of the computers are not computer literate and I have to let them create directories which make sense to them and are easy to read.

Thanks again

---

### Post by TheFu on 2019-05-07
I figured it was something like that. 

I wouldn't use tarballs.  Use a real backup tool like rdiff-backup or duplicity. Let the tool handle the versioning.  Both are efficient for network and storage.  TGZ should only be used like a ZIP file, IMHO. Only for trivial storage needs, smaller than 50MB before the tgz creation.

We use rdiff-backup, then use rsync to push those offsite.  Before doing the first backup, some scripts run to capture system data like package lists, dumping DBs, system configs with these things placed into a location that gets included in the rdiff-backup.  This way, our daily backups have everything necessary to restore the system to the same state, while not being overly complex. 

Se don't use cloud storage.  I have a very hard time trusting the entire cloudly businesses.  All of them have leaks and failures. OTOH, I think I can roll my own as good as they can, and limit the risks sufficiently.

We also only "pull" backups from a backup server that doesn't have internet access. Mounting storage on client machines for backups could allow crypto-malware to destroy backups.  The clients cannot directly can access to the backups server. The connections are 1-way, from the server, using ssh-keys, to the clients.

Funky scripts concern me.  If a script uses methods that I and most average-level admins can't create ourselves, then how will someone else restore the data if I'm hit by a car tomorrow.  OTOH, my limited bash skills can always be improved, though I generally switch to perl for non-trival uses.  For many years, when I was a Unix admin, we didn't have bash, so I tend to write Bourne shell script, not even using ksh features, much less bash or zsh features.  Dealing with arrays in bash is painful.  Dealing with arrays in python, ruby, perl, is a joy.  Just say'in.

I was a maintenance software programmer for 5 yrs. When I look at code that I don't immediately understand, I get a little concerned that others won't understand it either.  Please ensure at least 2 people, hopefully more, can understand the code.

---

