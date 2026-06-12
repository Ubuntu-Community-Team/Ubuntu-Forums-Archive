---
title: "Ubuntu 12.04 - mysqldump: Got error: 1045: Access denied for user 'root'@'localhost'"
date: 2012-05-28
forum: Server Platforms
---

### Post by vavr on 2012-05-28
Hi @ all

I hava make a windows share folder which has been mount in mu 12.04 server.
i'm trying to to run a mysqldump commnad in order to backup my db and then if it works to make it work automatically via the crontab and from then directly to my server.

the command :
mysqldump -u root -pRootPassword --all-databases | gzip > /mnt/backup/MYSQL_Backup/DBname_`date '+%m-%d-%Y'`.sql.gz

and i am getting the error : 

Error : -bash: /mnt/backup/MYSQL_Backup/Nessus_05-28-2012.sql.gz: Permission denied
mysqldump: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect.



Any help plz?
thanks

---

### Post by LHammonds on 2012-05-28
Well, that looks like a file permission / access problem more than a mysqldump problem.

Type "whoami" to see what ID you are currently logged in as.

Then do "ls -l /mnt/backup" and make sure the ID has read/write access.

The next thing you want to do after you clean up your permission problem is to change how you are calling your mysqldump command.  You do NOT want to have your root ID / password exposed which it will be when the dump command is called via crontab.

You can create a my.cnf file to hold the password so that when you issue the mysqldump command, you do not need to issue the ID or password as part of the command.

For details on how to set this up, look in my sig for the MySQL server setup and see how I did it there.

LHammonds

---

### Post by d4m1r on 2012-05-28
1) Does the user you are using to connect to your mysql server have r/w/x permissions to ALL your DB's?

2) Does the user running the command/cron job have r/w/x permission to the location you specified the backup to save?

---

### Post by vavr on 2012-06-06
Hi again,

you were both right, i had to create a local user account in my windows machine in order to work.

But now the strange thing is that the command works perfect only when i first give sudo su and then the mysqldump command.

when i type sudo mysqldump... i get this error


  
  [FONT=&quot]username@server:~$ sudo mysqldump -u backupuser –pbackupuser --all-databases | gzip > /mnt/backup/MYSQL_Backup/Server_`date '+%m-%d-%Y'`.sql.gz[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]It returns that : -bash: /mnt/backup/MYSQL_Backup/Server_06-06-2012.sql.gz: Permission denied[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Add then it asks for password [/FONT]
  [FONT=&quot][sudo] password for Server:   (Then I type the password)[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]And I get this[/FONT]
  [FONT=&quot]mysqldump: Got errno 32 on write[/FONT]
  [FONT=&quot]username@server:~$[/FONT]

---

### Post by vavr on 2012-06-22
any help here?

thanks

---

### Post by Habitual on 2012-06-22
> **vavr said:**
> bash: /mnt/backup/MYSQL_Backup/Server_06-06-2012.sql.gz: Permission denied

Your linux user have permission to write to [FONT=&quot]/mnt/backup/MYSQL_Backup/ ?

open a terminal and type
[/FONT]```
sudo touch /mnt/backup/MYSQL_Backup/test

```report the success or failure of that command here please.

---

### Post by vavr on 2012-06-26
Hi,

i gave your command and it worked without errors... a test file created in the /mnt/backup/mysql... directory.

---

