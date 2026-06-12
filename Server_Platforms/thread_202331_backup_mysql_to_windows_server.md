---
title: "backup mysql to windows server"
date: 2006-06-23
forum: Server Platforms
---

### Post by binks on 2006-06-23
i need for my server to be able to back up all the db's in mysql (ubuntu server) and back them up on a daily basis accross my lan and onto my windows 2003 server as this will then get backed up onto tape,
i have read a little about cron how could i achieve this .
thanks binks

---

### Post by lamego on 2006-06-23
You can easily achieve this by install the mysql client programs on your Windows 2003 box, then create a batch file to use mysqldump and dump the database to a local file.
Add a windows task to run this batch, make sure the file is going to the tape and it is done.

---

### Post by houstonbofh on 2006-06-25
You could also add a share on the windows server to your "Ubuntu Places" and automount it.  Then you can use cron and mysql client software to export the DB to there.

---

