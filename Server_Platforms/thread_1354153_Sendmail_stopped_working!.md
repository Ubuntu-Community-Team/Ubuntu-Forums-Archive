---
title: "Sendmail stopped working!"
date: 2009-12-13
forum: Server Platforms
---

### Post by Krupski on 2009-12-13
Hi all,

I have a little file server at home running Ubuntu Server 9.04, 64 bit.

At bootup, one of the things it does is send me an email telling me that it booted.

Problem is... all of a sudden, it stopped working (the email that is).

Here's the script that sends me the email (which hasn't changed in over a year):

```

#! /bin/bash
tmpfile=$( /bin/mktemp -t )
myname=[COLOR="Red"]xxxxxxx[/COLOR]@roadrunner.com
/bin/echo return-path: $myname >> $tmpfile
/bin/echo for: $myname >> $tmpfile
/bin/echo from: $myname >> $tmpfile
/bin/echo to: $myname >> $tmpfile
/bin/echo subject: linux storage drive boot >> $tmpfile
/bin/echo Hello there Roger... this is an informational message: >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo System rebooted: $( /bin/date +%c ) >> $tmpfile
/bin/echo >> $tmpfile
/bin/echo Yours truly, "The Storage Drive" >> $tmpfile
/bin/echo >> $tmpfile
/bin/cat $tmpfile | sendmail -t
/bin/rm $tmpfile
/usr/bin/beep -f 2349 -l 100 -r 5
exit 0

```

To see it more clearly, here's what $tmpfile contains (i.e. what is piped to sendmail):

```

return-path: [COLOR="Red"]xxxxxxx[/COLOR]@roadrunner.com
for: [COLOR="Red"]xxxxxxx[/COLOR]@roadrunner.com
from: [COLOR="Red"]xxxxxxx[/COLOR]@roadrunner.com
to: [COLOR="Red"]xxxxxxx[/COLOR]@roadrunner.com
subject: linux storage drive boot
Hello there Roger... this is an informational message:

System rebooted: Sun 13 Dec 2009 03:38:03 PM EST

Yours truly, The Storage Drive

```

(of course, the "[COLOR="Red"]xxxx[/COLOR]" is not there... my real email address is).

Anyway, it used to work... now it's stopped. It seems that it stopped working about 1-1/2 weeks ago.

My ISP's SMTP server hasn't changed, and I can send email to myself using Thunderbird no problem.

I've also taken the message source of a received email and piped it to 'sendmail' (see example below) and this doesn't work either.

```

From: xxxxxxx@roadrunner.com
Subject: NETGEAR Security Log [3c:b3:92]
To: xxxxxxx@roadrunner.com

2009 Dec 12 22:35:52 [FVS338] [login] Value TTTTT at change  lloginTimeoutGet  and value is LOCALDOMAIN_
2009 Dec 12 22:35:52 [FVS338] [login] At line 2527  TTTT at func lloginLogout_
2009 Dec 12 22:35:52 [FVS338] [login] Logout succeeded for user admin
2009 Dec 12 22:35:52 [FVS338] [login] Deleting all cookie files with privilege 0
2009 Dec 12 23:28:51 [FVS338] [login] Value TTTTT at change  lloginTimeoutGet  and value is LOCALDOMAIN_
2009 Dec 12 23:28:51 [FVS338] [login] At line 2527  TTTT at func lloginLogout_
2009 Dec 12 23:28:54 [FVS338] [login] Value TTTTT at change  lloginTimeoutGet  and value is LOCALDOMAIN_
......
......
---rest deleted for this example---
......

```

This is sent by my router to my email account. I receive these just fine, but to pipe it through my file server's 'sendmail', it fails.

Anyone have any ideas what the heck may have gone wrong?

I have backups of my OS (a 4 gigabyte CF card) that I routinely make. Restoring a backup from 03 December 2009 does not help, so whatever went wrong or changed happened BEFORE that date. Or, maybe not... since the last email I got from my file server is dated 09 December 2009. Confusing.

Any help will be greatly appreciated!

Thanks!

-- Roger

(edit to add):

When I hand run the script that sends the email, the process "smtp" appears in memory for a minute or so... longer that it seems like it should (which makes me think it's "trying", but failing).

```

root@storage:/ ps -A | grep -i smtp
 3543 ?        00:00:00 smtp

```

...and here is the last entry in '/var/log/mail.log':

```

Dec 13 15:58:41 storage postfix/pickup[2808]: 5877129065: uid=0 from=<root>
Dec 13 15:58:41 storage postfix/cleanup[3539]: 5877129065: message-id=<20091213205841.5877129065@storage.roadrunner.com>
Dec 13 15:58:41 storage postfix/qmgr[2809]: 5877129065: from=<root@roadrunner.com>, size=494, nrcpt=1 (queue active)
Dec 13 15:58:42 storage postfix/smtp[3543]: 5877129065: to=<xxxxxxx@roadrunner.com>, relay=smtp-server.roadrunner.com[75.180.132.33]:25, delay=0.85, delays=0.42/0/0.24/0.19, dsn=2.0.0, status=sent (250 OK B2/F1-01550-185552B4)
Dec 13 15:58:42 storage postfix/qmgr[2809]: 5877129065: removed

```

(note: name replaced with 'xxxxx')

---

### Post by Krupski on 2009-12-13
More info:

Found the problem - need a solution.

Although I specify the "From" field in the file that I pipe to sendmail, it gets REPLACED with "root@".

My ISP SMTP server rejects any email coming from "root@(anything)" for security purposes.

How can I change "root" to my actual name?

My '/etc/mailname' file correctly contains the domain (i.e. "roadrunner.com") but sendmail keeps sending mail "from" [email]root@roadrunner.com[/email] which my ISP rejects.

I want to override (or change) that default. How to do that?

And please no face slapping about using the root account... because USUALLY the emailing is done by the server itself and even when I log in as a "user", my username is not the same as my email account name... so that's not an option.

Thanks.

-- Roger

---

### Post by Krupski on 2009-12-14
Found the problem... Unknown to me, sendmail was changing the "From" field to "root@roadrunner.com".

My ISP suddenly decided, for security purposes, to not accept email from "root@anything".

So, I had to force sendmail to use MY email address rather than "root" as the sender by using the '-f' command line option.

So, here's the solution:

```

# before (fails)
cat file | sendmail -t

```

```

# after (works)
cat file | sendmail [COLOR="Red"]-f email@mydomain.com[/COLOR] -t

```

The part in red was the addition necessary to make it work.

-- Roger

---

### Post by BkkBonanza on 2009-12-15
I believe you need to add the -f <realfromaddress> to the senmail command line.
I had to do that once for automated emails being sent via smtp. If not sure then read up "man sendmail" about the -f option to get it right.

---

