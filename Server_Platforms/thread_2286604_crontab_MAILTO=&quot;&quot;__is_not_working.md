---
title: "crontab MAILTO=&quot;&quot;  is not working"
date: 2015-07-13
forum: Server Platforms
---

### Post by jay98 on 2015-07-13
Before anyone gets too incensed, please know that I have googled this and have yet to find a viable or applicable solution.  So...
I am running Ubuntu Server 12.04, and run tripwire every morning.  I have a tripwire report emailed to me, but a copy of that report is also emailed to the root account on that server, and I cannot stop these emails.  

Running ```
sudo crontab -e
``` my crontab looks like this:

```
MAILTO=""
0 5 * * * /usr/sbin/tripwire --check | mail -s "Daily Tripwire Report" me@mydomain.com

```

Am I setting the MAILTO variable incorrectly?
Any thoughts on stopping the local email to root but still receiving the external email?

Thx

---

### Post by nerdtron on 2015-07-14
From here: [http://unix.stackexchange.com/questions/100722/how-do-i-completely-silence-a-cronjob-to-dev-null](http://unix.stackexchange.com/questions/100722/how-do-i-completely-silence-a-cronjob-to-dev-null)

try redirecting all output to /dev/null
0 5 * * * /usr/sbin/tripwire --check | mail -s "Daily Tripwire Report" [email]me@mydomain.com[/email] > /dev/null 2>&1

---

### Post by jay98 on 2015-07-14
Thanks, I'll give it shot.  I actually thought about this, but wasn't sure if /dev/null would squash the email I did want.  Will let you know...

---

### Post by nerdtron on 2015-07-14
> **jay98 said:**
> Thanks, I'll give it shot.  I actually thought about this, but wasn't sure if /dev/null would squash the email I did want.  Will let you know...

If the /dev/null squashes even the content of the email, then move your cron commands to a script file, then trigger the script using cron. Something like:
0 5 * * * /bin/bash /my/tripwire/script.sh > /dev/null 2>&1


Then the contents of the script.sh is:
```
 #!/bin/bash
/usr/sbin/tripwire --check | mail -s "Daily Tripwire Report" [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL]

```

---

### Post by jay98 on 2015-07-15
This did not work :(  
I actually got both emails; the email to [EMAIL="me@mydomain.com"]me@mydomain.com[/EMAIL], and the email to root on that box.
MAILTO="" and redirecting output to /dev/null 2>&1 are ignored completely.

I am editing cron with
```
sudo crontab -e
```
The same way I added the cron job itself...

Any thoughts?

---

