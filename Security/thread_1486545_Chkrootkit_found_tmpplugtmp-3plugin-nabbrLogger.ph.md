---
title: "Chkrootkit found /tmp/plugtmp-3/plugin-nabbrLogger.php"
date: 2010-05-18
forum: Security
---

### Post by MechaMechanism on 2010-05-18
Chkrootkit had some very interesting results.  After some investigation, I have determined there is nothing to worry about.  My question for you is, why the heck do ad tracking web services use terms like logger in files like PHP or JSON or whatever.  How about less scary words that don't make me have to go through investigation.  Not saying I panic, I don't.  The worst thing I could do is to panic and act irrational.  At any rate I deleted the harmless files after using Gedit and less and Google to figure things out.  So if you see scary stuff from flash directories in /tmp, usually called /plugtmp, don't panic just open the files as text and do a little investigation.

The nabbr file refers to this web site > [http://nabbr.com/](http://nabbr.com/)

> From:     Anacron <root@universal-mechanism.org>
To:     [EMAIL="root@universal-mechanism.org"]root@universal-mechanism.org[/EMAIL]
Subject:     Anacron job 'cron.daily' on universal-mechanism
Date:     05/17/2010 07:51:53 AM


/etc/cron.daily/chkrootkit:

/dev/shm/pulse-shm-1577550096

/usr/lib/pymodules/python2.6/.path /usr/lib/firefox-3.6.3/.autoreg /usr/lib/perl5/auto/DateTime/Format/Mail/.packlist /usr/lib/xulrunner-1.9.2.3/.autoreg


/tmp/plugtmp-3/plugin-index.php
/tmp/plugtmp-3/plugin-index-3.php
/tmp/plugtmp-3/plugin-index-1.php
/tmp/plugtmp-3/plugin-index-4.php
/tmp/plugtmp-3/plugin-nabbrLogger.php
/tmp/plugtmp-3/plugin-index-2.php

eth0: PACKET SNIFFER(/sbin/dhclient3[1460])
user nate deleted or never logged from lastlog!

---

