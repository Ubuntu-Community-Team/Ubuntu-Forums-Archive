---
title: "error 554 Postfix Relay Access Denied"
date: 2009-03-30
forum: Server Platforms
---

### Post by joselee on 2009-03-30
I have installed Ubuntu Server 8.10 with postfix, bind9, mysql, apache,php, tomcat, openssd applications

I have configured Postfix with saslauth and tls, all users in the mail server can log in through ms outlook and roundcube web client,

I can send emails to existing domains like google, yahoo etc,

the mail server does not receive emails.

The mail server is behind a router which forwards all smtp packets to the localip of the mail server.

part of the /var/log/mail.log is
""
Mar 30 12:31:46 mail postfix/smtpd[6445]: NOQUEUE: reject: RCPT from rv-out-0708.google.com[209.85.198.248]: 554 5.7.1 <administrator@kec.or.tz>: Relay access denied; from=<chanangae@gmail.com> to=<administrator@kec.or.tz> proto=ESMTP helo=<rv-out-0708.google.com>
Mar 30 12:31:48 mail postfix/smtpd[6445]: disconnect from rv-out-0708.google.com[209.85.198.248]

""

The old mail server runnig redhat-sendmail works with the same settings inside out. 
Help is appriciated

---

### Post by hyper_ch on 2009-03-30
you can't send emails to google?

---

