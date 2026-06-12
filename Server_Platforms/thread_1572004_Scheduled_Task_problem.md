---
title: "Scheduled Task problem"
date: 2010-09-10
forum: Server Platforms
---

### Post by xendistar on 2010-09-10
I am trying to get Scheduled Task to run a bash script (which runs an rsync command) but it does not seem to be running.

I can run the script from the command line with out a problem, but I have it scheduled in Scheduled Tasks to run once everyday and I can't find any evidence of it running or any indication why it does not run.

Can anyone give me any pointers or is there a better GUI for scheduling tasks?? 

I am running 10.04 server with xbuntu desktop

---

### Post by clrg on 2010-09-10
I recommend you don't use those fancy but unreliable GUI tools. Learn how to use crontab. If you already know how to set a job, just "sudo crontab -e" and voilà.

---

### Post by xendistar on 2010-09-10
The task are listed under crontab, if I do crontab -e I get the following (it opens in nano)

0 0 * * 1 ./day1.sh # JOB_ID_1
0 0 * * 2 ./day2.sh # JOB_ID_2
0 0 * * 3 ./day3.sh # JOB_ID_3
0 0 * * 4 ./day4.sh # JOB_ID_4
0 0 * * 5 ./day5.sh # JOB_ID_5

The basic are I want the script to run at midnight Monday to Friday. I don't have a cron or crontab log in /var/log/

I have uncommented cron in rsyslogd and restarted the service, but still no logs??

---

### Post by clrg on 2010-09-10
Edit your script to do something that confirms its been run, for example, add a

```
touch $HOME/iJustRan.$0;
```

to the end of your script. That will create a file named iJustRan.<nameOfProcess> in your home directory.

---

### Post by xendistar on 2010-09-10
Thanks I will try later as I don't have access to the server at the moment, I will report back how it goes.

---

### Post by hictio on 2010-09-10
> **xendistar said:**
> The task are listed under crontab, if I do crontab -e I get the following (it opens in nano)

0 0 * * 1 ./day1.sh # JOB_ID_1
0 0 * * 2 ./day2.sh # JOB_ID_2
0 0 * * 3 ./day3.sh # JOB_ID_3
0 0 * * 4 ./day4.sh # JOB_ID_4
0 0 * * 5 ./day5.sh # JOB_ID_5

The basic are I want the script to run at midnight Monday to Friday. I don't have a cron or crontab log in /var/log/

I have uncommented cron in rsyslogd and restarted the service, but still no logs??

The crontabs for users are stored under the directory "/var/spool/cron/crontabs/", and you have to use sudo actually view, to paginate, them, if you want to, like this:
```

sudo less /var/spool/cron/crontabs/some.user ENTER

```

Type q to exit the paginator.

---

