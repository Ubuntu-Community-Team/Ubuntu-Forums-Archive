---
title: "PHP Sendmail for web development environment"
date: 2007-02-18
forum: Server Platforms
---

### Post by mdbarton on 2007-02-18
Hi all

I've now got Apache / PHP / mysql installed on my Ubuntu desktop, so that I have my own private web development environment on my laptop.  Everything seems to be working well, except sendmail from PHP.  I've set the sendmail path in php.ini, but mails are not being sent.  I can see messages accumalating errors in /var/mail/www-data, but the body of the mails are 'mime encoded' so I cannot read them.  

I don't actually really need to have my websites set up locally on the laptop sending e-mails out, I just need to see the mails that would have been sent for testing purposes.  I know PHP/Sendmail will work on the various hosting companies servers that I use.

Is there a way of setting up apache/php/sendmail to just write the e-mails out to a file somewhere?  Any ideas?

cheers

Matt

---

### Post by mdbarton on 2007-02-20
I've found the answer.  sendmail queues e-mails in /var/spool/mqueue - if the mail cannot be sent, it gets stuck there.  Each email has a file starting 'df' and another 'qf'.  The df file contains the text of the e-mail and the qf file the headers and other info.  All I need to do is read the latest df file.  As I do not want to set my laptop up as a mail server, but want to grab any emails sent out by my PHP sites under development, this is perfect.

---

