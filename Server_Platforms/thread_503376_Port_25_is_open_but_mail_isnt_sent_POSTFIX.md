---
title: "Port 25 is open but mail isnt sent POSTFIX"
date: 2007-07-17
forum: Server Platforms
---

### Post by ankhmor on 2007-07-17
I have postfix installed on my computer. I opened my port 25 everywhere possible (or at least I think so). Postfix delivers mail locally and can accept mail.

HOWEVER IT DOESNT SEND MAIL TO OUTBOUND SERVERS.

In the mail.log file it says that connection timed out (port 25).

However when i do telnet localhost 25 I receive Connected to localhost and then 220 anton-desktop ESMTP Postfix (Ubuntu)

What can I do to make my server send mail to outbound servers?

---

### Post by Mr. C. on 2007-07-17
It is possible your ISP blocks outbound port 25.

Please show associated log entries from /var/log/maillog.

MrC

---

### Post by ankhmor on 2007-07-17
This is from my mail log:
```
Jul 17 21:25:26 anton-desktop postfix/pickup[5247]: 4B241C109: uid=1000 from=<anton>
Jul 17 21:25:26 anton-desktop postfix/cleanup[5524]: 4B241C109: message-id=<20070718012526.4B241C109@anton-desktop>
Jul 17 21:25:26 anton-desktop postfix/qmgr[5248]: 4B241C109: from=<anton@antonk.kicks-***.org>, size=306, nrcpt=1 (queue active)
Jul 17 21:25:56 anton-desktop postfix/smtp[5526]: connect to mxs.mail.ru[194.67.23.20]: Connection timed out (port 25)
Jul 17 21:25:56 anton-desktop postfix/smtp[5526]: 4B241C109: to=<ankhmor@mail.ru>, relay=none, delay=47, delays=17/0.01/30/0, dsn=4.4.1, status=deferred (connect to mxs.mail.ru[194.67.23.20]: Connection timed out)
```

And I have opened port 25 on my firewall (inbound and outbound) and on my 
NAT router (Unex).

---

### Post by Mr. C. on 2007-07-17
Try :

```
$ telnet mxs.mail.ru 25
```

If that times out, you are being denied access either by their server, or your ISPs firewall.

MrC

---

### Post by ankhmor on 2007-07-17
It seems that I'm being blocked (when i tried mx1.hotmail.com it said that the connection is refused).

[COLOR="Red"]So what do I do now?[/COLOR] I need my mail to get delivered.

---

### Post by Mr. C. on 2007-07-17
Many ISPs block outbound SMTP; if so, you will have to use their SMTP server.

Many mail servers block residential or dynamic ISP connections (I do), because they are major spam sources.  If you have such an IP, your best bet will be to use your ISPs SMTP server, change ISPs, or use a collocated host service.

MrC

---

