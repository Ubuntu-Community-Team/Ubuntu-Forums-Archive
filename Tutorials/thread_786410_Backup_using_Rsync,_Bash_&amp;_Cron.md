---
title: "Backup using Rsync, Bash &amp; Cron"
date: 2008-05-08
forum: Tutorials
---

### Post by DanneUK on 2008-05-08
I wanted to backup my home directory using rsync to a separate drive, and to make it happen automatically.

I spent ages doing research into the various commands, and found everything I needed to know, but not all in the same place. While it was fun for me, others may just want to know how to do it immediately.  So here goes!


**The rsync command**

```
sudo rsync -av --progress --delete --log-file=/home/your-username/Desktop/$(date +%Y%m%d)_rsync.log --exclude "/home/your-username/.gvfs" /home /media/HomeBackup
```


the -av bit: 'a' means archive, or copy everything recursively preserving things like permissions, ownership and time stamps. The 'v' is verbose, so it tells you what its doing, either in the terminal, in in this case, in the log file.  --progress gives you more specific info about progress.

--delete checks for changes between source and destination, and deletes any files at the destination that you've deleted at the source. --log-file saves a copy of the rsync result to a date-stamped file on my desktop.

--exclude leaves out any files or directories you don't want copied. In my case, the .gvfs directory in Hardy Heron was a pain as even with sudo it errored and wouldn't copy properly, so I excluded it (Its not necessary to copy it anyway)  If you don't use Hardy yet, or any distro using the latest Gnome, skip this line, or upgrade!

/home is the directory I want copied. /home copies the directory and its contents, /home/ would just copy the contents

/media/HomeBackup is the separate drive.  Change this to whatever your backup location is. You can actually have this drive off-site and use ssh, but that will be a tutorial for another day!


**The bash script**

I was just pasting this command into Terminal each day, but wanted something automatic, so step one was a bash script.

Very easy, just open a new document in your favourite text editor, and type #!bin/bash followed by the command itself on a new line. So:

```
#!/bin/bash
sudo rsync -av --progress --delete --log-file=/home/your-username/Desktop/$(date +%Y%m%d)_rsync.log --exclude "/home/your-username/.gvfs" /home /media/HomeBackup
```


Save that as rsync-shell.sh on your Desktop and make it executable by typing 
```
sudo chmod +x /home/your-username/Desktop/rsync-shell.sh
```    

or by right-clicking the file, select Properties, Permissions and then checking the Execute box


You can now double click that .sh file, choose 'Run in Terminal', it will ask you for your password and run, then leave a log file on your desktop.

or, you can make a cron job to do it for you!


**The cron job**

My biggest obstacle with this was the sudo bit. rsync won't be able to backup all files, or delete any, without root privileges. I didn't want to have to be there when it runs to type in my password, but after a bit of searching I found out how to make a root cron job.

Copy your .sh file to /root by typing 
```
sudo cp /home/your-username/Desktop/rsync-shell.sh /root
```

Then type 
```
sudo crontab -e
```

You'll see a line which reads:   # m h  dom mon dow   command

Under that type 
```
0 22 * * * /root/rsync-shell.sh

```
What this all means is:

1. The number of minutes after the hour (0 to 59)
2. The hour in military time (24 hour) format (0 to 23)
3. The day of the month (1 to 31)
4. The month (1 to 12)
5. The day of the week(0 or 7 is Sun, or use name)
6. The command to run

So at 22:00 (10pm) every day root will run the shell script, without prompting you for sudo password (because its running as root already)

Now press Control-X, then type Y, then press enter.

You'll see   crontab: installing new crontab

And you're done!


This article was first published by me at [[COLOR="Navy"]The Linux Basement[/COLOR]]("http://www.linuxbasement.com/content/backups-using-rsync-bash-cron") and is licensed under the Creative Commons Attribution-Non-Commercial 3.0 License


