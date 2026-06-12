---
title: "FTP server question"
date: 2007-01-03
forum: Server Platforms
---

### Post by Kinn on 2007-01-03
Hello,

I'm currently using proftpd and I am trying to set it up so that each person from my company can have a seperate login and folder. I would like to set it so when each user logs in it takes them to their own seperate folder and they are locked into that folder.

So if MikeD logs in, he is thrown into the folder "MikeD" and is locked there, but has write/read/overwrite permissions in his folder.

Does anyone know how to setup the proftpd.conf file to allow such an enviroment?

---

### Post by chrisfay on 2007-01-03
lol....read the post under the exact same title under your's. There's a link to Proftpd's documentation on the subject

---

### Post by NumberOne on 2007-01-03
I have this setup using Pure-ftpd.  It was pretty easy to setup and there are a few good How-to's on this forum that will walk you through it.

---

### Post by Lucho77 on 2007-01-04
I am sure this thread will help you.
[http://www.ubuntuforums.org/showthread.php?t=79588&highlight=ftp](http://www.ubuntuforums.org/showthread.php?t=79588&highlight=ftp)

---

### Post by nix4me on 2007-01-04
That is a basic private user setup.  The proftpd documentation is very clear on your setup.  Use localusers and defaultroot ~ each person into their own home dir.

[http://www.proftpd.org/docs/](http://www.proftpd.org/docs/)

nix4me

---

