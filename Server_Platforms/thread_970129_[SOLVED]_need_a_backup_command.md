---
title: "[SOLVED] need a backup command"
date: 2008-11-03
forum: Server Platforms
---

### Post by ARhere on 2008-11-03
I am looking for a good command line tool that will help me make copies of my data.  I am not interested in a program that compresses or makes an image of the data, I just want the raw files in <destination> to match <source>.

I have been using the copy command with the -u switch to update files from <source> to <destination> but I would like files to be removed from <destination> if they do not exists in <source>.

***Explanation of question.  Read if you are bored***
I used to run a RAID-1 on my file/print/web server and that protected against loosing a disk, but that did not take care of human error.  My disk utilization is so low on the server that I realized a simple duplicate of my data every 24 hours on separate drives would be better.  If a file is lost or deleted, I have a 24 hour back up.  I would like to complete this task myself using  a script for the fun, thus why I don't want to use a back-up program.  However I am not interested in re-writing everything from scratch as I am new to Linux scripts and want to keep it simple.

-AR

---

### Post by stinger30au on 2008-11-03
i cant help you with a command line. but i have installed wine 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and i use a windows freeware program called syncback

[http://www.2brightsparks.com/downloads.html#freeware](http://www.2brightsparks.com/downloads.html#freeware)

it will run in wine and you can get it to backup directoys, sync directorys locall, ftp, lan etc


hope this may help you

---

### Post by Vegan on 2008-11-03
a long time ago people used to use tape to backup

look into tar

```
man tar
```

;)

---

### Post by cariboo on 2008-11-04
I use rsync to back up files, rsync is installed by default have a look at the man page:

```
man rsync
```

There is a good rysnc howto here:

[http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

Jim

---

### Post by shazbut on 2008-11-04
+1 for rsync, after the initial run it only copies files that have changed or been added.

Good guide here:
[http://www.whatpc.co.uk/personal-computer-world/features/2159601/linux-risk?page=2](http://www.whatpc.co.uk/personal-computer-world/features/2159601/linux-risk?page=2)

example:

rsync -av /folder/subfolder /somewhere/else

---

### Post by conjur3r on 2008-11-04
Have you had a look at rsync?  Does pretty much what you are after.

---

### Post by ARhere on 2008-11-04
Enough people have suggested it to make me think it is the way to go, have not looked at it yet.

IF I was single, I would be a mini-expert in it already.  Now that I have two little girls plus a 3 week old baby, I get 30 min of good/fun Linux work done in about a week!:mad: 

Thanks guys,
-AR

---

### Post by ragtag on 2008-11-04
[Here]("http://ubuntuforums.org/showthread.php?t=958695") is a little script I wrote that uses rsync to create incremental dated backups. It uses hardlinks, so only files that have changed take up extra disk space on the backup.

What you get are multiple dated versions on another drive that you can browse just like any other folder. :)

It doesn't do an automated backup, though setting up a simple cron job to run it would be easy.

---

### Post by hrod beraht on 2008-11-04
[COLOR="RoyalBlue"][SIZE="4"]rsync![/SIZE][/COLOR]

Something along the lines of:
```
rsync -r -t -v --progress --delete  /source /destination/
```

Bob

---