[[IMG]http://i.creativecommons.org/l/by-nc/3.0/88x31.png[/IMG]]("http://creativecommons.org/licenses/by-nc/3.0/")

---

### Post by Badbunny on 2008-05-09
Very nice, thank you.
I find it easier to do cron via kcron (in Kubuntu, that is). You can just start it with kdesu kcron and insert new jobs for any user.
Any way to remotely backup a ftp drive with rsync? I'd like my computer to backup my website automagically.

---

### Post by sirlancelot on 2008-05-09
This is awesome, put your scripts in [CODE] tags though, it makes things easier to read. Thanks for this tip! I'm going to send this to my friend who's a n00b at linux and see if he can follow it :)

---

### Post by Timbothecat on 2008-05-09
> **DanneUK said:**
> 

Save that as rsync-shell.sh on your Desktop and make it executable by typing 
sudo chmod +x /home/your-username/**_Desktop_**/rsync-shell.sh    



Copy your .sh file to /root by typing 
sudo cp /home/your-username/rsync-shell.sh /root



I just have a query as a total noob. Should the path in the copy section have the Desktop (as highlighted in the first section) as part of the path?

Sorry if this is a stupid question but I'm just a little confused as to what goes where just yet.

All the best,

Tim.

---

### Post by Luke has no name on 2008-05-09
> **Timbothecat said:**
> I just have a query as a total noob. Should the path in the copy section have the Desktop (as highlighted in the first section) as part of the path?

Sorry if this is a stupid question but I'm just a little confused as to what goes where just yet.

All the best,

Tim.

That is literal. The Desktop directory has everything that is on your desktop, like shortcuts and such.

---

### Post by Timbothecat on 2008-05-10
> The Desktop directory has everything that is on your desktop, like shortcuts and such.

Which is kind of what I was asking. When the Bash script was created the instruction was to save it on to your desktop and make it executable with the following:
```
sudo chmod +x /home/your-username/Desktop/rsync-shell.sh
```
But then it says to copy the file to root with this:
```
sudo cp /home/your-username/rsync-shell.sh /root
```
In my very limited understanding I would have thought that the copy command would fail unless there was a copy of the file in home as well as on the desktop. 

There is of course every chance that I'm missing the point here anyway.

---

### Post by Daniel_UK on 2008-05-10
Tim, yes you're right!

Thanks for pointing that out

It should read 
**sudo cp /home/your-username/Desktop/rsync-shell.sh /root**


So, you're not such a noob then for spotting that!

I'm glad the tutorial has proved helpful.  Its a nice feeling to be able to offer something back to the community.

---

### Post by Timbothecat on 2008-05-11
Can I ask a few more questions Daniel?

1. Is it better to copy the file to the /root rather than move it there? 
2. Is it possible now that it has been copied to remove the shell script off the desktop?
3. Why do I get the .gvfs error on my wifes user account. There are 5 user accounts all up on the computer but both mine and my wifes have administrator privileges while the kids ones only have user privileges. I'm assuming this is part of the issue but would love to know how to fix it.

The backup works beautifully though. Well done.

All the best,

Tim.

---

### Post by DanneUK on 2008-05-11
1. I chose to copy it rather than move it so that I'd still have it on the desktop.  The only advantage of this is if you want to manually backup sooner than 24 hours. 

For example, If you have lots new photos or documents that mean a lot to you and losing them would be catastrophic... backup them up immediately!

2. Yes you can delete it from the desktop once you've copied it

3.  I really want to find this out!  Its the new Gnome Virtual Filesystem.  I looked in the directory and it had all the tracks from the music CD which was in the drive.  All the tracks were listed as read only... aha, maybe that's it!  I will look into it a bit more, but that seems likely doesn't it?  If they're read only, you can't copy them, but does that still apply to root? Not sure.

What's in your .gvfs directory?


I'm pleased its working for you Tim.

Yours,
Daniel

---

