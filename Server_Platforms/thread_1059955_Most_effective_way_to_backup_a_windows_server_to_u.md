---
title: "Most effective way to backup a windows server to ubuntu server?"
date: 2009-02-04
forum: Server Platforms
---

### Post by okpgreg on 2009-02-04
We currently have an Ubuntu server that we use as a backup for several servers.  However recently we, unfortunately, had to add a Windows amazon instance to our server lineup as well.  I have windows and sql server backing everything up on the instance, but I can't figure out the most effective way to get everything to the linux box.  Is it cygwin and rsync?  We use backupninja w/ rsync & ssh on all the linux servers at the moment. Does anyone have any other suggestions?

---

### Post by koenn on 2009-02-04
DeltaCopy : rsync for Windows
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

there are a couple of threads about it already, discussion different options on how to rsync between a windows and a linux host.

What you probably want is run Deltacopy as a service on windows, so you can initiate rsync from your backup server (and keep everything neatly centralized)

---

