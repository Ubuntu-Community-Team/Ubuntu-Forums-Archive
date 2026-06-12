---
title: "crontab"
date: 2010-03-18
forum: Server Platforms
---

### Post by rtvradio on 2010-03-18
I'm a newbie and sorry for my english.
Ubuntu server and  ssh session

crontab with * * * * * kill 20206 work
with with * * * * * kill SIGUSR2 20206 NOT work !

from SYSLOG
Mar 18 09:40:01 serverzzzz /USR/SBIN/CRON[20250]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Mar 18 09:40:38 serverzzzz crontab[20319]: (shoutcast) BEGIN EDIT (shoutcast)
Mar 18 09:40:55 serverzzzz crontab[20319]: (shoutcast) REPLACE (shoutcast)
Mar 18 09:40:55 serverzzzz crontab[20319]: (shoutcast) END EDIT (shoutcast)
Mar 18 09:41:01 serverzzzz /usr/sbin/cron[20284]: (crontab) ORPHAN (no passwd entry)
Mar 18 09:41:01 serverzzzz /USR/SBIN/CRON[20331]: (shoutcast) CMD (kill -SIGUSR2 20206)

Thank you very much.

---

### Post by cdenley on 2010-03-18
```

kill **[COLOR="Red"]-[/COLOR]**SIGUSR2 20206

```
```

man kill

```

---

### Post by rtvradio on 2010-03-18
Sorry for my error.
Correct syntax is with -SIGUSR2 but don't work.

from syslog
Mar 18 09:41:01 serverzzzz /USR/SBIN/CRON[20331]: (shoutcast) CMD (kill -SIGUSR2 20206)
From command line work, into crontab NOT.
Thanks.

---

### Post by cdenley on 2010-03-18
Are you sure the kill command is being run? Did you set a PATH variable?
```

/bin/kill -SIGUSR2 20206

```
Are you sure it is still the correct PID?

---

### Post by rtvradio on 2010-03-18
from bash

ps 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
.......................
1000     20206  0.4  0.0    900   560 ?        S    09:39   1:20 ./sc_nsv 8016.conf
......................

~$ kill -SIGUSR2 20206  

work

~$ crontab -l
# m h  dom mon dow   command
* * * * * kill -SIGUSR2 20206

don't work , nothing happens !

syslog
Mar 18 15:18:01 serverxxxxx /USR/SBIN/CRON[25980]: (shoutcast) CMD (kill -SIGUSR2 20206)


Thanks.

---

### Post by rtvradio on 2010-03-18
With  PATH variable WORK !
Thank you very very much.

[RTVTelevision]("http://rtvtelevision.22web.net")

---

### Post by cdenley on 2010-03-18
> **rtvradio said:**
> from bash

ps 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
.......................
1000     20206  0.4  0.0    900   560 ?        S    09:39   1:20 ./sc_nsv 8016.conf
......................

~$ kill -SIGUSR2 20206  

work

~$ crontab -l
# m h  dom mon dow   command
* * * * * kill -SIGUSR2 20206

don't work , nothing happens !

syslog
Mar 18 15:18:01 serverxxxxx /USR/SBIN/CRON[25980]: (shoutcast) CMD (kill -SIGUSR2 20206)


Thanks.

You still didn't specify the full path to /bin/kill! Did you set a PATH variable?

**nevermind**

---

### Post by rtvradio on 2010-03-18
~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by KB1JWQ on 2010-03-18
Your environment variables won't be called from cron; specify the locations of binaries via absolute path.

---

### Post by cdenley on 2010-03-18
> **KB1JWQ said:**
> Your environment variables won't be called from cron; specify the locations of binaries via absolute path.

Either that, or set the path variable in your crontab. I already suggested both.
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
* * * * * /usr/bin/mycommand
* * * * * myothercommand

```

---

### Post by rtvradio on 2010-03-18
founded on [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)


01,31 04,05 1-15 1,6 * /usr/bin/somedirectory/somecommandThe above example will run /usr/bin/somedirectory/somecommand at 01 and 31 past the hours of 4:00am and 5:00am on the 1st through the 15th of every January and June. 
The "/usr/bin/somedirectory/somecommand" text in the above examples indicates the task which will be run at the specified times. **It is recommended that you use the full path to the desired commands** as shown in the above examples. Enter *which somecommand* in the terminal to find the full path to *somecommand*.

---

### Post by cdenley on 2010-03-18
In the same link:
> 
Depending on the commands being run, you may need to expand the root users PATH variable by putting the following line at the top of their crontab file:
```

PATH=/usr/sbin:/usr/bin:/sbin:/bin

```


---

