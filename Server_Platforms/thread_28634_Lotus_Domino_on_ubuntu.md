---
title: "Lotus Domino on ubuntu"
date: 2005-04-21
forum: Server Platforms
---

### Post by rpm on 2005-04-21
Have ever someone tried to install it (R6) on ubuntu linux ?

Can this works correctly ?

thx

rpm

---

### Post by philcolbourn on 2005-04-21
server or client?

I think we run 56 servers on debian linux, but as of a year ago I had no luck with r6 notes on wine.

---

### Post by rpm on 2005-04-21
Lotus Domino Server

I red it have problems running on 2.6.x kernels

thx

rpm

---

### Post by philcolbourn on 2005-05-21
I don't think we had too many problems. Initially maybe, but it is certainly stable now.

We did get burnt with some IBM hard drives and reiserfs (both my ideas unfortunately - I thought IBM IDEs  would be safe!). I have not worked in the section for two years now, but I think they are running well.

---

### Post by bluefrog on 2006-05-22
I have just installed Domino 6 on breezy. works ok.

link the libstdc++ to the one domino is asking do the trick.

to run the domino setup, I have only found the following way.
I have installed it with all default settings.

as notes cd to /local/notesdata
launch Domino in listen mode
/opt/lotus/bin/server -listen

open a new terminal
sudo cp /opt/lotus/notes/latest/linux/{cfgdomserver.jar,jhall.jar,remotesetup} /home/notes

su to notes
cd /home/notes
./remotesetup

the Domino graphical setup will start.

then I launch administator/client from a windows box

james

---

