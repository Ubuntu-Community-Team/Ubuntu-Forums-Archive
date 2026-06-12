---
title: "Cronjob not working..."
date: 2008-12-12
forum: Server Platforms
---

### Post by mrdek11 on 2008-12-12
Hi There! I'm having a problem and I was hoping somebody could please help me.
I'm running Ubuntu Hardy Heron Server Edition.
In /etc/crontab, I have the following job:
```
* * * * * root bash /home/arcemu/server/bin/rrestarter.sh
```

The contents of /home/arcemu/server/bin/rrestarter.sh:
```
#!/bin/sh
cd /home/arcemu/server/bin/
pidof arcemu-world
PID1=$?
if [ $PID1 -eq 1 ]
    then
    /home/arcemu/server/bin/arcemu-world
# I've tried ./home/arcemu/server/bin/arcemu-world here too
fi

```

I can manually run ```
bash /home/arcemu/server/bin/rrestarter.sh
``` from the command prompt, and it works just fine.

However, it refuses to run on its own. All my other cronjobs are working, so it's not a cron problem, I don't think.
Perhaps pidof doesn't work from a cronjob? Is there a better way to do this?
All I want/need it to do is to start arcemu-world if it's not already running.

Thanks in advance and best regards,
 Derek

---

### Post by hrod beraht on 2008-12-12
> **mrdek11 said:**
> In /etc/crontab, I have the following job:
```
* * * * * root bash /home/arcemu/server/bin/rrestarter.sh
```


What's that **root** part of the command? If you're trying to run the script as root, the script should be in the root crontab.

Bob

---

### Post by mrdek11 on 2008-12-12
Thanks, I tried putting it in the root crontab without the user part of the cron call
```
* * * * * bash /home/arcemu/server/bin/rrestarter.sh

```
but it still doesn't work.
I actually managed to catch the pidof call using ps ux, so I know that the job is getting that far. But for some reason it doesn't run the rest.

---

### Post by ajgreeny on 2008-12-12
I don't know much about a server install, but do you actually need the word bash in the cron command.  usually a shell script will run without problem if you just specify the full pathway to it in the cron command.  As an example a cron job I have run in the past was the following shell script called *radiorecord.sh*
```
#!/bin/bash
/usr/bin/streamripper full.http.url -options
```This was made executable and that script ran from cron with no problem.  I was doing it on a gui install of ubuntu, but surely the principle is the same; streamripper is a console application, not a gui one.

---

### Post by Toet on 2008-12-12
As far as I know a cron job should not contain a . (dot)

If you change the jobname by removing the .sh from the file name it should work.

---

### Post by Dr Small on 2008-12-12
Give the script executable permissions:
```
sudo chmod +x /home/arcemu/server/bin/rrestarter.sh
```

And then make your crontab to say:
```
* * * * * /home/arcemu/server/bin/rrestarter.sh
```

---

### Post by sprouty on 2008-12-12
Hi,

It might be worth putting you'r crontab out to a logfile so you can see what erroe message you get:

```
* * * * * /home/arcemu/server/bin/rrestarter.sh >>/home/arcemu/server/bin/rrestarter.log 2>&1
```

I got a feeling that you're problem may lie in "pidof arcemu-world", although i've never used this feature/program before i got i feeling you may need to put a full path of "pidof". anyway the logfile should tell you.

If you still having problems post the logfile

Hope This help,
Sprouty

---

### Post by Wayne_V on 2008-12-12
/etc/crontab is the system wide crontab and it does require an entry like:

# m h dom mon dow user    command

Normal user crontabs require only:

# m h  dom mon dow   command

If you are using /etc/crontab change it to this:

* * * * * root /home/arcemu/server/bin/rrestarter.sh
and then make sure to


$ sudo chmod +x /home/arcemu/server/bin/rrestarter.sh 
If it doesn't work, try adding these two lines to the beginning of rrestarter.sh - it should give you some 
idea of what is wrong (in the file 'debug-output'):

set -x
exec 1>debug-output 2>&1

---

