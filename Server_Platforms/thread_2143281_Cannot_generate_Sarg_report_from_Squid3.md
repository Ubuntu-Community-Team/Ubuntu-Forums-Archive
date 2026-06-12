---
title: "Cannot generate Sarg report from Squid3"
date: 2013-05-08
forum: Server Platforms
---

### Post by bullet333 on 2013-05-08
Ubuntu 12.10
Squid3 [COLOR=#333333][FONT=sans-serif]3.1[/FONT][/COLOR]
Dansguardian [COLOR=#333333][FONT=sans-serif]2.10.1.1
Postfix [/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]2.9.6
[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]Webmin 1.620[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]

When I attempt to 'Generate Report Now' using 'Squid Report Generator' on the Webmin module I get the following error message:

[/FONT][/COLOR]```

sarg -l /var/log/squid3/access.log mail: cannot send message: Process exited with a non-zero status
SARG: command return status 36SARG: command: sudo mail -s "SARG report, Wed May  8 12:40:11 2013" "user@domain.com" <"/tmp/sarg/2013May08-2013May08/report"

```[COLOR=#333333][FONT=sans-serif]

Sending mail via the 'Mail' command works fine.  I was also getting error messages via email:
[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]
[/FONT][/COLOR]
[PHP]
Failed to generate Sarg report:sarg -l /var/log/squid3/access.log
SARG: getword backtrace:
SARG: 1:sarg() [0x4091c7]
SARG: 2:sarg() [0x4096c1]
SARG: 3:sarg() [0x405caa]
SARG: 4:/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7ff08ed3e76d]
SARG: 5:sarg() [0x408981]
SARG: Maybe you have a broken time in your access.log file
SARG: getword loop detected after 255 bytes.
SARG: Line=""
SARG: Record=""
SARG: searching for 'x20'
[/PHP]
[COLOR=#333333][FONT=sans-serif]

I've tried various Source and Destination variations as well as changing the permissions on the log files themselves.  This used to work when I had Sendmail installed but I recently switched to Postfix due to how complex Sendmail was and various other issues I was having (look at my other threads).

Please can someone tell me what's going on?
Thanks[/FONT][/COLOR]

---

### Post by tad1073 on 2013-05-09
Install webmin, enable the squid report generator module and see it the problem persists. I believe it will give you a definitive report on the errors and tell you how to fix them.

---

### Post by bullet333 on 2013-05-09
I have been using Webmin to troubleshoot this error.  That's where I'm getting the first error message from.

```

[COLOR=#333333][FONT=sans-serif]**Now generating Sarg report from Squid log file /var/log/squid3/access.log and all rotated versions ..**
[/FONT][/COLOR]

sarg -l /var/log/squid3/access.log 
mail: cannot send message: Process exited with a non-zero status
SARG: command return status 36
SARG: command: sudo mail -s "SARG report, Thu May  9 12:49:23 2013" 
"user@domain.com" <"/tmp/sarg/2013May08-2013May09/report"


[B].. Sarg failed! See the output above for details.
[/B]
```

---

### Post by bullet333 on 2013-05-13
Anyone have any ideas?

---

### Post by SeijiSensei on 2013-05-13
Well it does say:
> Maybe you have a broken time in your access.log file

Have you examined the file you are sending to SARG carefully?  Any non-standard lines?

---

### Post by bullet333 on 2013-05-14
I noticed that message as well but I wasn't sure what that meant.  I would check my access.log but it's over 28,000 lines long!

Although the format seems to be the same for most of the lines:
```

1368538402.987    303 127.0.0.1 TCP_MISS/302 621 GET http://go.microsoft.com/fwlink/? - DIRECT/65.55.58.195 text/html
1368538403.300    313 127.0.0.1 TCP_MISS/304 501 GET http://www.microsoft.com/atwork/community/rss.xml - DIRECT/65.55.57.27 -
1368538403.755    107 127.0.0.1 TCP_MISS/302 613 GET http://go.microsoft.com/fwlink/? - DIRECT/65.55.58.195 text/html
1368538403.936    178 127.0.0.1 TCP_MISS/302 530 GET http://iegallery.com/en/ie8slice/default.aspx - DIRECT/157.55.184.162 -
1368538404.091    147 127.0.0.1 TCP_MISS/200 2520 GET http://az307127.vo.msecnd.net/webslices/ie8? - DIRECT/65.54.93.135 text/html
1368538405.702    106 127.0.0.1 TCP_MISS/302 621 GET http://go.microsoft.com/fwlink/? - DIRECT/65.55.58.195 text/html
1368538405.797     93 127.0.0.1 TCP_MISS/304 501 GET http://www.microsoft.com/athome/community/rss.xml - DIRECT/65.55.57.27 -

```[COLOR=#FFFFFF][FONT=Helvetica]com/dl/slog.png[/img][/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-05-14
Since any valid line will begin with a one for the date field, try using

```
grep -v ^1 /var/log/squid/access.log
```

That will return any lines that do not begin with the numeral one.

---

### Post by bullet333 on 2013-05-14
The Webmin Squid Proxy Server Module shows the following for the Logging:
[IMG]http://filesmelt.com/dl/slog.png[/IMG]

---

### Post by SeijiSensei on 2013-05-14
I'm not sure what the point of showing that was.  I guess the log is in /var/log/squid3, not /var/log/squid.  I run CentOS on servers which differs from Debian/Ubuntu in terms of some log file names.  So just replace "/var/log/squid" with "/var/log/squid3" in the command above.

---

### Post by bullet333 on 2013-05-14
I posted that because I saw *formatting *options and wasn't sure if that's where my problem was.  Yes I'm using Squid3 and the directory is different.  I performed that command but it didn't seem to do anything.

I went ahead and decided to check syslog and noticed the following logs immediately when I ran "Generate Report":
```

May 14 11:00:01 Squid CRON[3156]: (root) CMD (/etc/webmin/bandwidth/rotate.pl)
May 14 11:00:01 Squid kernel: Kernel logging (proc) stopped.
May 14 11:00:01 Squid rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="2299" x-info="http://www.rsyslog.com"]$
May 14 11:00:01 Squid kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 14 11:00:01 Squid rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="3172" x-info="http://www.rsyslog.com"]$
May 14 11:00:01 Squid rsyslogd: rsyslogd's groupid changed to 103
May 14 11:00:01 Squid rsyslogd: rsyslogd's userid changed to 101
May 14 11:00:01 Squid rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 14 11:00:35 Squid postfix/sendmail[3229]: fatal: root@Squid(0): No recipient addresses found in message header

```

I'm confused as to why it's not finding a recipient in the message?

---

### Post by SeijiSensei on 2013-05-14
```
SARG: command: sudo mail -s "SARG report, Thu May  9 12:49:23 2013" 
"user@domain.com" <"/tmp/sarg/2013May08-2013May09/report"
```

It looks to be sending them to [email]user@domain.com[/email].  Did you change the delivery address when you configured SARG?

---

### Post by bullet333 on 2013-05-14
I removed my actual email from that message due to security reasons.  It does say my email, i.e. [EMAIL="bullet@email.com"]bullet@email.com[/EMAIL]

Also I don't think I've ever touched SARG.  I've only configured Postfix as far as I remember...couldn't seem to find the configurations?

---

### Post by bullet333 on 2013-05-17
bump

---

### Post by bullet333 on 2013-05-22
I bypassed the issue by removing the ability to send the SARG report to my email.  For some reason it didn't like email and it works fine now without that option.  We'll just have to use the web interface which is probably a better solution anyways.  Won't clog up out email!

---

