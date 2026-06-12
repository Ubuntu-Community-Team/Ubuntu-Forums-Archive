---
title: "USB Flash drive backup - www-data and access to /media"
date: 2012-12-08
forum: Ubuntu Dev Link Forum
---

### Post by mattcall on 2012-12-08
Hello all,

First ever post on any forum so apologies in advance for any newbie errors or poor etiquette.

I am in the process developing a Ubuntu / Chrome (PHP,mysql) based kiosk application. One of the requirements is to do daily backups of the database to a USB Flash Drive. I have this working on a Windows dev system however I have hit a problem under Linux with my poor knowledge of the OS.

I cannot figure out how to (if indeed it is possible) allow the web server access to write to the the attached USB drive? From my understanding this runs as user www-data, do I need to add this user to a Group or edit permissions somewhere?

Any thoughts or advice greatly appreciated.

---

### Post by irv on 2012-12-08
What version of Ubuntu are you running? And can you just use Backup under system settings. You can setup what you want to backup, where to backup to, and how often.
[ATTACH]228386[/ATTACH]

---

### Post by mattcall on 2012-12-09
Hi irv,

Thanks for the reply...I'm using 12.04 LTS. I'm dumping some mySQL tables in full along with parts of other tables dependant on some logic direct from PHP so I don't think backup will do it no. 

Basically need full access to the Flash Drive.

---

### Post by irv on 2012-12-09
I am not into scripting but I know there is a way to do this with a simple script. The information you will need to know is the USB id. When I plug in a USB the partition info is /dev/sdb1. If I use gparted this is the information on my USB drive.
[ATTACH]228441[/ATTACH]
Maybe someone can help with a script file to do this.

---

