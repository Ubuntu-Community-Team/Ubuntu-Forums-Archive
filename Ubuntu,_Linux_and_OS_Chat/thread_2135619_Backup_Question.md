---
title: "Backup Question"
date: 2013-04-14
forum: Ubuntu, Linux and OS Chat
---

### Post by kr4m17 on 2013-04-14
Hello.  I am not sure what section to post this in, so if I am in the wrong section I apologize.  I am looking to use a backup utility, maybe rsync or scp to copy files in certain directories to another machine.  I can do this with no problem what-so-ever.  The problem I am having is that I want to be able to delete files on the machine that received the copies and not have them created again during the next backup.  

Just in case that is confusing.  I want to copy /example-directory/* (lets says this contains file1 file2 file3 file4 file5) to user@*remote-host*:/example-directory/.  I want to be able to delete files that were copied (lets say file1 file2 file3) on *remote-host*.  Then, the next time the backup runs, I do not want the files that were deleted to copy again.  So lets say between backup one and backup two files file6, file7 & file8 were created.  Even though file1, file2 & file3 were deleted I only want the contents of the example directory on the *remote host* to be file4, file5, file6, file7 & file8.

I hope that makes sense.  Thank you in advance for the help.

---

### Post by sudodus on 2013-04-14
the man page of ***rsync*** describes **[FONT=courier new]--exclude-from=FILE[/FONT]**

```
--exclude-from=FILE     read exclude patterns from FILE

       --exclude=PATTERN
              This option is a simplified form of the --filter option that defaults to an exclude rule
              and does not allow the full rule-parsing syntax of normal filter rules.

              See the FILTER RULES section for detailed information on this option.

       --exclude-from=FILE
              This  option  is  related to the --exclude option, but it specifies a FILE that contains
              exclude patterns (one per line).  Blank lines in the file and lines starting with ’;’ or
              ’#’ are ignored.  If FILE is -, the list will be read from standard input.

```

You can enter the names of the deleted files into FILE, and the best thing is probably to make a script to do that at the same time as you delete the files.

But it would be much easier to delete the files you don't want to back up from both the target and source. After all, if you don't need the backup copy, why do you want to keep the original file? Then you can use ***Unison*** to synchronize the source and the target.

---

### Post by kr4m17 on 2013-04-14
So this is not actually for backup purposes.  I have a storage server that stores all of the files that need to be accessed by anyone in my network. These files are large and my network is not a single physical site.  There are times that it is easier to work with these files if they are locally stored at whichever site is currently working with them.  If a change is made, so does the filename.  I want to copy new versions of any files to my remote-site file servers so there are local copies of the large files.  In the end, all files will be saved on the central storage server.  I just don't want to replicate the entire 28TB storage server to all of the smaller servers.  Think of the remote-site storage servers as a local cache that will be cleared manually when the project is complete.

---

### Post by sudodus on 2013-04-14
The problem is for rsync to tell the difference between a file that was deleted from the local cache, and a file that was never there.
The **[FONT=courier new]--exclude-from=FILE[/FONT]** could solve that problem, but maybe not very conveniently. Another method might be to replace the files in the local cache with empty files, that are 'newer on the receiver' and use the **[FONT=courier new]--update[/FONT]** option.

```
-u, --update                skip files that are newer on the receiver

       -u, --update
              This forces rsync to skip any files which exist on the destination and have  a  modified
              time that is newer than the source file.  (If an existing destination file has a modifi&#8208;
              cation time equal to the source file&#8217;s, it will be updated if the sizes are different.)

              Note that this does not affect the copying of symlinks or other special files.  Also,  a
              difference  of  file  format  between the sender and receiver is always considered to be
              important enough for an update, no matter what date is on the objects.  In other  words,
              if the source has a directory where the destination has a file, the transfer would occur
              regardless of the timestamps.

              This option is a transfer rule, not an exclude, so it doesn&#8217;t affect the data that  goes
              into  the  file-lists,  and  thus it doesn&#8217;t affect deletions.  It just limits the files
              that the receiver requests to be transferred.
```

You can use an alias or script with removes and touches a file with a particular name, so that an empty file with that particular name will be there with a newer time stamp, like this very simple example

```
#!/bin/bash
rm "$1" && touch "$1"
```

---

### Post by kr4m17 on 2013-04-14
Hmmm, I think I can make that work.  Thanks for the idea!  I was thinking, this is pretty much just copying new files to a dead drop... Think of it that way.  Maybe that will give someone a better idea.

---

### Post by breezypt on 2013-04-14
Sudodus, do you recommend Unison to use as a regular back up, from one disk to another on the same computer?

 I'm looking for a backup system that I can restore from one disk to another if the one OS goes ballistic on an update.

 I'm not trying to highjack this thread but if its about backups I figure why not include it into this one instead of just starting a redundant thread.

---

### Post by sudodus on 2013-04-14
I'm not sure Unison is the right tool for such a backup. If you want a complete backup, I suggest Clonezilla (to make a cloned image). But if you backup certain directories with for example rsync or some GUI using rsync, it will be easy to restore your system to something similar, that will work. There are Deja Dup, Simple Backup and several other tools for backup. If you need more help or some specific kind of backup, you should start an own thread and keep that discussion separate from this thread. It will not be redundant :-)

---

### Post by sudodus on 2013-04-14
> **kr4m17 said:**
> Hmmm, I think I can make that work.  Thanks for the idea!  I was thinking, this is pretty much just copying new files to a dead drop... Think of it that way.  Maybe that will give someone a better idea.
Did you notice, that I made a change to the script, so that it won't create an empty file, if the parameter is not found (not a file)?

Another way would be to use ***find*** to select only files newer than a certain time, and copy only those files.

---

