---
title: "Automatic DDclient updating - or similar"
date: 2008-03-18
forum: Server Platforms
---

### Post by jayashleysmith on 2008-03-18
Ok I run a wb server in my bedroom ([www.destinywebserver.org.uk](www.destinywebserver.org.uk)) which is setup as a scp ssh http apache server. I have dyndns accout setup and its all working, i can ssh i can view websites transfer files etc. But ....

When my Internet IP changes obiously my dyndns ip address is incorrecct, so i need to use something like ddclient. 

I installed ddclient added all my infomation to /etc/ddclient.conf 

But I now need it to be setup on automatic updateing. This is what i need help doing. 

Any help would be great! 

JAS

PS. great step by step detail needed as im fairly new to linux distro and also only 14!

---

### Post by smileypaul on 2008-03-19
You can run it as a cron job.

sudo gedit /etc/crontab

add this to the bottom

#This section added by me, runs ddclient at 1pm, and 1am.
00 01,13 * * *  root    /usr/sbin/ddclient

save the file.

call it a day.

You can change the timing as necessary, but if you're on the free account, too many updates is considered abuse.

---

