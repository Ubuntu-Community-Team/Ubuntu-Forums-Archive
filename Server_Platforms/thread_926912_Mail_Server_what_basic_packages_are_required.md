---
title: "Mail Server what basic packages are required"
date: 2008-09-22
forum: Server Platforms
---

### Post by ade234uk on 2008-09-22
I am putting together a small tutorial for myself on how to setup a very basic webserver. So far I have the webserver running with PHP, MySQL. I can access this locally and online too.

One thing that has always stumped me is setting up mail. 

I am looking for the very basic packages to get this running. I am not interested in Spam filters or anything like just yet. 

What are the two or three main packages needed so that I can 

1) Send Mail
2) Receive Mail

Once I have mastered this, I can then look at other things such as Spam filters etc....

Thank you

---

### Post by qstraza on 2008-09-22
well you need MTA, like sendmail or postfix... take a look at those packages.

---

### Post by schiznik on 2008-09-22
That covers sending mail (your MTA), you also need a MDA to receive mail, usually a POP3/IMAP server, such as dovecot or courier

---

### Post by HermanAB on 2008-09-22
...or just go here [http://www.citadel.org](http://www.citadel.org) - run the Easy Install script and about 20 minutes later you are done.

---

### Post by ade234uk on 2008-09-22
Thank you for your help. I will go with installing the packages bit by bit. The more I do the more I will learn from it.

---

### Post by baudday on 2008-09-22
This helped me a lot when I was setting up my mailserver...

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

