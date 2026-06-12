---
title: "Automatic upload script with cron"
date: 2007-10-04
forum: Server Platforms
---

### Post by xnxcom on 2007-10-04
Hello all .. i'm a newbie. 
i'm work in 2 server, production server and real server. Everyday i'm work at production server do some scripting with PHP .. but at end of day i should upload my work to real server. 

i want create a automatic process to upload my work to real server with cron, but this scipt can check file has been modified or not. 

Any one know how to do it .. ? 
Thank You

---

### Post by conjur3r on 2007-10-04
Use a program called rsync to synchronize changed files/folders across the two servers.  I think it is preinstalled.  If not you can add it quite simply with apt-get install rsync.

You may need a little bit of work to get it to run without intervention.  This will most likely invlove some form of SSH key.

---

### Post by netlogic on 2007-10-05
rsync over ssh to keep source file in insync with the destination 
> rsync -ave ssh --delete server:/home/you/public_html /home/bob/servercp
or reverse destination and source based on your need.

---

