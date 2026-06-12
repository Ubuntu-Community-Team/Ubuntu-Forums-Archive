---
title: "root mailbox filling with Cron messages"
date: 2010-02-03
forum: Server Platforms
---

### Post by Rich78 on 2010-02-03
I'm getting the following messages sent to my root account mailbox.  It appears to be reporting an issue finding ntpdate, however when running the following command:

aptitude show ntpdate | grep State

It shows as installed and any ntpdate commands work with no issues, so I have no idea why this is getting regularly reported?


From [email]root@mydomain.co.uk[/email] Wed Feb 03 18:20:01 2010
Return-path: <root@mydomain.co.uk>
Envelope-to: [email]root@mydomain.co.uk[/email]
Delivery-date: Wed, 03 Feb 2010 18:20:01 +0000
Received: from root by meta-serv-01 with local (Exim 4.69)
	(envelope-from <root@mydomain.co.uk>)
	id 1NcjpZ-0005aW-Uo
	for [email]root@mydomain.co.uk[/email]; Wed, 03 Feb 2010 18:20:01 +0000
From: [email]root@mydomain.co.uk[/email] (Cron Daemon)
To: [email]root@mydomain.co.uk[/email]
Subject: Cron <root@my-serv-01> ntpdate -u tick.xtrahost.co.uk
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1NcjpZ-0005aW-Uo@my-serv-01>
Date: Wed, 03 Feb 2010 18:20:01 +0000

/bin/sh: ntpdate: not found



Any help would be greatly appreciated as I'm running out of ideas.

---

### Post by gombadi on 2010-02-03
cron does not use the same environment as you have when logged in. The PATH is very small for security reasons.

The best option is to use the full path to ntpdate -
```

/usr/sbin/ntpdate

```

---

### Post by Rich78 on 2010-02-03
Sorry I may have not explained myself to well.

Ever since I installed Exim4 as an MTA, my root account has been receiving mail every 5 mins, an example being the above.

They appear to be being generated due to a problem with ntpdate, however I cannot fault ntpdate.

I can issue the command in the subject line ntpdate -u tick.xtrahost.co.uk and get back the correct response:

3 Feb 20:09:15 ntpdate[21759]: adjust time server 82.113.128.10 offset 0.004965 se

However the detail of the mail suggests ntpdate isn't found, which I cannot fault so I don't know where or how it's calling ntpdate in order to solve the issue and stop the mail reports.

I didn't setup a Cron job for this so I don't know what's calling ntpdate.  

crontab -l, lists "no crontab for root"

Thanks

---

### Post by BkkBonanza on 2010-02-03
gombadi has it right. You have a path problem since the cron path is limited to /usr/bin;/bin and ntpdate is in /usr/sbin

There has to be a cron running somewhere. I would check cron for other user accounts like exim or see if there are crons installed in /etc/cron.hourly (or daily). These cron services make use of anacron rather than cron, so maybe explore that, /etc/anacrontab. Also check logs in /var/log to see if you can track down whats originating the cron messages.

---

### Post by Rich78 on 2010-02-04
Thanks, will take a look tonight.  I had a response from support hosting my VM and they suggested similar.

---

### Post by BkkBonanza on 2010-02-04
It just occurred to me another thing to check.

sudo dir /var/spool/cron/crontabs/

That will list any cronjobs active regardless of which user they're run as. If you see a file in there with a user's name then you can use,

sudo crontab -l -u <user>

to see what that user's cron is set as.

(note - do not edit the files directly, that's what "crontab -e" is for)

---

### Post by Rich78 on 2010-02-04
ok I had a look and it seems that there were no variables set in cron tab.

Only entry was:

*/5 * * * * root ntpdate -u tick.xtrahost.co.uk


So I added:

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/

# run-parts
*/5 * * * * root ntpdate -u tick.xtrahost.co.uk


I edited this in vi and then noticed you put to not edit the file directly?  Is this an issue?  I restarted the cron service after the edit.

---

### Post by Rich78 on 2010-02-04
Final update, this has obviously fixed the issue as I'm still receiving mails however the message is:

4 Feb 19:50:01 ntpdate[21911]: adjust time server 82.113.128.10 offset -0.000233 sec


So I've added the following to the end of the command line:

/dev/null 2>&1

Which is supposed to run ntpdate silently.

---

### Post by Rich78 on 2010-02-04
Seems I was told a load of rubbish with that last line so amended to 

ntpdate -s -u tick.xtrahost.co.uk

Which runs it silently.

---

### Post by BkkBonanza on 2010-02-04
When you use the crontab command to edit it makes sure that cron knows of the updated file. Editing it directly doesn't notify cron but if you restart cron then it probably works, though isn't the recommended method.

The "/dev/null 2>&1" silencer part should work but you missed a symbol. What this is supposed to do it redirect "stdout" to /dev/null and redirect stderr as well. It needs an initial ">" redirect for it to work, so like this...

cmd-to-run >/dev/null 2>&1

However, if ntpdate works with -s to prevent output then that's fine too.

Good to see you got it all sorted out. You probably don't need to run ntpdate quite so often as your time isn't going to drift much in 5 minutes, if at all. I'd suggest once a day or once an hour unless there's a need to be super accurate, in which case using the ntpd (the network time daemon) is the preferred method as it will track network latencies as well.

---

### Post by Rich78 on 2010-02-05
Thanks again, all is well with it now :D

---

