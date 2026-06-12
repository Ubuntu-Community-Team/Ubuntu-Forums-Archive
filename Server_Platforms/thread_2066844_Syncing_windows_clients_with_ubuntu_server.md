---
title: "Syncing windows clients with ubuntu server"
date: 2012-10-05
forum: Server Platforms
---

### Post by BuriBuster on 2012-10-05
Hello,
I've got following situation: I have 1 private server (running ubuntu 12.04) and several windows (7,XP) clients. What i try to acomplish is to have number of users that have shared folder over all their computers and that folders have automatic revision controls. This should be done over WAN. I have setup No-IP account (DynDNS alternative), so static ip is not a problem.

Simply put, i want few computers to sync data /data/share/user1, another two computers save to /data/share/user2 and so on. And whole folder /data/share should have automatic version control / backup (incremental with possible full backup).

Sync and backup doesn't need to be live, once an hour or so will do the job, but it has to be automatic since users won't spend time on manualy syncing their folders.

So far i tried Bacula, which i didn't manage to get working, fwbackups, which aren't working with Win 7 x64 and now I'm trying rsync for windows. Can anyone point me if I'm going in right direction or if should i try another program? Thanks in advance.

---

### Post by markbl on 2012-10-05
Not sure of what you are doing but install the free deltacopy (windows rsync server) on each of the windows clients and then run [rsnapshot](http://www.rsnapshot.org/) each hour from cron on your ubuntu server to pull the data. Rsnapshot is in the standard packages.

---

### Post by BuriBuster on 2012-10-06
Thnx. As for syncing I've managed to get up and running iFolder. Works good so far. I'll definetely look onto rsnapshot, thanks for the tip.

---

### Post by albandy on 2012-10-06
check amanda backup. Is a very good backup system. In my company we use it to backup over 500 workstations.

[www.amanda.org](www.amanda.org)

---

