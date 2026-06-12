---
title: "making mirror copy of HDD"
date: 2011-10-11
forum: Security
---

### Post by bestbg on 2011-10-11
Hello , 
i`m a newbie with Ubuntu. I`ve read a lot , but i can`t find my "problem".
I have 3 SATA HDD. On the first one i`ve install ubuntu Server11.04 ( and download after that GNOME) , second one is with my information. I want when someone of the group working with the second the third one makes a copy and update all info from the second.

Sorry if you can`t understand me , but my English is not very good. And sorry if the topic is not for this SubForum.

---

### Post by Lars Noodén on 2011-10-11
One way of making a mirror copy is to set the two drives up as [RAID 1](http://www.pcguide.com/ref/hdd/perf/raid/levels/singleLevel1-c.html)

Or if you do not set up raid, you can have [cron](http://manpages.ubuntu.com/manpages/natty/en/man5/crontab.5.html) run [rsync](http://manpages.ubuntu.com/manpages/natty/en/man1/rsync.1.html) at regular intervals.

---

### Post by bestbg on 2011-10-11
i `ve download grsync and strated to copy from one to other HDD. How i can  make it to update every day the infromation , because i can`t see in the option? or should i make comands in terminal?

---

### Post by Lars Noodén on 2011-10-11
> **bestbg said:**
>  How i can  make it to update every day the infromation , because i can`t see in the option? or should i make comands in terminal?

Ultimately it is useful to learn how to do things in the terminal. 

However, if you would like a graphical front-end to cron, then you can use [gnome-schedule](http://manpages.ubuntu.com/manpages/natty/en/man1/gnome-schedule.1.html) or kcron.

---

### Post by dirtrider1 on 2011-10-11
There is also the program DD which will completely image a hard drive. [http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

---

