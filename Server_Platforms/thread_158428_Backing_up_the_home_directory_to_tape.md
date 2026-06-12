---
title: "Backing up the /home directory to tape"
date: 2006-04-11
forum: Server Platforms
---

### Post by towerofsong on 2006-04-11
Hi there I need to setup a weekly backup of the /home directory to a tape drive. I've managed to get the tape drive working...I think, I can send it commands at the very least. I do not need any web servers, or anything complicated like that. I just need it to backup the /home directory. Nothing less, nothing more. What is the easiest way to do this? All the software i've looked at, amanda, backuppc, partimage, afbackup, I either can't get working correctly or it does way more than I need.

Thanks.

---

### Post by hagen00 on 2006-04-11
Hmmm, 

Not sure if this will work for a tape drive, but i followed the advice of[this]("http://servers.linux.com/article.pl?sid=04/11/04/0346256&tid=119&tid=47&pagenum=1") article and it worked very well for me. Basically it takes you through how to backup to a remote computer (whether incremental backups or snapshots, your choice). Maybe your tape drive can be treated like a remote computer? Don't know what i'm talking about really, since i've never used tape drives before, but if you can "ssh" to your tape drive then this should work. Just my 0.5 cents.

---

### Post by towerofsong on 2006-04-11
Cheers for your suggestion

I tried backing up using the tar command
I typed
tar cvf /dev/st0 /home
but after going through all the files it errors out with

"tar: /dev/st0: Cannot write: Input/output error
tar: Error is not recoverable: exiting now"

argh

---

### Post by hagen00 on 2006-04-11
```
tar cvf /dev/st0 /home
```
take a look at the tar man page. You need to do something like

```
tar cvf mybackupfile.tar /home
``` That will put the tar file into your current directory (assuming you have write permissions to your current dir)
What are you trying to do with /dev/st0?

---

### Post by towerofsong on 2006-04-11
Ok I have definately managed to get data on to the tape now. So I need to automate the process, I guess using the cron is the best way?

I have created a script and made it executeable. Will this work for backing up my /home directory to tape, then rewinding and ejecting the disc?

tar cvf /dev/st0 /home
mt -f /dev/st0 rewoff

or will this try to eject the tape straight after the first command? Aborting the copy process?

---

### Post by hagen00 on 2006-04-11
ah, ok, /dev/st0 must be your tape drive. 

I'm pretty sure that the second command will only run once the tar has been completed. That's how it usually works. So, no, I don't think the copy process will be aborted. Why don't you just try it out...

---

### Post by towerofsong on 2006-04-12
Heh yeah I did try it, it seems inconsisten, sometimes it works, sometimes it doesn't. I set it up in the crontab and it ejected the tape after a few seconds of running. And when checking the tape contents with "tar tvf" it errors out after a bit with "Unexpected EOF in Archive."
Almost there, heh. Desperate to get this working as its going to be backing up people's data in work every day. Need to get it so it is stable.
I will go have another crack and just to figure out the error.
Cheers

*Edit* It works fine if I execute the script backup.sh from a terminal. But when I do it from a crontab it fails after a few files every time. Really don't understand.

---

### Post by hagen00 on 2006-04-12
> *Edit* It works fine if I execute the script backup.sh from a terminal. But when I do it from a crontab it fails after a few files every time. Really don't understand.

That is usually a user permission problem, but in your case it shouldn't be, because cron runs as root i think, meaning your script will be executed as root. When you say it works from the terminal, try to become root first and then run it from the terminal. See what happens then. (i.e. run the script from the terminal by putting a sudo in front).

Edit:
Please discount the above. If you open up /etc/crontab you can actually choose which user should run the script. So just make sure that the same user that sucessfully runs the script from the terminal, also runs it from cron.

---

### Post by allenlux on 2006-04-12
I recommend using a little package - really just a script - called flexbackup. It has worked almost flawlessly since I first set it up with my DDS-2 tape drive. I use the "afio" archive type. If anyone is interested, my flexbackup.conf file is here: [http://www.homepages.lu/allen/linux_flexbackup.htm](http://www.homepages.lu/allen/linux_flexbackup.htm)

---

### Post by StarryTripper on 2007-02-15
I just got a DDS4 drive and got flexbackup setup.  What I can't figure out is should I use software compression (gzip for example) without disabling the hardware compression?  Or am I better to disable the software compression and just let the drive do it's thing.

---

### Post by mannheim on 2007-02-16
There's a a fairly simple example of a backup script for use with tar and a tape drive [here.]("http://www-math.mit.edu/~psh/tapedrive/runbackup") A look at that might be an idea to see if you are missing something.

---

