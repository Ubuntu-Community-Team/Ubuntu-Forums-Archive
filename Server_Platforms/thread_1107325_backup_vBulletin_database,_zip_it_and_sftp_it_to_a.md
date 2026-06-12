---
title: "backup vBulletin database, zip it and sftp it to a remote server?"
date: 2009-03-26
forum: Server Platforms
---

### Post by theRick on 2009-03-26
I'm hoping someone can hold my hand on this one...

I've got a vBulletin forum with database that is about 2gig right now and we don't have a very good backup regimen... I have a calendar reminder to jump in once a month, dump the database, zip it and sftp it to my home server... that's about it...

What I'd love to have is an automated process that does exactly this once a week and overwrites the existing backup.

How could I accomplish that?

---

### Post by Xiong Chiamiov on 2009-03-27
Write a bash script with the exact same commands as you use.  Keep in mind that it will run as root, and the $PATH may not be set the same as for your user.  Then dump it into cron.weekly.

---

### Post by hyper_ch on 2009-03-27
and don't copy the binary database files. They could become corrupted if you start copying and some change was commited. use mysqldump instead.

---

### Post by theRick on 2009-03-28
Thank you for the assistance!

I have never used a bash script before and so I am getting stuck... Here is what I've come up with so far...

```
rickpass="PASSWORD"
mysqldump --opt -Q -u utopia -pPASSWORD utopia_forum > /home/webmaster/database-backups/UtopiaWeeklyRemoteDUMP.SQL
tar -czpf /home/webmaster/database-backups/UtopiaWeeklyRemoteDUMP.tar.gz /home/webmaster/database-backups/UtopiaWeeklyRemoteDUMP.SQL
sftp USER@rick.is-a-geek.com
echo $rickpass
cd /media/filestorage/utopiabackup
put /home/webmaster/database-backups/UtopiaWeeklyRemoteDUMP.tar.gz
quit
```

I'm doing ok until I get to the sftp section of the code... It connects to my remote server but it doesn't pass the password.

How do I get sftp to accept the password and then put the file?

---

### Post by hyper_ch on 2009-03-28
if you do a keybased authorization then it shouldn't ask for a password.

local --> the computer where you run the mysqldump
server --> the computer where you want to put the backup file to
user --> the user that you login to onto the server

(1) create a key on the local
```

ssh-keygen -t dsa

```

(2) add the key to the server
```

cat ~/.ssh/id_dsa.pub | ssh -l user server 'cat && ~/.ssh/authorized_keys'

```

(3) check if you can login:
```

ssh user@server

```

if that works, then you should be able to just issue this command:

```

scp /path/to/mysqldump.tar.gz user@server:/home/user/data-base-backups/mysqldump.tar.gz

```
of course change the above path and names to your liking.

---

