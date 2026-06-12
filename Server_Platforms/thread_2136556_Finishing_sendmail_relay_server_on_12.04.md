---
title: "Finishing sendmail relay server on 12.04"
date: 2013-04-18
forum: Server Platforms
---

### Post by WhatAreTheStandards on 2013-04-18
Hello Ubuntu folks,

I'm trying to finish setting up sendmail on my Ubuntu 12.04 web server to relay emails sent from other servers of mine.  The reason:  The other servers need to send emails on behalf of the domain used by the web server.  So, I figured that, in order to help those emails avoid being spammed (since those servers know nothing of the domain), I'd just relay those mails to the sendmail relay server on my Ubuntu web server.

I believe I have the other servers set up correctly (adding the domain next to "DS" in [FONT=courier new]/etc/mail/sendmail.cf[/FONT]).  Whenever I test send an email, I can see that it is indeed relayed to the Ubuntu web server.

However, I recieve a "connection refused" from the Ubuntu server ([FONT=courier new]stat=Deferred: Connection refused by [IP_ADDRESS][/FONT]). On the Ubuntu server, I edited the [FONT=courier new]/etc/mail/access[/FONT] file to include the other servers IP addresses with "RELAY" next to them:  [FONT=courier new]<ip_addres>  RELAY[/FONT].  I also regenerated the .db and restarted sendmail.

There must be a step that I'm missing.  I just need to be able to tell the Ubuntu server to accept emails from my other servers and relay them.  Can anyone provide any suggestions?

Thank you!

---

### Post by duesentriebchen on 2013-04-18
Hy.

Can you post the output of ```
sendmail -v yourname@yourdomain.tld
``` on your 12.04 Webserver

Can you also post the output of ```
tail -f /var/log/syslog
``` on the other server of yours

---

### Post by SeijiSensei on 2013-04-18
In sendmail.cf on the relay host, check to see whether sendmail is only listening on the localhost interface with address 127.0.0.1 like this:
```
[s]O DaemonPortOptions=Port=smtp,Addr=127.0.0.1, Name=MTA[/s]
```

Remove the "Addr=127.0.0.1," entry and use this instead:
```
O DaemonPortOptions=Port=smtp,Name=MTA
```

