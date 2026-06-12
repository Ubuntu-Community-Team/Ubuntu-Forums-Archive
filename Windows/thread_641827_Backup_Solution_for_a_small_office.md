---
title: "Backup Solution for a small office?"
date: 2007-12-15
forum: Windows
---

### Post by monkeymartin on 2007-12-15
what do you use for a small office (20 computers) backup solution.  


I am looking at these solutions 

[http://www.dailycupoftech.com/windows-backup-with-rsync-and-freenas/4/](http://www.dailycupoftech.com/windows-backup-with-rsync-and-freenas/4/)
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)
[http://ping.windowsdream.com/ping.html](http://ping.windowsdream.com/ping.html)
[B]
This one looks really good for windows XP machines [/B] 
[http://freeghost.no-ip.org/index.php?option=com_frontpage&Itemid=1](http://freeghost.no-ip.org/index.php?option=com_frontpage&Itemid=1)

I really like the idea of cloning Computers because it is very easy to restore the entire system.  I all so like rsync because it only copies files that change.  

what do you think.  Any sugestions would be great.  

Thanks for your time

---

### Post by Sef on 2007-12-16
> This one looks really good for windows XP machines
[http://freeghost.no-ip.org/index.php...tpage&Itemid=1](http://freeghost.no-ip.org/index.php...tpage&Itemid=1)

It does, but it is still beta software.

My preference from the top three is [Ping]("http://ping.windowsdream.com/ping.html").

---

### Post by cyclefiend2000 on 2007-12-16
does you server OS have to be windows?

we are using sme server at our office. we have two servers really. one is only a backup though. the main machine (tux) is available to everyone in the office. the backup (putt) cannot be seen by any user. there is an rsync every 10 or 15 minutes (i forget which). so if tux goes down we at most lose 15 minutes worth of data, and putt can be up and running in place of tux in about 10 minutes.

---

### Post by garret on 2007-12-17
[http://restore.holonyx.com](http://restore.holonyx.com)

---

### Post by rickyjones on 2007-12-17
Well, what is your network layout? What data do you wish to backup?

You probably don't want to backup all files on every single computer... that is just a waste. You most likely only want to backup the user files, documents, and program data files.

Are you running Windows Server 2003 and Windows XP Professional for the workstations? If so, you could do what a lot of small offices do. Redirect the My Documents folder for each user to a folder on the server. Use a filesync program to backup required individual files/folders on workstations to folders on the server. Then use some form of backup system on the server to backup straight from the server. I personally use USB hard drives and the built in Windows Backup program.

-Richard

---

