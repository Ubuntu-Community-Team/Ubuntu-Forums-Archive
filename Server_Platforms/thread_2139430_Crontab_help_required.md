---
title: "Crontab help required"
date: 2013-04-26
forum: Server Platforms
---

### Post by jamesr on 2013-04-26
Hi,

I need help cron parameters for the following procedures. I currently use Mondorescue to run a backup on a weekly basis. This is set-up as cron job.
The requirements are weekly, Saturday morning at  4:01am . This task was easy:-
 ```
PATH=/sbin:/bin:/usr/bin:/usr/sbin:/root
# m h  dom mon dow   command
01 04 * * 6 /root/cron_backup_e_sh

```
But I have changed my requirements. I would like to do the following  only do a full backup monthly on the first Saturday and differential backups on the other Saturdays. 
I was told that Cron could be restricted to only running certain days, can that be linked to days of the week. As follows if x-x was replaced by 1-7 and leave the day of the week to 6 ie Saturday  
```
PATH=/sbin:/bin:/usr/bin:/usr/sbin:/root
# m h  dom mon dow   command
01 04 x-x * 6 /root/cron_backup_e_sh

```
But equally I would like to run a differential backup on the remaining Saturdays of the month, but cannot find a way excluding week 1.

Currently I am using a series of "at" jobs that I copy over at the end of the month.

Best Wishes
Jim R.

---

### Post by papibe on 2013-04-26
Hi jamesr.

Although cron have lots of options, selecting the first Saturday of a month is not one of them. Luckily, that concern can be easily solved by adding a basic bash test.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2073687&highlight=cron+monday") with a similar concern, and let us know if it helps.

Regards.

---

