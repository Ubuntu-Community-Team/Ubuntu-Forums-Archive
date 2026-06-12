---
title: "Mysterious Cron Emails / Syslog Output"
date: 2006-07-17
forum: Server Platforms
---

### Post by wahman143 on 2006-07-17
Hi all,
I finished installing an Ubuntu 6.06 LTS server yesterday (x86 arch), and while it is working properly for the most part, I've gotten some funny cron emails and syslog output...I believe the two are related, but I'm not 100% sure.  Anyway, here's the scoop:

- Ubuntu 6.06 x86 Server Install
- Main items installed:  Apache2, MySQL, Postfix, Dovecot, Gallery2, Horde3 / Horde-Imp3

Cron Email in question:
```

Subject: Cron <root@belisarius> root    run-parts --report /etc/cron.hourly

Date: Mon, 17 Jul 2006 04:17:01 -0400 (EDT)
X-Virus-Scanned: ClamAV using ClamSMTP

/bin/sh: root: command not found
```

Not too sure why /bin/sh is failing, as it is in my path...
The only crontab active is the system crontab, and here it is:
```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root@<snip>.info

# m h dom mon dow user	command
17 *	* * *	root    run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6	1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly

```

Now the second part of my question - if I do a 'tail /var/log/messages', I am getting a lot of entries like this:

```

Jul 17 01:44:57 belisarius -- MARK --
Jul 17 02:04:58 belisarius -- MARK --
Jul 17 02:24:58 belisarius -- MARK --
Jul 17 02:44:59 belisarius -- MARK --
Jul 17 03:04:59 belisarius -- MARK --
Jul 17 03:24:59 belisarius -- MARK --
Jul 17 03:45:00 belisarius -- MARK --
Jul 17 04:05:00 belisarius -- MARK --
Jul 17 04:25:01 belisarius -- MARK --
Jul 17 04:45:01 belisarius -- MARK --

```
I have never seen anything like this, so I'd appreciate any input anyone can toss this way!  Please let me know if I can provide any other info that would be useful!

Off-topic - just wanted to thank the Ubuntu community for a solid product!

Cheers, and thanks in advance for taking time to look at my post!

Wah

---

### Post by scxtt on 2006-07-17
i can't imagine why you wouldn't, but do you have the **/bin/sh --> /bin/bash** symbolic link?
[SIZE="4"][php]:> ll /bin | grep sh
-rwxr-xr-x 1 root root 649K 2006-04-21 18:51 bash
lrwxrwxrwx 1 root root    4 2006-07-09 04:55 rbash -> bash
lrwxrwxrwx 1 root root    4 2006-07-09 04:55 sh -> bash[/php][/SIZE]and i have those "MARK" entries as well, every 20 minutes, it is weird ...

---

### Post by wahman143 on 2006-07-17
Hi scxtt,
Thanks for the response!

Yes, I do have the /bin/sh -> /bin/bash link...I even went as far as changing the line in my crontab to 'SHELL=/bin/bash', and it gave me the same error, but with /bin/bash instead of /bin/sh.  

Those --MARK-- log messages are weird, aren't they? :lol: - and you're right, they are exactly every 20 minutes!

Cheers,
W.

---

### Post by scxtt on 2006-07-17
i wish i had some ideas for the /bin/sh problem, but my crontab doesn't give me that error, and i don't make use of the default cron entries (i use /etc/crontab, but not the hourly, daily, weekly, monthly entries) ... if you don't use them, couldn't you comment them out (or at least the hourly one) to stop the message?

and that MARK thing is a total mystery to me, i'm assuming it has something to do w/ default install programs - cause i don't use my box as a server (use a VM for that, don't know if the entries exist in the log there) ...

---

### Post by wahman143 on 2006-07-17
Yeah, I was planning on doing my own crontab as the next step - on my Gentoo box, I don't use the default crontab either.  So, I'll see how that goes!

Thanks again for your time, and if I find anything about the --MARK-- messages, I'll be sure to post up!

Take care,
W.

---

### Post by va3uxb on 2006-07-17
I have the --MARK-- in my /var/log/messages as well.  I just found this via google:
[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3517611](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3517611)

Seems it is the syslog daemon just letting us know it's alive, so it seems to be a normal function.

-Stephanie

---

### Post by scxtt on 2006-07-17
well that's boring :p -- but thanks for solving the mystery (i knew i shoulda google'd it) ...

---

### Post by wahman143 on 2006-07-17
Awesome va3uxb!  I just made the change and I set it to --MARK-- every 4 hours...I'll see if that does the trick!  Thanks for the link!

@scxtt - creating my own crontab fixed the issue with /bin/sh.  Not sure why, but hey...it's fixed!

Thanks to the both of you for helping!

Cheers, and have a great day!

W.

---

