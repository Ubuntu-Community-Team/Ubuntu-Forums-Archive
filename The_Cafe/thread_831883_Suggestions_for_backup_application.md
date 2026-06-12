---
title: "Suggestions for backup application"
date: 2008-06-17
forum: The Cafe
---

### Post by damoxc on 2008-06-17
I decided to write a backup application in python for use at where I work initially to backup unix machines.

It's expanded a little bit to allow you to deploy configuration files from version control, you can also restore backup files to the host.

All of it is still very young but I was merely curious if anyone could think of any additional things that would be useful for such an application to contain.

It's on launchad at: [http://www.launchpad.net/soter](http://www.launchpad.net/soter)

---

### Post by eldragon on 2008-06-17
nice. i just wonder why make yet another backup script based on rsync when there are dozens.

what i mean,is what does this aproach offers that some others dont.

i use rsnapshot to backup, which is sort of what you are doing. doesnt support subversion, but relies on hardlinks for incremental backups.

so, what does your approach offer that isnt yet out there? maybe you should concentrate your efforts in adding functionality to other backup projects out there. but again, i dont know much about anything. just asking why :D

anyway, good luck

---

### Post by tamoneya on 2008-06-17
you should take a look at sbackup.  It is what I personally use as my backup system for both my laptop and my desktop.  The part you may find the most interesting however is that most of it is written in python as far as I can tell.  See if you can get your hands on the source code.

---

### Post by damoxc on 2008-06-17
After a quick look SBackup is GUI based? And to be run on the machine being backed up.

The one I'm writing is geared more towards a server environment, so no gui. The backup process gets called by cron every hour and checks to see if a backup needs to be performed and pulls the files remotely off the server.

The other reason is purely I wanted to simply try making one in python as I've only recently just started, so it's mostly for fun that I'm writing it.

---

### Post by beercz on 2008-06-17
Aren't you duplicating the effort?  Have a look at [http://rsnapshot.org]("http://rsnapshot.org/")

---

### Post by beercz on 2008-06-17
> **eldragon said:**
> nice. i just wonder why make yet another backup script based on rsync when there are dozens.

what i mean,is what does this aproach offers that some others dont.

i use rsnapshot to backup, which is sort of what you are doing. doesnt support subversion, but relies on hardlinks for incremental backups.

so, what does your approach offer that isnt yet out there? maybe you should concentrate your efforts in adding functionality to other backup projects out there. but again, i dont know much about anything. just asking why :D

anyway, good luck
rsnapshot is brilliant - use it every day

---

### Post by tamoneya on 2008-06-17
> **damoxc said:**
> After a quick look SBackup is GUI based? And to be run on the machine being backed up.

The one I'm writing is geared more towards a server environment, so no gui. The backup process gets called by cron every hour and checks to see if a backup needs to be performed and pulls the files remotely off the server.

The other reason is purely I wanted to simply try making one in python as I've only recently just started, so it's mostly for fun that I'm writing it.

I realize this and I wasnt as much recommending that you use it but look at the source code.  Yes it is GUI based but just ignore that section of the source code and you may find something interesting stuff.  You could look at the code in there for the incremental backups and such as well as the logarithmic backup managment.

---

### Post by damoxc on 2008-06-17
> **tamoneya said:**
> I realize this and I wasnt as much recommending that you use it but look at the source code.  Yes it is GUI based but just ignore that section of the source code and you may find something interesting stuff.  You could look at the code in there for the incremental backups and such as well as the logarithmic backup managment.

Ah thanks, I will look at it for ideas for the backup part.

Not sure whether moving in a more deployment focused direction would be beneficial, adding the ability to run tests on a new configuration file to avoid errors etc.

---

