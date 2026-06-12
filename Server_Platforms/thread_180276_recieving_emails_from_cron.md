---
title: "recieving emails from cron"
date: 2006-05-21
forum: Server Platforms
---

### Post by peanut butter on 2006-05-21
every 20 min or so i get the folloowing message to my account on my server:

  PINE 4.64   MESSAGE TEXT                                                                         Folder: INBOX  Message 132 of 685 ALL NEW

Date: Sun, 14 May 2006 05:40:01 -0700 (PDT)
From: Cron Daemon <root@paulhost.net>
To: [email]root@paulhost.net[/email]
Subject: Cron <smmsp@sparkie> test -x /usr/share/sendmail/sendmail && /usr/share/sendmail/sendmail cron-msp

/usr/share/sendmail/sendmail: line 820: /usr/sbin/sendmail-msp: No such file or directory

i had installed sendmail but have uninstalled it
how can i get theese to stop.

---

### Post by Iowan on 2006-05-22
[QUOTE=peanut butter]
how can i get theese to stop.[/QUOTE]Check the crontab files and eliminate the offending line?
[https://wiki.ubuntu.com/CronHowto]("https://wiki.ubuntu.com/CronHowto")

---

### Post by peanut butter on 2006-05-23
sorry for the late reply. i cant seem to find anything about sendmail in any of the cron files maby im missing something.

---

### Post by peanut butter on 2006-05-23
[QUOTE=peanut butter]sorry for the late reply. i cant seem to find anything about sendmail in any of the cron files maby im missing something.[/QUOTE]

sorry. i found a file in a cron directory called sendmail so hopefully thats it.:)

---

