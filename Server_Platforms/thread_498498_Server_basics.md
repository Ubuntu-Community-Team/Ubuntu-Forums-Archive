---
title: "Server basics?"
date: 2007-07-11
forum: Server Platforms
---

### Post by 56seeker on 2007-07-11
Hello all; 

Having got used to Ubuntu on my laptop over the first couple of months I've taken the plunge and installed my first server; and of course I've a couple of basic questions:

1) Installers. Are there any "list" type utilities which show what applications are available? I guess I'm really looking for a command line version of Synaptic, even if it looks like Midnight Commander :) I realise I could do it by command line such as: sudo apt-get install mc; but that presupposes I know that the app is there, it's name and any dependancies; which is a bit much to expect from a newbie.

For instance, long term it's my aim to have the system Email me if, for example, a RAID disk fails; so I imagine I'll need to install some kind of SMTP server; is there any way to find out what's available from a repository listing? How would I find it's dependancies?

2) File transfer. How do I "share" folders/partitions (which ever is the proper term :) ) in Ubuntu via the comand line? I have to servers, and I want a temporary connection to move large files between them?

Thanks in advance!

---

### Post by koenn on 2007-07-12
> **56seeker said:**
> 
For instance, long term it's my aim to have the system Email me if, for example, a RAID disk fails; so I imagine I'll need to install some kind of SMTP server; is there any way to find out what's available from a repository listing? How would I find it's dependancies?

You can find packages in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
It has keyword and advanced seach features. 

The commandline approach would be
```

apt-get update
apt-cache search KEYWORD

```

eg.```

~$ apt-cache search email
...
courier-imap - Courier Mail Server - IMAP server
courier-pop - Courier Mail Server - POP3 server

~$ apt-cache search SMTP
...
python-twisted-mail - An SMTP, IMAP and POP protocol implementation
python2.4-twisted-mail - An SMTP, IMAP and POP protocol implementation
courier-base - Courier Mail Server - Base system
exim4 - metapackage to ease exim MTA (v4) installation

```
MTA stands for Mail Transfer Agent  - a.k.a a "mail server"


You don't have to work out dependencies, apt-get, aptitude, synaptic etc do that for you. 

> **56seeker said:**
> 2) File transfer. How do I "share" folders/partitions (which ever is the proper term :) ) in Ubuntu via the comand line? I have to servers, and I want a temporary connection to move large files between them?

To just copy between servers, you need a user account on each server. log in on one server, then transfer files to the other one.
like, I'm kn on server1 and I want to copy a large_file to the home directory of nn on server2. You need to know the username and password of nn on server2, and go
```
scp large_file  nn@server2:/home/nn/copy_of_large_file 
```
You can do something similar with rsync - its more suitable for multiple files, directories, etc

```
rsync -av /etc/  nn@server2:/home/nn/config_backup/  
```

do 'man rsync' and/or 'man scp' of you need more info on syntax and options, and disregard the "rsync server' in the man page, you don't need that. 
Or read a bot here : [http://users.telenet.be/mydotcom/howto/linux/clone.htm](http://users.telenet.be/mydotcom/howto/linux/clone.htm)

---

### Post by AcworthJack on 2007-07-12
Great question!

I also run Ubuntu desktop.  It automaticly (and I hate to say it - but like Windows) finds updates and patches to software I have installed and gives the oppurtunity to install the patches/updates.

Is there a similar tool for the server?

Thanks

---

### Post by 56seeker on 2007-07-12
Thanks a lot!

Maybe apt is tool enough after all :)

Is rsynch in reality synchronising two directories? And if so could it be scheduled? (that'd be "cron"; right?)?

AcworthJack; I haven't found a way to automate the update process per se; but there's two commands: "apt-get update" and "apt-get upgrade" which I imagine could be automated in some sort of script.

The first command updates the list of available software and the second comand updates/upgrades installed software.

---

### Post by koenn on 2007-07-12
> **56seeker said:**
> Is rsynch in reality synchronising two directories? And if so could it be scheduled? (that'd be "cron"; right?)?

yes, and yes. yes, cron. you add scripts in one of the /etc/cron.___ directories, or run crontab. 

> **56seeker said:**
> AcworthJack; I haven't found a way to automate the update process per se; but there's two commands: "apt-get update" and "apt-get upgrade" which I imagine could be automated in some sort of script.
.
yep, apt-get update && apt-get upgrade, in a cron job, would automatically keep your system up to date, but you'd have to think if you really want that, on a server. Updates/patches do sometimes break things. The professional way would be to test the updates on a test-machine, and only apply them if they turn out OK. Nopt something you automate easily. 

Then again, on a simple home server, it's not all that critical, and breakage rarely occurs (in stable releases).

---

### Post by AcworthJack on 2007-07-12
> **56seeker said:**
> Thanks a lot!

Maybe apt is tool enough after all :)

Is rsynch in reality synchronising two directories? And if so could it be scheduled? (that'd be "cron"; right?)?

AcworthJack; I haven't found a way to automate the update process per se; but there's two commands: "apt-get update" and "apt-get upgrade" which I imagine could be automated in some sort of script.

The first command updates the list of available software and the second comand updates/upgrades installed software.

Thanks! Those are exactly what I was looking for.

---