If you [build sendmail.cf from sendmail.mc]("http://manpages.ubuntu.com/manpages/natty/man8/sendmailconfig.8.html"), then make sure your sendmail.mc has this line at the bottom:
```
DAEMON_OPTIONS(`Port=smtp, Name=MTA')
```
with no reference to 127.0.0.1.

---

### Post by WhatAreTheStandards on 2013-04-19
Hello everyone.  With your suggetsions, I think I've solved it.  I have some output to share, but I may not have the exact combination that you were asking for...

Here's the output when calling [FONT=courier new]sendmail -v[/FONT] from my other server (the one that is sending email to be relayed on the Ubuntu server - it is **CentOS**, FYI):

[FONT=courier new]WARNING: local host name (PROD-asterisk3) is not qualified; see cf/README: WHO AM I?[/FONT]
[FONT=courier new]I'm sending this mail for the forums![/FONT]
[FONT=courier new]<<my email>>... Connecting to [127.0.0.1] via relay...[/FONT]
[FONT=courier new]220 PROD-asterisk3 ESMTP Sendmail 8.13.8/8.13.8; Thu, 18 Apr 2013 20:17:34 -0700[/FONT]
[FONT=courier new]>>> EHLO PROD-asterisk3[/FONT]
[FONT=courier new]250-PROD-asterisk3 Hello server.take2hosting.com [127.0.0.1], pleased to meet you[/FONT]
[FONT=courier new]250-ENHANCEDSTATUSCODES[/FONT]
[FONT=courier new]250-PIPELINING[/FONT]
[FONT=courier new]250-8BITMIME[/FONT]
[FONT=courier new]250-SIZE[/FONT]
[FONT=courier new]250-DSN[/FONT]
[FONT=courier new]250-ETRN[/FONT]
[FONT=courier new]250-DELIVERBY[/FONT]
[FONT=courier new]250 HELP[/FONT]
[FONT=courier new]>>> MAIL From:<root@PROD-asterisk3> SIZE=38[/FONT]
[FONT=courier new]250 2.1.0 <root@PROD-asterisk3>... Sender ok[/FONT]
[FONT=courier new]>>> RCPT To:<<my email>>[/FONT]
[FONT=courier new]>>> DATA[/FONT]
[FONT=courier new]250 2.1.5 <<my email>>... Recipient ok[/FONT]
[FONT=courier new]354 Enter mail, end with "." on a line by itself[/FONT]
[FONT=courier new]>>> .[/FONT]
[FONT=courier new]250 2.0.0 r3J3HYdw016471 Message accepted for delivery[/FONT]
[FONT=courier new]<<my email>>... Sent (r3J3HYdw016471 Message accepted for delivery)[/FONT]
[FONT=courier new]Closing connection to [127.0.0.1][/FONT]
[FONT=courier new]>>> QUIT[/FONT]
[FONT=courier new]221 2.0.0 PROD-asterisk3 closing connection[/FONT]

Here is the result from [FONT=courier new]/var/log/maillog[/FONT] (there is no syslog on this CentOS server):

[FONT=courier new]Apr 18 20:21:33 server sendmail[16660]: r3J3HYdw016471: to=<<my email>>, ctladdr=<root@PROD-asterisk3> (0/0), delay=00:03:59, xdelay=00:00:00, mailer=relay, pri=210315, relay=<<[Ubuntu IP]>> <<[Ubuntu IP]>>, dsn=4.0.0, stat=Deferred: Connection refused by <<[Ubuntu 12.04 relay server IP]>>[/FONT]


OK, I then made the DaemonPortOptions as suggested above.  Actually, this is what mine looks like now (I just removed the 127.0.0.1 address):  [FONT=courier new]DaemonPortOptions=Family=inet,  Name=MTA-v4, Port=smtp[/FONT]

That produced some new results when I tested again.  I basically got the same output from [FONT=courier new]sendmail -v[/FONT], but [FONT=courier new]/var/log/maillog[/FONT] on CentOS was different:

[FONT=courier new]Apr 18 21:45:01 server sendmail[18320]: r3J4ix8q018318: to=<<my email>>, ctladdr=<root@PROD-asterisk3> (0/0), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=120356, relay=<<[Ubuntu IP]>> <<[Ubuntu IP]>>, dsn=5.1.8, stat=User unknown[/FONT]


Progress!  Then I looked at [FONT=courier new]/var/log/mail.log[/FONT] on Ubuntu ([FONT=courier new]syslog[/FONT] didn't really have anything useful):


[FONT=courier new]Apr 18 21:45:01 frontend sm-mta[4571]: r3J4j0Lr004571: ruleset=check_rcpt, arg1=<<my email>>, relay=<<CentOS IP(separated with dashes!)>>.take2hosting.com [<<CentOS IP>>], reject=553 5.1.8 <<my email>>... Domain of sender address root@PROD-asterisk3 does not exist[/FONT]

I guess that makes sense because it's just using the hostname (PROD-asterisk3) as the sender and sendmail was saying that it didn't recognize it so it was rejected.  So, I ran another test and specified my domain as the sender.  Seems it worked!  From  [FONT=courier new]/var/log/mail.log[/FONT] on Ubuntu:

[FONT=courier new]Apr 18 22:06:59 frontend sm-mta[5490]: r3J56v4Z005488: to=[/FONT][FONT=courier new]<<my email>>[/FONT][FONT=courier new], delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=120501, relay=gmail-smtp-in.l.google.com. [74.125.141.26], dsn=2.0.0, stat=Sent (OK 1366348019 vu9si11009195pbc.158 - gsmtp)[/FONT]

I *think* that's all I need to do.  Wow, great suggestions!  Thank you.  I learned a lot.  Let me know if I missed something though!  Thanks!

---

### Post by &amp;rei on 2013-09-14
Hi.

Just to confirm this thread helped me. My changes to the original sendmail.mc:

dnl DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp')dnl

dnl DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, Addr=127.0.0.1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission')dnl

Thank you folks!

Andrei

---

### Post by WhatAreTheStandards on 2013-09-14
:) Awesome, glad to hear it.

---

