---
title: "Automated Backup Suggestions"
date: 2012-02-10
forum: Server Platforms
---

### Post by DanHorniblow on 2012-02-10
Hi, I have a VPS running Ubuntu 10.04 and I want to backup "/var/www/" and "/var/vmail" plus all MySQL databses.

Any sugestions?

---

### Post by bubylou on 2012-02-10
Where will you be placing the backup files. Writing a script and automating it with cron would be a simple and effective way of doing backups. Try [this]("https://help.ubuntu.com/11.10/serverguide/C/backups.html") to get you started. I personally just use [rsync]("http://ss64.com/bash/rsync.html") to backup my server to another host on my network.

---

### Post by SeijiSensei on 2012-02-12
[Sample MySQL Backup Script]("http://ubuntuforums.org/showpost.php?p=10368151&postcount=3")

If you want to create offsite copies, I'd add an rsync command to that script.

---

### Post by Cheesemill on 2012-02-13
I tend to use [rsnapshot]("http://rsnapshot.org/") and [automysqlbackup]("http://sourceforge.net/projects/automysqlbackup/") on my servers.

---

