---
title: "[SOLVED] backup won't restore"
date: 2007-12-29
forum: Server Platforms
---

### Post by gishaust on 2007-12-29
Hi everyone

I setup a server to backup my data. I used simple backup to daily copy the home folder. When I was updating the other day it asked me update ubuntu from 7.04 to 7.10 so i did at the time i thought i would not have to backup my data because I had done it  with simple backup.

Now I have simple backup restore looking at the backups but it will not restore them for me.

Most of the time this would not worry me. I leave it and get on with my 
live. But I have been putting all my business data on that drive and backing it up. If I don't get it open I am going to loss 12 months of work.

Is there away through the terminal to break into the backups

please:(

---

### Post by HermanAB on 2007-12-29
Well, first of all, what is 'simple backup'?

If you can tell me how you 'backed the data up' then I can help you recover it.

Cheers,

Herman

---

### Post by gishaust on 2007-12-29
The program is call sbackup you can use it from the terminal, but it is has a gui that is in system,adminstration,simple backup.

All the information is kept on a second hard drive.
As to how i did it I used the gui interface change the drive that it should back onto and then told it to do it daily, I also only told it to backup the home folder.  

thanks for the reply

gishaust

---

### Post by HermanAB on 2007-12-29
Ok, now I don't have Ubuntu running and Googling for it turned up something that doesn't exactly inspire confidence.  The best backup systems use tar - this one doesn't...

So look at whatever you backed up to: DVD, another disk drive?

Mount it and see what kind of files are on there. 

---

From the sbackup wiki (a severely spammed wikki):

[http://sbackup.sourceforge.net/HomePage](http://sbackup.sourceforge.net/HomePage)
1. Run "System->Administration->Simple Backup Restore" and enter your password;
2. Select backup target directory from where to restore (optional);
3. Select a snapshot from the dropdown list;
4. Select a file or directory in the tree;
5. Press Restore or Restore As ... to restore.


In command line

1. Run "sudo srestore.py /var/backup/2005-11-18_04.00.07.065628.hostname.inc /home/myuser /home/myuser/old". You can omit the last parameter to restore to the same directory.

---

lot of planning went into the backup format and despite that I had to change it several times during the development cycle. Trying to keep the format as simple as possible, I came up with this:

    * All backup operations write inside one directory - target directory (default - "/var/backup/")
    * Target directory contains a subdirectory for each backup run, I call these - backup snapshots. The directory name contains time of the backup, hostname and type of backup (full or incremental). The name and structure of directories is formed in such a way to allow the user to easily manipulate snapshots: if you have too many backups, you can delete some snapshot directories, you can write these directories to CD or DVD for a way of manually backing up to external media. If you later copy a directory back to the target directory, it will be recognised and used by all restore tools. You can even copy snapshot directories between different computers.
    * Each snapshot directory contains a fixed set of files:
          o ver - this file contains the version of the backup snapshot folder format. For SBackup 0.9 it is 1.2. All snapshot directories are upgraded via upgrade-backups before the first backup run after an upgrade.
          o package - contains a dump of list of packages installed on the system at the time of backup. If you need to reinstall your system, you can use this file to do: %%(bash)dpkg --set-selections <packages 

---

The answer is out there Sculley...

Cheers,

Herman

---

### Post by gishaust on 2007-12-29
Well that is the one i have already tried. and it sayes it won't work.

Lessons I have learned,
1.if you are going to setup a server text is always better in linux.
2. Ask if you are not sure.
3.I knew i should have back up my data. Silly, silly, silly man that i am.

Thankyou for your help.


gishaust :-|

---

### Post by gishaust on 2007-12-29
heh the files are kept in a *.*gtz format if I can get to that file am I able to up tar it?

---

### Post by gishaust on 2007-12-29
how do i get into a directory that is owned by root on ubuntu?

---

### Post by HermanAB on 2007-12-29
.gtz probably means gzipped tar ball.

So copy a file to a subdir somewhere and try this:
tar -zxvf filename.gtz

And see what happens.

Cheers,

H.

---

### Post by HermanAB on 2007-12-29
OK, you will probably get fed-up with sudo, so try this:

$ sudo -i

or
$ sudo bash

That should give you a root # prompt.

Cheers,

H.

---

### Post by dixonstalbert on 2007-12-29
hello

I have used sbackup 1.4 in Feisty for some time. 

the backup is in *.tgz fomat ; ie a tar file that has been compressed with gunzip.

On my system I can open them with Simple Restore, but I found the gui difficult to follow sometimes- if I remember i had some difficulty getting it to read the right directory for the backup I wanted. maybe that is the problem you are having.

the files.tgz file that sbackup creates is a standard compressed tar file. You can open it on the command line with: tar -xvzf files.tgz or use can use archive manager to open it. My files.tgz is about 35 gig and it takes almost 40 minutes for my AthlonXP 1.9GHZ to open it in Archive Manager so be prepared to wait.

if you want to use Nautilus (Ubuntu File Manager) to view directory with backup, then open a terminal and type sudo nautilus and Nautilus will open with root privilages.

good luck

---

### Post by dixonstalbert on 2007-12-29
If you want to open it with archive manager you will have to open with root privelages so type sudo file-roller in a terminal

---

### Post by gishaust on 2007-12-29
The answer is yes, yes, yes, yes, oh am I a very happy person.

I have two more questions 
1. How do I cp whole directories at once
2. How do i back every day using tar

thankyou HermanAB  

yeh,yeh, yeh:-)

---

### Post by gishaust on 2007-12-29
Thanks  dixonstalbert, 

I just trialed what you are talking about and it work. Put i would still like to backup just using the terminal from now on

gishaust

---

### Post by gishaust on 2007-12-29
Yes Yes Yes It works I can get the files out thankyou  HermanAB your direction was great
dixonstalbert   i have tried what you told me and it worked.

I have a couple of questions how do i cp whole directories and second how do you  back up using the terminal and just get it to save in tar?

:-) yes yes yes i am very happy.

Gishaust

---

### Post by dixonstalbert on 2007-12-29
Hi gishaust

I have attached a text file of notes on how to use tar on the command line to backup and restore.

---

