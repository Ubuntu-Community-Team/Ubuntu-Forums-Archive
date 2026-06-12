---
title: "Mail coming from monitoring tool not forwarded"
date: 2015-10-05
forum: Server Platforms
---

### Post by metan on 2015-10-05
Hi all

I got a monitoring tool (myvm0, Cloudera Manager to monitor Hadoop clusters). In mail alert option I configured all settings linked to my POSTFIX server (myvm7)
At the beginning, when I tried to click on the button "send test mail alert", I had the following error message in POSTFIX log :

```
Oct  5 22:16:37 myvm7 postfix/smtpd[3774]: connect from myvm0[172.16.0.4]
Oct  5 22:16:37 myvm7 postfix/smtpd[3774]: NOQUEUE: reject: RCPT from myvm0[172.16.0.4]: 454 4.7.1 <myaccountmoo2@gmail.com>: Relay access denied; from=<noreply@localhost> to=<myaccountmoo2@gmail.com> proto=ESMTP helo=<myvm0>
Oct  5 22:16:37 myvm7 postfix/smtpd[3774]: disconnect from myvm0[172.16.0.4]
```

Of course, after adding my subnet in mynetworks option in Postfix main.cf (instead of 127.0.0.1), now when I click on the send test mail alert button, I got a better message :

```
Oct  5 22:34:03 myvm7 postfix/smtpd[4022]: connect from myvm0[172.16.0.4]
Oct  5 22:34:03 myvm7 postfix/smtpd[4022]: AF7C5B055A: client=myvm0[172.16.0.4]
Oct  5 22:34:03 myvm7 postfix/smtpd[4022]: disconnect from myvm0[172.16.0.4]

```


BUT, I still not receive anything in my inbox! :( I confirm I'm able to send mail directly from the POSTFIX server using TELNET.

Do you what is going on ? what I missed ? what I would need to modifiy ?

THANKS A LOT FOR YOUR HELPFUL FEEDBACK, really need you ! ! ! :)

---

### Post by metan on 2015-10-05
hum...ok so it works when I try to send to a GMAIL address, but I receive nothing (even in spam) when I want to send in HOTMAIL accounts. Already met the case ?

---

