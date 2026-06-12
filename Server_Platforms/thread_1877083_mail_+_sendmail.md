---
title: "mail + sendmail"
date: 2011-11-07
forum: Server Platforms
---

### Post by zalix on 2011-11-07
hello

 I am within a poltergeist, or at least I think ..

 I installed sendmail + sendmail.cf to send email. Using the mail command, and the mail is sent properly because localhost sendmail default mode.

 The moment I edit sendmail.cf the DS field in the file, specifying the relay to send mail (with restart sendmail process), the operation of mail remains inviariato ... always use localhost as a relay.

 I followed the manual that wants to be changed sendmail.mc file and then run the command:
```

 m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf 

```log:

```
Nov  7 16:24:04 xxx sendmail[2537]: pA7FN4rM002537: from=root, size=55, class=0, nrcpts=1, msgid=<201111071523.pA7FN4rM002537@xxx.xxx.com>, **relay=root@localhost**
Nov  7 16:24:04 xxx sendmail[2537]: pA7FN4rM002537: to=xxx.xxx@xxx.com, delay=00:01:00, mailer=esmtp, pri=30055, dsn=4.4.3, **stat=queued**
```more then if I run:

```
#mailq
/var/spool/mqueue is empty
        Total requests: 0
```I enter the server as a relay is always in my management, but the problem is not on this mail server, but on the server running sendmail + mail that can not use anything outside localhost ..

 help me .. :confused:

---

### Post by SeijiSensei on 2011-11-08
First, make sure you can actually see the relay. From the box running sendmail try running "telnet relay.example.com 25" with the actual relay host name substituted for "relay.example.com".  The server should reply with a banner.  If so, make sure it will accept a message from you like this:

```

[banner from remote server]
**ehlo my.server.name**
[server should respond OK]
**mail from: you@yourdomain.com**
[OK]
**rcpt to: someone@someotherdomain.com**
[OK]
**data**
[server responds]
[B]Type your test message here.
.[/B]
[server responds]
quit

```

The line with a single dot is required.  I've bolded the lines that you type for clarity.

Are you sure your Internet service permits outbound connections on port 25?

---

### Post by zalix on 2011-11-09
hello,
 thanks for the answer.

 I solved the problem. It was the DNS. the server could not resolve the target domain with the DNS. When I sent an e-mail, sendmail is not able to access a DNS, used as a relay to localhost.

 after changing firewall policies, sendmail still has forwarded all mail in the spool

Alessio

---

