---
title: "auto start transmission"
date: 2011-04-02
forum: Server Platforms
---

### Post by wlraider70 on 2011-04-02
I have a headless server booting to the command line.
I just setup transmission to monitor a dropbox folder.

My fear is that i will restart my server and forget to start transmission. (do I need to start it)

So how can I cause transmission to start with boot or does it have a daemon. Do those auto start?

---

### Post by tangerine0469 on 2011-04-02
I would use cron to start it. I use cron to run shell scripts and programs.
```
 sudo crontab -e
```
Then add an entry that follows the following format for transmission:
minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command
example:
```
@reboot /etc/init.d/transmission start
```

If my understanding of cron is what i think it is then that should work.

Edit:
The date and time format is for scheduling start and stop times should you want it to run it at certain times. But with the ```
@reboot
``` you do not need to take dates and times into account.

For more information read these:
[http://www.cyberciti.biz/faq/linux-execute-cron-job-after-system-reboot/](http://www.cyberciti.biz/faq/linux-execute-cron-job-after-system-reboot/)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by MechaMechanism on 2011-04-02
```
$ sudo apt-get install transmission-daemon
```Edit the file at /etc/transmission-daemon/settings.json
Also read README.json at the same location.

---

