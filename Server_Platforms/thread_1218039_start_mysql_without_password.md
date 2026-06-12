---
title: "start mysql without password"
date: 2009-07-20
forum: Server Platforms
---

### Post by jackel7007 on 2009-07-20
I want to use areca to make a copy of my mysql data folder.
In areca I can set a pre and an after command

The pre command would be to stop the mysql server
then the areca backup command would be to copy the entire mysql datafolder to another folder.

Then the aftercommand would be to start the mysql server.

Now normally to start the mysql server you need to sudo.
This brings allong that ou have to use your password.

My wish is to automate this completely, and I succeeded in so far that i can stop and copy the data. But I can't (re)start the mysql server without having to fill in my password.

I have been looking into adding mysql into sudoers but that didn't work so far.

Anybody has an idea?

---

### Post by Cheesemill on 2009-07-20
The prefered method of backing up a MySQL database is with the mysqldump command, not backing up the raw data files.

Or take a look at the AutoMySQLBackup script on sourceforge if you want incremental backups of all of your databases, you can run it from roots crontab on a daily basis.
[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

---

### Post by jackel7007 on 2009-07-20
I had already found autoMySQLBackup, but we would like to backup the raw data.
So is there any possibility to start mysql again without password questions?

---

### Post by Cheesemill on 2009-07-20
You can make a script to do your shutdown and startup and put it in roots crontab, this way it will run as root without asking for a password.

---

### Post by jackel7007 on 2009-07-20
sounds like a good idea, but...

The machine we are currently configuring is going to be our server, and were making it in such a way that after a power dip, the system reboots and everything continuous to run.
So in other words, the system will always be in the "nobody logged in" mode.

I already got areca so far to run in this mode, and also hamachi.
Does Crontab run when nobody is logged in?

---

### Post by Cheesemill on 2009-07-20
Yup. It sure does :)

---

### Post by jackel7007 on 2009-07-21
The problem left is that I use areca to stop the mysql server, then I create a raw backup copy.

After that the copy is done the mysqlserver should be started again.

Normally areca would run the after command directly when copying is done.
But since I'm running this restart commando from the root's cron, i believe i can't link it to areca.

So I will have to "estimate how long the backup will take, and then create a timerule in cron... 

So when something goes wrong, cron will be starting Mysql while it's copy is still being made. Is there Any way I can run this start script using areca after command?

---

