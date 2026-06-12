---
title: "Ubuntu server the way to go small office?"
date: 2007-11-05
forum: Server Platforms
---

### Post by snagaslas on 2007-11-05
Hello everyone!

I´ve just been asked by my superior we should get some nice backupsystem for all our computers before something bad happens wich will happen in given time we are talking electronics.

What I need to setup is basically a document server that is "secure". I assume I should be raiding some smart way and use 2 disks.

About 20-30 computers with windows on em will want to access the server and uploads their files against some kind of loginaccess. 
Easy as possible, was thinking of creating something that runs at startup/closeing of windows that just mirrors the users my documents/workdocument/ directory against the one on the server.

SO I assum I will be needing samba but except from that I can´t see anything more realy, and then work on some way to make it secure and the hardware I can check later on.


Is this a good solution or should I for easy sakes just go windows NT or the similar?

---

### Post by dantrevino on 2007-11-05
Definitely the way to go.  There are multiple backup solutions that integrate with windows, Amanda being one of the most popular.

---

### Post by HermanAB on 2007-11-05
Abschloooly yes! Install 'buntu with twin (mirrored) Software RAID1 disk drives and please do install a UPS for added reliability.  In my experience a UPS makes a computer last years longer since it filters out all the nasties on the mains supply.

---

### Post by sorryd on 2007-11-05
backuppc is another good package for backing up multiple PCs. I only use it for 4 PCs, but I imagine it would scale fairly well.

---

### Post by Traxman on 2007-11-06
I have only been running with backuppc but its just want i want.

Im doing backup of both servers and clients and the users can
make restore of their own data so they dont need to call me for 
restoring their missing word document.

Backuppc even does compression and it reuses the old backupfiles
so it saves diskspace. Doing backup of 250Gb daily from 25 servers
and 10 workstations and so far during the last 2 years have been
flawless.

With backuppc 3.0 you will do most settings from a webinterface
so i think you can get it up and running quite fast nowdays )

---

### Post by snagaslas on 2007-11-06
AHh thanks guys, I´ll check out both Backuppc and Amanda and see what I can figure out.

Anything in particular to think about like some stupid misstake that it´s easy to make the first time?

---

