---
title: "email server"
date: 2006-10-30
forum: Server Platforms
---

### Post by nebi on 2006-10-30
I have some problem when i setting up a email-server. I use postfix and courier. I can send mail local and over internet but i can only receive mail when i send local not from internet. I have open email port on my router(110 and 143).Postfix and courier use default settings. I have change the mx settings at my dns provider so it point to my server. So what have I done wrong ?

---

### Post by Pintel on 2006-10-30
Hi, that is not really an answer to your question, but have you tried the new service from google. Register and point your dns entries to google. You will have than a gmail account with your own domain. That saves a lot of trouble with setting up an own mailserver.
[https://www.google.com/a/](https://www.google.com/a/)

Pintel

---

### Post by foxylad on 2006-10-30
I would try to connect to your mail server from the internet, using telnet. This will tell you if the port is open and active.

```
[foxylad]$telnet your.mail.server 25
Trying 111.222.333.444...
Connected to your.mail.server.
Escape character is '^]'.
220 your.mail.server ESMTP Postfix
```
If you get the response above, your problem is a postfix setting (check main.cf). If you don't, it is a network problem - check router, firewall, and that postfix is running.

---

### Post by mtcook01 on 2006-10-30
Not sure if this helps at all, but I noticed you only opened 110 and  143.  Those ports are for pop and imap.  If you want to receive email for your .com .org etc..  then you will need to open up and forward port 25.  Thats the smtp port that your server is listening on.  To check the ports that your server is listening to, just open a terminal and type netstat -ant.  It should have something listening on port 25.

---

### Post by jimm on 2006-10-31
Hi,

Looks like you have one part of the puzzle sorted but not the critical part... you have POP and IMAP sorted, these are the local delivery end-points that your client use to **retrieve** mail. 

For sending and receiving of Internet mail you need a SMTP based Mail Transfer Agent (MTA) like SendMail, EXIM or Postfix. This listens on the SMTP port (25) for incoming mail and then attempts to deliver it to another MTA (ie somewhere else on the net or a relay) or locally if your server knows where to put the mail. Likewise recieving mail. Other MTA's on the net expect to send you mail via SMTP (to a server listening on port 25). 

So you need to install and configure an SMTP server on you box and open port 25 so that mail for your domain can be delivered.

Have a read on the net about Sendmail, EXIM or Postfix for more information... I probably did a terrible job of explaining it!

Thanks,
James

---

### Post by MJN on 2006-11-01
He's already got Postfix up-and-running! :)

As foxylad and mtcook said, it's looking like an incoming port 25 issue (i.e. not being forwarded by the router).

Mathew

---

### Post by nebi on 2006-12-01
I got everthing up and running but with exim instead . I had some small problem with exim but it was easy to fix after I reading the log file and some searching on google :)

Thanks for the help anyway :)

---

