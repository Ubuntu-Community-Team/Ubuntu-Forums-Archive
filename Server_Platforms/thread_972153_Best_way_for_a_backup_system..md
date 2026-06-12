---
title: "Best way for a backup system."
date: 2008-11-05
forum: Server Platforms
---

### Post by hockey97 on 2008-11-05
Ok, I have read many backup tutorials for ubuntu.

I never found good programs that can do this.

I been using commands in the bash terminal to do a backup.

I want to know what's the best and fastest way to backup a system on a external hard drive.

I followed ways to go a backup copy and save it on the root system area and make a copy of it to the external hard drive.

I notice I was not able to just move the backup compressed file onto the external hard drive saying that I don't have permissions to do so.

Which I have changed permissions to chmod 777.

So I just copied and saved the copy to the external hard drive using the bash terminal.


I would like some software that does this automatically so I don't have to keep using commands.

I want to also know how to restore this backup  if lets say my system gets currupted where I can only boot into a command area.

This happened to me a while back about 5 months ago and I lost everything even my websites that I was close to finishing. 

So I didn't want this to happen again so I bought a external hard drive.

I then started doing backups using bash but it's now a pain for me to keep typing commands since after a month or so I do a backup I forget the commands since I don't use it on a daily bases.

I  would like to know how to restore systems. ALso is it possible for me to use this backup to also install this same system on another computer??


Also is there anyway I can also build a backup system that would save 2 backups.

just in case one backup backups bad config settings ect or somthing in that order that cases the system to crash.


thanks for your time.

---

### Post by baudday on 2008-11-05
You could combine those commands you type into a bash script, and then set it as a cron job to run daily or monthly or whatever.

---

### Post by baudday on 2008-11-05
[http://simplebashbu.sourceforge.net/](http://simplebashbu.sourceforge.net/) sounds like what you're looking for

---

### Post by hrod beraht on 2008-11-05
[SIZE="4"][COLOR="RoyalBlue"]rsync![/COLOR][/SIZE]

Roughly, something along the lines of:

```
rsync -r -t -v --progress --delete /home/me /externaldrive/Backup/Current/
```

Or, to have a previous version 'archive' folder, add the -b (backup) option:

```
rsync -r -t -v --progress --delete -b --backup-dir=/externaldrive/Backup/Archive /home/me /externaldrive/Backup/Current/
```

Stick it in crontab to run automatically. Or, I just wrote a two-line script (backup.sh) which has my rsync and then shuts the computer off. I just run the script (assigned to a panel icon) and it backs up and shuts off. I just click and walk away. (That way the backup only runs when I'm not using the computer, and so doesn't slow me down).

Bob

---

### Post by hockey97 on 2008-11-06
ok, thanks for the replies. yes I am looking for a script that can do this.

I don't know all about bash scripting.

I know some commands and I have a bad memory and I currently don't use it much.

I am starting 2 websites and making a system. I at this point don't need a automation backup.

All I need is to click on something or press a keyword that would run some script that would automaticly backup my system and save it on the external hard drive.

I also have some more questions. What is a good system to prevent system crahses???

like a backup system.

lets say I or a hacker hacks into my computer and changes settings that screwed up my system.

should I make 2 backups of the system so that I can have a backup without the new configs settings??

---

