---
title: "Backup Cronjob"
date: 2010-10-05
forum: Server Platforms
---

### Post by exeTrix on 2010-10-05
Hi Guys.

I'm kinda new to *NIX based systems and have been struggling to setup a cron job on my VPS. Basically, I have setup MySQL replication via a stunnel wrapper to a slave MySQL server which is working great! I did this so I can backup from the slave to reduce load on the master. So in order for the backups to take place I have written my first bash script (probably sucks) and what i was thinking about doing was add this into cron to run @ midnight every night. I thought it'd be good house keeping to create a user called backup for the job to run under. After doing this I moved the script I've written to /home/backup/bin then used crontab -u backup -e and added the following:

```
* * * * * /home/backup/bin/backup
```**Note: **I realise that this will run every minute and I did this for testing purposes.

But the job fails to run I have checked the logs (/var/log/syslog) where there is no mention of the backup users cron even running... even though I can see the backup users cron being edited and reloaded. I then enabled cron logging via syslog, restarted syslog and saw the same in /var/log/logcron.log. 

After extensive reading on the internet I have found that environments can cause issues similar to this but how can environments affect this when i have included a fully qualified file path to my script?

One other thing that is worth mentioning is that the permissions are fine backup user has rwx!

Here's the script just in case it's something to do with that:

```

#!/bin/bash

# Wriiten by Craig for MySQL Dump cronjob


## Constants

DATE_NOW=$(date +"%d%m%Y")
BACKUP_PATH="/home/backup/backups"

## Functions

function get_dump
{

mysqldump -u dumper -p password -h 127.0.0.1 db > $BACKUP_PATH/tmp/db-$DATE_NOW

echo "Dump Created"

}

function tar_dump
{

mkdir $BACKUP_PATH/tar/$DATE_NOW

echo "Folder Created"

tar -cvzf $BACKUP_PATH/tar/$DATE_NOW/db-$DATE_NOW.tar.gz -C $BACKUP_PATH tmp/db-$DATE_NOW

echo "Archive Created"

}

function remove_dump
{

rm $BACKUP_PATH/tmp/db-$DATE_NOW

echo "Cleaned tmp Directory"

}

### Code

get_dump

tar_dump

remove_dump


```Any help would be greatly appreciated.

Thanks

---

### Post by CharlesA on 2010-10-05
I've actually not had much success with adding entries to cron using -u username, but that could just be me.

Try redirecting the output to a file and see if it's spitting out any errors.

Add this to the end of the entry in the crontab:

```
>> /path/to/some/file 2&>1
```

---

### Post by exeTrix on 2010-10-05
Thanks for your speedy response! I have just tried you suggestion and nothing appears to have happened. I have added the output file to cron then touched the output file. Still nothing though (file is empty)... I have realised that there is no cron.allow deny files within /etc/. Would this cause that to happen? All the jobs that are setup appear to be within /etc/cron.daily etc. Maybe my VPS host has disabled user based cron jobs? How would I check this?

Hope that helps.

---

### Post by CharlesA on 2010-10-05
Hrm.

If there aren't any error messages, that should mean that it ran successfully.

Try adding this to the end of each function:

```
&& echo "Whatever command Completed successfully" >> /path/to/some/file
```

So it would look like this:
```
mysqldump -u dumper -p password -h 127.0.0.1 db > $BACKUP_PATH/tmp/db-$DATE_NOW && echo "Whatever command Completed successfully" >> /path/to/some/file
```

---

### Post by exeTrix on 2010-10-05
Many thanks for your suggestions. Still the same issue... cron just doesn't appear to be running the job. I really don't understand why. I tried changing the path of the call to mysqldump to /usr/bin/mysqldump (FQP) within the script but that makes no difference. I tried running the script manually and the output gets printed in the log file as you would expect. It's like cron is either not allowing the user to run cron jobs or is being affected by some security setting?

I have tried running the script under root and I get the same problem. No errors, no log entries to even say the command has been run. To be sure that it wasn't a problem with the environment within the script, I have also tried running /usr/bin/mysqldump blah blah directly within crontab -e... still nothing. 

This makes no sense :( 

Thanks.

:guitar: <-- no sure why I added that just thought it was quite funny :D

---

### Post by CharlesA on 2010-10-05
Well I guess what you could do is set up a MTA for local mail to see if cron is actually running the job or not, since cron will mail you a message if it completes or not.

---

### Post by exeTrix on 2010-10-05
After extensively bashing my head against my desk, in midst of the haze of concussion I decided to login to this pile of turd web interface known as Plesk for the first time on my VPS. Apparently *"It allows you to control all aspects of your server, including DNS,  virtual hosts, cron jobs, scheduled tasks, web services, scripting  software, statistics and more". *Anyway, it was Plesk that was causing the issue... I went into cronjobs and saw the task clicked on it then clicked save and it worked. I know that this isn't related to Ubuntu in any way shape or form but I wanted to post the fix just in case anybody else has the misfortune of having Plesk installed on their VPS out of the box but wants use a command line interface so they actually learn something!

Thanks for your help CharlesA and I'm sorry to have wasted your time.

---

### Post by Vegan on 2010-10-05
to get you script to work do the following

chmod 777 myscript
chown root:root myscript
ln myscript /etc/cron.daily 

change the cron.daily to hourly or however often your script needs to run

More headaches than needed with permissions to run scripts. Making the script root's means its got no worry doing whatever it needs to.

---

### Post by CharlesA on 2010-10-05
Glad you got it working. Don't forget to mark the thread as solved. :)

---

### Post by exeTrix on 2010-10-06
> **Vegan said:**
> to get you script to work do the following

chmod 777 myscript
chown root:root myscript
ln myscript /etc/cron.daily 

change the cron.daily to hourly or however often your script needs to run

More headaches than needed with permissions to run scripts. Making the script root's means its got no worry doing whatever it needs to.

Hi Vegan,

The only problem that I can see with this though is that if you were to set owner and group to root and chmod 777 that means that your script is world writable and is owned by a super user... to me this seems extremely insecure. Surely chmod 700 would suffice? If that didn't work then maybe cron is running under a user so find out what that user is and chown to match.

Personally I avoid chmod 777 like the plague even during testing.

---

### Post by Vegan on 2010-10-06
My backup script would not run until I chown'd and chmod'd it.

I realize that 777 is not he most secure, but my script is in my home director and its safe there.

At least now my SQL database is backed up, and my web folder is also backed up.

---

