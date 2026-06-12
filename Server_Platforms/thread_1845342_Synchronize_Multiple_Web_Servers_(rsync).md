---
title: "Synchronize Multiple Web Servers (rsync?)"
date: 2011-09-16
forum: Server Platforms
---

### Post by tts5 on 2011-09-16
I have a clustered Ubuntu server layout that looks like this:

Server A - Web Server (Primary)
Server B - Web Server (Secondary)
Server C - Database Server (Master)
Server D - Database Server (Slave)
Server E - Load Balancer
Server F - Load Balancer
Multiple web sites are hosted on Server A in each users /home/$name/public_html directory (e.g. /home/aaa/public_html, /home/bbb/public_html, etc.).

For the Load Balancer (Servers E/F) to function properly, Server A's /home directory (where files are stored) must always be in sync with Server B's /home directory.

Is the best way to implement this using rsync? If so, how do people set that up? I found a few websites on the subject -- none of them were very detailed.

---

### Post by Dangertux on 2011-09-16
Personally I would say just create a script to rsync the two server's and set it as a cron job. 

That seems like the most straight forward way to do it.

This gives a pretty simple breakdown of using it (its a copy of the man page)

[http://ss64.com/bash/rsync.html](http://ss64.com/bash/rsync.html)

---

