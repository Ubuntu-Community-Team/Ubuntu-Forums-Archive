---
title: "Server startup file"
date: 2006-12-16
forum: Server Platforms
---

### Post by NumberOne on 2006-12-16
I am fairly new to Linux.  I am runing Pure-ftpd, an I am trying to use Virtual users.  In order for this to work, I need the ftp server to start with this command.

```
/usr/sbin/pure-ftpd -j -lpuredb:/etc/pure-ftpd/pureftpd.pdb &
```

how do I make this part of my boot up sequence.  Please be specific as I am a noob.

I am running ubuntu 6.10 with the gnome desktop.

Thanks,
Tony

---

### Post by PilotJLR on 2006-12-16
Just add that exact command to the end of /etc/rc.local, and it should be run at the end of the normal sys V startup tasks.

---

### Post by MJN on 2006-12-17
However if PureFTP is started at boot time anyway (just without the options you want) then find it in /etc/init.d/ and edit accordingly. The file will likely contain a line specifically for options.

If you get stuck post the file and I'll tell you what to modify.

Mathew

---

### Post by NumberOne on 2006-12-17
Thanks MJN and Pilot,
puting the command in the rc.local worked just fine.  MJN, I do not have an init.d file in /etc.  Am i supposed to?  I do have a folder called init.d.

---

### Post by MJN on 2006-12-17
Yeah I meant the pureftpd file inside /etc/init.d/

The problem with starting it from rc.local is that it's likely to be already running given that it'll have been started from the script in /etc/init.d/ (in here live the majority of scripts controlling the starting/stopping/reloading of services) and so whilst it may 'work' it's very sloppy at best and could give rise to difficulties.

Not knocking Pilot's suggestion, just giving another opinion of what might be better.

Mathew

---

### Post by chrisfay on 2006-12-17
EDITED: lol....me<------------too slow

---

### Post by MJN on 2006-12-17
Chris, we do keep bumping into each other... clearly we've followed similar paths as to where our 'knowledge' lies! ;)

Mathew

---

### Post by chrisfay on 2006-12-17
I was thinking the same thing......:mrgreen:

---

### Post by Andycas on 2007-11-28
Im having same issue, however I want to add this to my init.d/pure-ftpd.
I dont know which option should I change.
The line I want it to use would be: "/usr/sbin/pure-ftpd-mysql -j -lpuredb:/etc/pureftpd.pdb &"

Here is my current configuration: [http://andycas.pri.ee/pure-ftpd-mysql](http://andycas.pri.ee/pure-ftpd-mysql)

---

### Post by MJN on 2007-11-28
What's your question?

---

### Post by Andycas on 2007-11-29
Umm, I need to have my pureftpd start up with this: "/usr/sbin/pure-ftpd-mysql -j -lpuredb:/etc/pureftpd.pdb &".
So I looked at the /etc/init.d/pure-ftpd-mysql, but didn't know where to put this line... I tried putting it at "DAEMON=....-$SUFFIX", but that didn't have any effect, the ftp server wouldnt start either...
My /etc/init.d/pure-ftpd-mysql is here: [http://andycas.pri.ee/pure-ftpd-mysql](http://andycas.pri.ee/pure-ftpd-mysql)

---

### Post by MJN on 2007-11-29
It look like quite an involved startup script so it might be best searching on pure-ftp related forums for this. I don't use it myself but it's obvious from this thread that the requirement exists for some to start it with specific options so the solution must have been discussed elsewhere.
 
Mathew

---

### Post by Andycas on 2007-11-29
Ive tried finding info on this issue, but havent found any workable solution... Ive found out, that on debian the startup arguments are in "/etc/conf.d/pure-ftpd". However I couldnt find this dir on ubuntu. :(

---

### Post by Andycas on 2007-11-29
Ive tried using the rc.local file too, but that didnt work.
I cant keep shutting the server down myself and booting it up with that argument, there has to be a some kind of a solution :(

---