### Post by andrew.46 on 2008-07-07
Hi Daniel,

 Great tutorial, thanks for making the effort! Would it be worthwhile perhaps to consider adding in the use of the -n or --dry-run option as a first trouble-shooting run?

 All the best,

    Andrew

---

### Post by Robocoastie on 2008-07-08
Great tutorial! I had an assignment for Linux Admin. class in which we were to find a script and cron job on the internet, summarize it and reference it. This worked so well that I used it for my assignment. Since your real name isn't listed I used your pseudonym for the reference citation.

I thought I read in one of my classes though that this could be done using tar so that it was compressed and still only backup new and changed files like rsync does. Do you know if there's a way to do that or is one of my cylinders not fireing right? (it wouldn't be the first time that happend LOL).

Rob

---

### Post by tom.swartz07 on 2010-03-28
> **DanneUK said:**
> I wanted to backup my home directory using rsync to a separate drive, and to make it happen automatically.

I spent ages ........
And you're done!


This article was first published by me at [[COLOR="Navy"]The Linux Basement[/COLOR]]("http://www.linuxbasement.com/content/backups-using-rsync-bash-cron") and is licensed under the Creative Commons Attribution-Non-Commercial 3.0 License


[[IMG]http://i.creativecommons.org/l/by-nc/3.0/88x31.png[/IMG]]("http://creativecommons.org/licenses/by-nc/3.0/")

Hey! Great job! very helpful!

I have one suggestion, rather than use "/home/[COLOR="Red"]your-username[/COLOR]/Desktop/" Why dont you edit the code so that it reads, "/home/[COLOR="red"]$USER[/COLOR]/Desktop/...." That way, no one has to change the code for their specific computer, they just copy and paste away!

Keep up the great work!

---

### Post by sirlancelot on 2010-03-30
> **tom.swartz07 said:**
> I have one suggestion, rather than use "/home/[COLOR="Red"]your-username[/COLOR]/Desktop/" Why dont you edit the code so that it reads, "/home/[COLOR="red"]$USER[/COLOR]/Desktop/...." That way, no one has to change the code for their specific computer, they just copy and paste away!

Or better, use ```
$HOME
``` ;)

---

### Post by tom.swartz07 on 2010-03-31
> **sirlancelot said:**
> Or better, use ```
$HOME
``` ;)

Truth- a simple oversight on my part. 

That would greatly simplify the commands, and prevent any type of confusion. :D Thanks again for a great guide!

---

### Post by alfplayer on 2010-05-27
This is exactly what I've been looking for.

Thank you.

---

### Post by altonbr on 2010-06-03
I also have a script that does ssh/rsync/cron over at [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979) / [http://github.com/brettalton/rsync-over-ssh](http://github.com/brettalton/rsync-over-ssh) if it's of use to anyone.

---

### Post by RudyE on 2013-01-23
With apologies for reviving an old thread, but people arriving here may be interested in a complete & tested backup script based on rsync cron and bash.

See below for a ready made solution that builds on the excellent work of Mike Rubel ([http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)), but with many additional features:

* Keep an archive of data up to one year back

* Reliable and persistent
Continues to retry transfering the files until succesful, or a user set
max retry limit.

* Use soft links to identify the most recent succesful backup
Incomplete backups will not be used for the next incremental backup.

* Advanced locking
Only one instance of the backup will run at any given time. A long
(remote) backup will never be overun by the cron job from the next day.
Stale lock files will be removed automatically.

* True set & forget functionality
Runs from a cron job, and only bothers you if an error occurs. Weekly
emails inform you the cron job is still present and functional.

* Backup to and _from_ remote hosts as well as local disks

* Versatile & compatible
Remote machines can run bash and csh as their native login shells (and
possibly others).

* Free & open source software released under the BSD license

Please check for yourself and let me know what you think. A description and link to the latest version can be found here:

[http://eschauzier.wordpress.com]("http://eschauzier.wordpress.com/")

---

