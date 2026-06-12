---
title: "Backup Fails when run with cron"
date: 2006-08-02
forum: Server Platforms
---

### Post by charlie. on 2006-08-02
I have a backup script that compresses some files, dumps a mysql database and then pushes the result across the network using SMBCLIENT. The script is rather primitive. Here's an abridged version:

```
tar --totals --verbose --index-file=tar-log \
    -cjf my-files -C $source_dir /var/www/my-web
mysqldump my-db --routines > my-data-backup
smbclient \\servername\\share -Uwindowsuser%windowspass -c"
    mkdir \"insertdatehere\";
    cd \"insertdatehere\";
    put \"tar-log\";
    put \"my-files\";
    put \"my-data-backup\";
"
```

I add this to the "backup" user's crontab using:
```
sudo crontab -eu backup
```

... and adding the line:
```
50 22 * * * /var/backups/my-web-temp/my-backup-script >> /var/backups/my-web-temp/log
```

This script runs perfectly when I run it as "root", using sudo. It runs perfectly when I run it as myself.

I tried running it as "backup" using the commands:
```
sudo -u backup -i
./my-backup-script
```

... it runs beautifully - the output is identical to the output as myself or "root" and the files magically appear on my Windows server.

When it runs on the cron schedule, however, the output is not right - the sql script that comes out of mysqldump is about an eighth of the expected size. (100k instead of about 800k) Other than this, the files are tarred correctly and the data is correctly pushed across the network. The SQL script that is generated when this backup runs on the cron schedule does include valid SQL - clearly not the whole database, however.

I have checked that the cron job does run as the "backup" user. The "backup" user group (of which "backup" is a member) has full access to the temporary directory in which the backups are prepared. (/var/backups/my-web-temp) I have checked that the "backup" user does have the necessary permissions on the MySql databases (SELECT and LOCK TABLES on the database, SELECT on `mysql`.`proc`) but I do not believe that to be the reason anyway - it worked when I impersonated "backup" using the -u switch for sudo. I have also checked that the cron job is running the identical script.

This is a most confusing problem. I cannot figure out what I might have missed. Why would the job run when I impersonate "backup" with sudo but not run on "backup"'s crontab?

Please help!

---

### Post by apjone on 2006-08-02
try 
su - backup

and then 
crontab -e

---

### Post by charlie. on 2006-08-07
The "backup" use has no password, so "su" is not very usefull. I can, however, use...

```
sudo -u backup -i
```

... to get an interactive session as "backup".

I did this and used...

```
crontab -l
```

... to list the cron table. It is listed exactly as I entered it.

I could have told you this even without checking. Please read the third last article of my original post, which states that the backup job DOES run on the cron schedule and only the output from mysqldump is incorrect!

Thanks anyway.

---

### Post by charlie. on 2006-08-08
Further investigation reveals that this is definitely a problem with mysqldump, not any other tools used by the script. I am, however, no close to a solution.

Please help!

---

### Post by charlie. on 2006-08-11
BUMP... I&#8217;m really desperate on this one!

---

### Post by linuxone on 2006-08-12
Hi,

> **charlie. said:**
> Further investigation reveals that this is definitely a problem with mysqldump, not any other tools used by the script. I am, however, no close to a solution.

the shell in which your script is running misses the bash environment. Due to this the PATH settings were unknown, so the script doesn't now where your programs could be found.

Solution for your problem is real simple: add the complete path to all your commands. Instead of "mysqldump" write "/usr/bin/mysqldum", same to all other commands, and your script should work correctly.

Thomas

---

### Post by charlie. on 2006-08-14
Thanks for the suggestion, but it did not help. I do not think that the paths are a problem because the backup file is not empty when the script runs with cron, it's just not complete.

I performed some more tests:

Here's a statement to backup my database:

```
mysqldump mydatabase --routines > /var/backups/test.sql
```

If I run this as root....

```
sudo mysqldump mydatabase --routines > /var/backups/test.sql
```

.... the backup comes out complete, at 833k.

If I run this as "backup", using sudo, not interactive....

```
sudo -u backup mysqldump mydatabase --routines > /var/backups/test.sql
```

... I get ....

```
-bash: /var/backups/test.sql: Permission denied
```

... *blink* .... BUT, if I run it as "backup", using sudo in interactive mode...

```
sudo -u backup -i
mysqldump mydatabase --routines > /var/backups/test.sql
```

... it works perfectly and a complete file is created: 833k.

If I schedule the same command on the crontab for "backup", by...

```
sudo crontab -eu backup
```

... and adding ...

```
* * * * * mysqldump mydatabase --routines > /var/backups/test.sql
```

... and waiting for a few minutes, the backup file is created correctly, but it is not complete - it ends before all the tables have been dumped, at about 154k.

This raises two questsion. Firstly, why does the identical command fail if it is run with sudo in non-interactive mode, but succeed with sudo in interactive mode? (I checked that the same username was passed to the -u switch)

Secondly, back to the original question, why does the identical command result in different output when run by cron?

I thought that I might have put the line on the wrong crontab, so I added a line that pipes the output from "whoami" to a text file. This line is on the same crontab and, you guessed it, reading the textfile returns: "backup".

Now I am really confused. Please help!

---

### Post by charlie. on 2006-08-17
Here's an update:

I have tried running my script on my own crontab. The script backs up correctly and produces a complete backup file. This is a temporary solution to the problem, but it does not answer the big question:

**THE BIG QUESTION:**
The fact that the script works when running on my own crontab leads me to believe that this whole issue is related to permissions granted to the backup@localhost user within MySql. If so, why does the script run correctly for "backup" when impersonated with sudo? Additionally, if the permissions are set incorrectly, why do I get partial output from mysqldump? I would expect a completely blank file if the permissions were wrong!

As a matter of interest, what permissions are required to use mysqldump? I have...

```

GRANT SELECT, LOCK TABLES ON thedatabase.* to backup@localhost;
GRANT SELECT ON mysql.proc to backup@localhost; -- for routines

```

What's wrong with that?

---

### Post by chonger on 2006-08-17
When you run sudo using non-interactive mode and tries to redirect the output to a file. The file get created using your own id. That is, because of the way you wrote the command, the redirect and the command executed by "sudo" is separate. Only the command is executed by the backup user, the redirect that writes to the file gets executed by you.

Some examples:

```
sudo -u root echo foo > /tmp/output
```

This command is saying, execute "echo foo" as root, then take that output and save it in /tmp/output using your own id.

To include the redirect as a part of the "sudo-ness", you will need to rewrite the command like this.

```
sudo -u root bash -c "echo foo > /tmp/output"
```

This says execute "echo foo > /tmp/output" as root. I needed to do some hacking to get this to work, so it is not pretty. But I think it illustrates the point.

Or if you put your entire in a script, called 'foo.sh', then you can call. 

```
sudo -u foo.sh
```

---

### Post by charlie. on 2006-08-18
Thanks, chonger. You've answered question 1 from reply 7. Your answer makes perfect sense.

There's only one remaining question now: why does it fail with cron?

---

### Post by Bil-E-daKid on 2006-11-24
Hey charlie,

Did you ever find an answer to this perplexing thing? I'm having a similar problem (though just using tar and not mysqldump).

:-)

---

### Post by charlie. on 2006-11-24
My solution was to kick MySql in favour of PostgreSQL, which has proven to be more stable on all fronts.

I'm sorry I can be of no help.

---

