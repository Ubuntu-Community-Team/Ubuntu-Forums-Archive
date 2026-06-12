---
title: "Security Emails form cron.daily"
date: 2014-07-20
forum: Security
---

### Post by dunbrokin on 2014-07-20
I am not sure this is quite the correct place to put this email so, dear Moderator, please feel free to move it to the correct place...

I have a number of security cron.jobs running each day and the idea is that I get sent an email of the logs. Here is what I get....

Why is this being sent to root and not to my gmail account?

Delivery to the following recipient failed permanently:

     [email]root@gmail.com[/email]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the server for the recipient domain gmail.com by gmail-smtp-in.l.google.com. [2607:f8b0:400e:c02::1b].

The error that the other server returned was:
550 5.2.1 The email account that you tried to reach is disabled. wh7si11234829pac.46 - gsmtp

----- Original message -----

DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;
        d=gmail.com; s=20120113;
        h=from:to:subject:content-type:message-id:date;
        bh=JMEvrFXwWI5JnIuROA+G/6w8uxfbKmrr2ug//g2pyzE=;
        b=CFCaX7WD7GkY2/6s8ZL/DjItUM9svNx87sMRoTBII9sUGLk1nJGpOkXI/PqdcSt1/Y
         HgQNCw2GtLax7paqqIPuNXoKJ5igK6eH4cGdgUi26jIaI2s6/fkpRizBI0cXZ5F8/YhO
         ox5qyWG8whuMvcH0gckrKJn4CHaZo0UU8g2NPWgvMHmzBwH+DztXG9bb3J3pkOKuwRD/
         VRt1hseLGJGkIUHuM2zwqrqidhtQfiJ80jojaFZYIvFZ2BxTKMhmY+DQ9z+cRLEE/XvA
         7wTuDBUb7bjK9SRvbpjT6UbM0U1Qlca9+p1ViRsj9F/i0w4ZZV51hlzPsxIzsPyH9hNu
         uk0A==
X-Received: by 10.70.50.137 with SMTP id c9mr18342629pdo.101.1405862839416;
        Sun, 20 Jul 2014 06:27:19 -0700 (PDT)
Return-Path: <xx-xx@gmail.com>
Received: from pj-selfbuild (125-236-150-149.jetstream.xtra.co.nz. [125.236.150.149])
        by mx.google.com with ESMTPSA id xk1sm46168333pac.21.2014.07.20.06.27.16
        for <root@gmail.com>
        (version=TLSv1.2 cipher=ECDHE-RSA-AES128-GCM-SHA256 bits=128/128);
        Sun, 20 Jul 2014 06:27:17 -0700 (PDT)
From: Anacron <xx-xx@gmail.com>
X-Google-Original-From: Anacron <root@gmail.com>
Received: by pj-selfbuild (Postfix, from userid 0)
        id 6714598; Mon, 21 Jul 2014 01:27:10 +1200 (NZST)
To: [email]root@gmail.com[/email]
Subject: Anacron job 'cron.daily' on pj-selfbuild
Content-Type: text/plain; charset=US-ASCII
Message-Id: <20140720132711.6714598@pj-selfbuild>
Date: Mon, 21 Jul 2014 01:27:10 +1200 (NZST)

/etc/cron.daily/aide:
/etc/cron.daily/aide: line 413: NF_ADD: unbound variable
run-parts: /etc/cron.daily/aide exited with return code 1
/etc/cron.daily/chkrootkit:

---

### Post by dunbrokin on 2014-07-20
I get this output from my aide scan....I have no idea what it means and nothing sensible comes up when I google it?!

/etc/cron.daily/aide: line 413: NF_ADD: unbound variable

---

### Post by QIII on 2014-07-21
Threads merged, as they seem to be caused by the same issue.

Looks like you are running in to [this]("https://bugs.launchpad.net/ubuntu/+source/aide/+bug/1323827") bug.

You can click "Affects me" if you have a Launchpad account, but please don't make a comment "Affects me, too".  Those just get in the way.

You can subsribe to it and see how it progresses.

---

### Post by dunbrokin on 2014-07-21
Thanks for that link. Though having read about the bug, I am not sure that the root posting issue as in the first posting is caused by the same issue. I think the first posting is something that I have got wrong in either postfix or in cron...or in the various .conf files that I am using....I just cannot figure it out and don't even know where to start!

---

### Post by dunbrokin on 2014-07-24
I am getting nowhere fast on this problem. I have set up a crontab instead. The crontab runs because I can find the output in the log...however I do not get a mail sent to my email address.

Here is the crontab 

# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
MAILTO=dunbrokin@gmail.com
 00 09 * * * root /usr/local/lynis/lynis -c -Q

My mail server is exim4. I am guessing that this is the problem, but do not have sufficient knowledge to debug. Can somebody help me out here please

---

### Post by dunbrokin on 2014-07-24
This might help.

UPEX4CmacrosUPEX4C = 1
##############################################
# the following macro definitions were created
# dynamically by /usr/sbin/update-exim4.conf
.ifndef MAIN_LOCAL_INTERFACES
MAIN_LOCAL_INTERFACES=<; 10.1.1.14; ::1
.endif
.ifndef MAIN_PACKAGE_VERSION
MAIN_PACKAGE_VERSION=4.82-3ubuntu2
.endif
.ifndef MAIN_LOCAL_DOMAINS
MAIN_LOCAL_DOMAINS=@:localhost:gmail.com
.endif
.ifndef MAIN_RELAY_TO_DOMAINS
MAIN_RELAY_TO_DOMAINS=empty
.endif
.ifndef ETC_MAILNAME
ETC_MAILNAME=gmail.com
.endif
.ifndef LOCAL_DELIVERY
LOCAL_DELIVERY=mail_spool
.endif
.ifndef MAIN_RELAY_NETS
MAIN_RELAY_NETS=10.1.1.14 : 127.0.0.1 : ::::1
.endif
.ifndef DCreadhost
DCreadhost=empty
.endif
.ifndef DCsmarthost
DCsmarthost=empty
.endif
.ifndef DC_eximconfig_configtype
DC_eximconfig_configtype=internet
.endif
.ifndef DCconfig_internet
DCconfig_internet=1
.endif

---

