---
title: "autmysqlbackup file permission problems"
date: 2013-12-02
forum: Server Platforms
---

### Post by pdcooper on 2013-12-02
I'm trying to tie together automysqlbackup (bash  script to backup DB) and lftp (program to send the backups offsite). So i  want to make the files world-readable  so lftp can read them and copy  them

the script creates directories that are 755 and files that are 700. 
eg
 
~$ ls -l /usr/local/automysqlbackup/daily/ | grep test
drwxr-xr-x 2 root root 4096 Dec  2 16:44 test

~$ ls -l /usr/local/automysqlbackup/daily/test 
total 4
-rw------- 1 root root 560 Dec  2 16:44 test_2013-12-02_16h44m.Monday.sql.gz

 so i change the permissions 
acer@Acer-Aspire:/usr/local$ sudo chmod -R 644 /usr/local/automysqlbackup/
[sudo] password for acer: 

but i then cant read the files as user 
acer@Acer-Aspire:/usr/local$ ls -l /usr/local/automysqlbackup/daily/test 
ls: cannot access /usr/local/automysqlbackup/daily/test: Permission denied

but the permissions have been changed 

acer@Acer-Aspire:/usr/local$ sudo ls -l /usr/local/automysqlbackup/daily/test 
total 4
-rw-r--r-- 1 root root 560 Dec  2 16:44 test_2013-12-02_16h44m.Monday.sql.gz

so what am i doing wrong ? 
(the other way would be to create a backup group, add the user lftp is running under  and change group permissions, but that might not work  either)

---

### Post by steeldriver on 2013-12-02
In Linux/Unix, the action of *opening *a directory is considered to be equivalent to *executing *it - by changing the directory permissions to 644 you have removed all execute permissions so nobody can open the directories to see the files inside

---

