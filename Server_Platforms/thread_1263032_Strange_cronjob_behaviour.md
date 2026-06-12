---
title: "Strange cronjob behaviour"
date: 2009-09-10
forum: Server Platforms
---

### Post by ThomWilhelm on 2009-09-10
For many months now I have been running a cronjob at the start of every week using the following command:

1 0 * * 1 wget -q [http://127.0.0.1/serverScripts/script.php](http://127.0.0.1/serverScripts/script.php)

However, every week this started running the script twice! Does anyone know why this could possibly be? I have checked all obvious problems such as the same script being run at the same time from another server, and it is definately a problem with this server running the script twice...

Cheers.
Thom.

---

### Post by wojox on 2009-09-10
```
* * * * */0 wget -q http://127.0.0.1/serverScripts/script.php
```

That should run it every Sunday.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by ThomWilhelm on 2009-09-10
Thanks for the reply, however sorry when I say start of the week I mean I want it to run at 00:01 on Monday morning (I always see this as the start of the week :)).

I have found a guy having the same problem as me and am now trying his solution to see if it works:

[http://forums.quadrahosting.com.au/showthread.php?p=3078](http://forums.quadrahosting.com.au/showthread.php?p=3078)

As far as I can see, its more a case of a technical thing with wget rather than my crontab being wrongly configured (however I'm still relatively new to Ubuntu having only just migrated the server system from Windows).

---

### Post by wojox on 2009-09-10
```
1 * * * 1 /usr/bin/wget http://127.0.0.1/serverScripts/script.php
```

Maybe the full path to wget.

---

### Post by terazen on 2009-09-11
What does it do if you manually run it?  Just run once?

---

### Post by ThomWilhelm on 2009-09-12
Yup if I run it once by using my browser to open the file then it does just run once. Funnily enough I tried running the script midweek from the old cron syntax and it ran more than twice! On Monday morning the script I had a problem with last week will be run again using:

1 0 * * 1 wget -q --ignore-length [http://127.0.0.1/serverScripts/script.php](http://127.0.0.1/serverScripts/script.php)

Reading about the ingore-length parameter, it sounds as if it could do the job:
‘--ignore-length’Unfortunately, some http servers (cgi programs, to be more precise) send out bogus Content-Length headers, which makes Wget go wild, as it thinks not all the document was retrieved.  You can spot this syndrome if Wget retries getting the same document again and again, each time claiming that the (otherwise normal) connection has closed on the very same byte.       So I will let you know what happens. Wojox, would specifying the full path to wget have any effect?

---

### Post by scorp123 on 2009-09-12
> **ThomWilhelm said:**
> Wojox, would specifying the full path to wget have any effect? cron jobs run inside a very very minimal shell. Yes, it's still "bash" but it does not necessarily load your profile and what not, just the bare minimum so it could run jobs. It could easily be that when the job runs it does not get the $PATH variable set that would tell it where to look for programs and what not. So yes, setting the full path of commands inside a cron job is therefore a good idea.

---

### Post by ThomWilhelm on 2009-09-24
Ok this has now been fixed, the problem was that wget has a default timeout of 900 seconds. As the script was running for longer than 900 seconds, it I think caused the script to be recalled. I have increased this timeout parameter to 3600 and everything is fine again.

Thanks for the help! :)

---

