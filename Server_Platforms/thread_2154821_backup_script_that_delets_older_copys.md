---
title: "backup script that delets older copys"
date: 2013-06-16
forum: Server Platforms
---

### Post by m9365428 on 2013-06-16
I am new to scripting in linux and I'm juming in head deep.
I have a script that:
[INDENT]stores date to variable [/INDENT]
[INDENT][INDENT]"DATE=$(date +%m-%d-%y_%H:%M)"[/INDENT][/INDENT]
[INDENT]creates folder using the variable as the folder name [/INDENT]
[INDENT][INDENT]"mkdir $DATE"[/INDENT][/INDENT]
[INDENT]and then copys the files into that folder [/INDENT]
[INDENT][INDENT]"cp $source/file $target/$DATE/file"[/INDENT][/INDENT]

I have the script running and I found a problem. After a few months I start running out of drive space. I only need to have 7 days of backup but I can only get on the server to delete the older folders every 4-7 weeks. 

What I need is a command operator that will reed the name of all folders in my archive folder and test if that folder is older than 'x' days and delete it.

I am trying to learn how to read the man pages to write a file like this so if you would be so kind as to explain your code I would appreciate it.

---

### Post by CharlesA on 2013-06-16
You could try using

```
date --date=STRING
```

Where STRING is two weeks ago or eight days ago.

---

### Post by Cheesemill on 2013-06-16
Take a look at [rsnapshot]("http://www.rsnapshot.org/"). It will handle the removal of old backups for you.

I use rsnapshot to backup my home folder and it automatically keeps 1 days worth of hourly backups, 1 weeks worth of daily backups, 2 months worth of weekly backups and 1 years worth of monthly backups but you can set it up however you want.

---

### Post by SeijiSensei on 2013-06-16
I use the approach Charles suggests where I create another environment variable with the same date codes but in the past.  Using your example, 

```
STALE=$(date +%m-%d-%y_%H:%M --date='8 days ago')
```

I then use "rm -rf $STALE" to delete the directory or files.

---

### Post by CharlesA on 2013-06-16
> **SeijiSensei said:**
> I use the approach Charles suggests where I create another environment variable with the same date codes but in the past.  Using your example, 

```
STALE=$(date +%m-%d-%y_%H:%M --date='8 days ago')
```

I then use "rm -rf $STALE" to delete the directory or files.

I've been wanting to implement that in my backup script, but so far I haven't gotten around to it. I would still need to determine how often to prune my daily backups, but since I still have around 500 GB left on my backup drive, I'm pretty much putting it off. :lol:

---

### Post by m9365428 on 2013-06-16
@CharlesA Thanks for the info but I didn't understand what you meant. When I looked at a man page for date I didn't find what I could input for the string in "--date=STRING".

@SeijiSensei Thanks for clarifying what CharlesA said. After testing the command string that you suggested I searched for a date man page again. After looking at 4 or 5 different man pages i found one that finally gave a few examples of what the STRING could be. 
Seeing as there are so many sources of man pages out there can you suggest a preferred source. It appears that some of these sources leave out a good bit of detail.

@Cheesemill Thank you for suggesting rsnapshot. I'm not looking to backup entire directories for crash recovery. My application is more narrow and focused. 
I'm running several game servers with active maps. These map files change as players interact with the environment and on rare occasion crash when an in-game items background code has an error.  Since I didn't write the code to these games or their servers I cannot fix the issue only report it and wait. To keep the server online I have to ask the player when they placed/used the item and reload a backup just prior to that time. Yes I loose world data but all the players prefer to loose up-to 60 minutes of work over the sever being down for 1-3 weeks while the game authors fix the issue.
I don't know know how rsnapshot stores the archived files so I am hesitant to spend allot of time to test and see how it works.
Don't get me wrong I'm thankful for the input and will explore that option in the future but for now I think I will look into the other method mentioned. 

To clarify on what I'm trying to do. I have several game servers running on one "box" under different user accounts (MC, CS, KF(Don't ask to join it's limited to friends and colleges only they paid for the box and want it that way I only administrate it they own it)). 
To preserver certain servers world files which like to break regularly (bloody mods) I have been using a backup file to save a 'clean' copy of those problematic files. In an archive folder that is labeled as the date it was created and inside is an hourly folder labeled with the time it was made. So I end up with many folder containing 24 folders of files. 
Works great I can find the exact files I need to restore too (aka latest file just before the crash occurred). But I have a problem, I ran out of HDD space after I wasn't able to logon the server to remove the old folders for a few weeks(8 or so, we need a bigger HDD) I am trying to rewrite my macro or find an alternative method of using that file structure so that all needed files are backed up and copies over 7 days old are automatically deleted to clear up HDD space.

I will work on the file and post a trimmed down version soon as I'm done.

---

### Post by CharlesA on 2013-06-16
I usually use whatever pops up when I google "man whatever command"

It's usually a mix of these two sites though:
[http://ss64.com/bash/date.html](http://ss64.com/bash/date.html)
[http://linux.die.net/man/1/date](http://linux.die.net/man/1/date)

I really like ss64.com.

---

### Post by markbl on 2013-06-17
> **m9365428 said:**
> In an archive folder that is labeled as the date it was created and inside is an hourly folder labeled with the time it was made. So I end up with many folder containing 24 folders of files.
You really should make the effort to learn about rsnapshot as it is just perfect for this. You can set it to create N by hourly "snapshots" of the folder[s] you want saved (and weekly, and monthly, if you want etc). The best thing is that even though it looks to users like complete independent copies of the full tree of files, it actually only uses disk space for one copy plus the incremental differences. This is done internally via the magic of the rsync --link-dest option. Rsnapshot is kinda like Apple's Time Machine backup.

---

### Post by m9365428 on 2013-06-17
@ markbl I will look at it when I get more time but for now I got something to work.

My existing backup script hasn't really changed. Instead I made a new script that runs once a day. Here is a striped down version of the file.
```
#!/bin/bash
path='/home/minecraft/test'
DAY1=$(date +%m-%d-%y)
DAY2=$(date +%m-%d-%y --date='1 days ago')
DAY3=$(date +%m-%d-%y --date='2 days ago')

shopt -s extglob
cd $path
rm -r !(\
$DAY1|\
$DAY2|\
$DAY3)
echo "after"
ls
echo -ne
```
I tried to insert spaces to make reading the rm command easier but the command failed to run.

I also tried placing the date commands directly instead of storing them in a variable and it failed. I think the program was trying to look for a folder labeled as the command. Is there a way that I can pull the output of the date command directly as the operator declaring the folder name.
In other words I would like to replace the variable '$DAY' call with a direct call of the output of 'date +%m--%d-%y --date='1 days ago'. Any idea how I could do this.

I can make the script work as is I'm just trying to use 1 line per folder to keep instead of 2. You know compress it to as few lines as possible.

---

### Post by 3L33T on 2013-06-17
My suggestion:  

Utilize cron job scheduling.

1. Setup a cronjob that will execute your daily/nightly/weekly backup.

2. Setup a cronjob that will cleanup your backup files every X days/months.

---

### Post by CharlesA on 2013-06-17
> **3L33T said:**
> My suggestion:  

Utilize cron job scheduling.

1. Setup a cronjob that will execute your daily/nightly/weekly backup.

2. Setup a cronjob that will cleanup your backup files every X days/months.

This is the best solution if you do not want to modify the existing script.

---

### Post by 3L33T on 2013-06-17
Or, Utilize the linux "find" utility:

# /usr/bin/find <backupdir> -mtime +<how many days?> -print -exec /bin/rm -f {} /;

---

