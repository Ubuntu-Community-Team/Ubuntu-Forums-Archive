---
title: "Problems with mail server. How to succesfully set it up?"
date: 2011-05-18
forum: Server Platforms
---

### Post by barisurum on 2011-05-18
Hello; 
I've been dealing with php + mysql for some time and I haven't been able to send mail using the mail() function whatever I did. I installed the sendmail program and adjusted the php.ini file to point to the sendmail location (/usr/lib/sendmail) but it doesn't send mail to my gmail account.
 
When I execute the mailing php script, I see firefox appears to be doing something for a long time but when it ends and I check my mail, nothing has been sent. I also look at spam section but nothing there too. What may I be doing wrong or not doing at all? Thanks.

---

### Post by barisurum on 2011-05-19
bump

---

### Post by SeijiSensei on 2011-05-19
Start by looking at /var/log/mail.log.  What happens to the messages you try to send to gmail?

---

### Post by barisurum on 2011-05-19
Thanks! These are the errors I see when I attemp to send to one of my own websites:

> May 18 12:40:01 baris-desktop sm-msp-queue[5665]: My unqualified host name (baris-desktop) unknown; sleeping for retry
May 18 12:40:11 baris-desktop sm-mta[5636]: p4HHM9Vn009494: to=<nobody@tourguideinistanbul.com>, ctladdr=<www-data@baris-desktop> (33/33), delay=16:18:01, xdelay=00:03:09, mailer=esmtp, pri=4890368, relay=tourguideinistanbul.com., dsn=4.0.0, stat=Deferred: tourguideinistanbul.com.: No route to host
May 18 12:41:02 baris-desktop sm-msp-queue[5665]: unable to qualify my own domain name (baris-desktop) -- using short name

---

### Post by collisionystm on 2011-05-19
Deferred: tourguideinistanbul.com.: No route to host

---

### Post by collisionystm on 2011-05-19
[http://www.linuxquestions.org/questions/red-hat-31/sendmail-no-route-to-host-782468/](http://www.linuxquestions.org/questions/red-hat-31/sendmail-no-route-to-host-782468/)

Have a look at that

Or just google,

sendmail no route to host

---

### Post by SeijiSensei on 2011-05-20
The Postfix computer doesn't have a "fully-qualified domain name" like mail.example.com.  Remote servers won't accept mail from user@host addresses like www-data@baris-desktop.  Have you registered a domain?

You appear to be sending this message from a script within Apache.  Notice that the SMTP sender is "www-data".

---

