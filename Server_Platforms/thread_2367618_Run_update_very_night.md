---
title: "Run update very night"
date: 2017-08-01
forum: Server Platforms
---

### Post by cazz on 2017-08-01
Do I have to create a bash and crontab to make my system run update every night or is that any build inside?

I remember when I did install it ask if I want to have auto update for the system but I did say no.

Like it to run a specific time at night

---

### Post by #&amp;thj^% on 2017-08-01
> cron-apt method

This method is for people who have installed a cut-down, customised or server version of Ubuntu. If you have installed the full desktop version of Ubuntu, updates are automatically handled by the GUI method described above. There is no need to install cron-apt yourself if you are running the full desktop version of Ubuntu. But the whole point of Linux and open source software is that you can customise it, right?

The package cron-apt is designed to automatically update the package list and download upgraded packages. Therefore it basically calls the command 
See this: [https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)
By default, cron-apt will execute automatically at 4am.

---

### Post by cazz on 2017-08-01
ahh thanks, well 4am is ok with me.

---

### Post by TheFu on 2017-08-03
I would recommend caution in doing automatic updates.  I've been burned a few times and left with non-working systems.  

Automatic security patching is a different thing. I don't do it either, but many organizations do.

Plus, you still need to manually reboot after some updates, so be certain to check for that too.

I find it best to patch weekly, usually early on Saturday mornings, so I have time to fix issues that sometimes arise.  Once, the update process removed the DBMS completely so any dependencies were also removed.  It was a bad day here.  I will NEVER automatically patch again.

---

### Post by cazz on 2017-08-03
mmm have think about that too so I think I wait and see.

---

