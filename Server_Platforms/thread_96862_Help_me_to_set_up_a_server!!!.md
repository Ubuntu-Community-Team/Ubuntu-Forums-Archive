---
title: "Help me to set up a server!!!"
date: 2005-11-29
forum: Server Platforms
---

### Post by johnwillis on 2005-11-29
I want the following services:

Web Site - Apache (done)

FTP Site - VSFTPD (done)

Telnet / SSH - Done

Mail Server - stuck!

I would really appreciate it if someone could tell me in step by step guide how to install and configure a mail server (pop3/smtp and webmail access) as well as how to get the servers installed. Im quite familiar with command line, and I know linux quite well. So terms like CHMOD are not new. Or things editing .conf files are fine. I just need to know how to do it. And i want it to be as simple as adding a user under ubuntu will also create a login and mail box for a user.

Many thanks for your help

John

---

### Post by cactus on 2005-11-29
I would recommend postfix for the MTA (smtp), and dovecot works great for pop3/imap.
With imap in place, you can easily setup squirrelmail for webmail.

---

### Post by ndtoan13 on 2005-11-29
What about sendmail? Anyone have tried it yet?

---

### Post by greenway on 2005-11-29
I haven't worked through it yet but it's supposed to be a very decent howto:

[How to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix/")

goodluck!

---

### Post by ndtoan13 on 2005-11-29
Thank you for your links, but this is not sendmail (from sendmail.org).
Because this is my first time with ubuntu, so install an email server like sendmail is hard work. And I need some help on sendmail (Courier IMAP & Squirrel WebMail is good but it is not easy for me to find out the similation).
Err, sorry about my English, it is not my native, so maybe it does not have clearly meanning.

---

### Post by J.C. Denton on 2005-11-30
Sendmail is a nice MTA, but it's fairly complex and hard to "dive into."  If you're really interested in learning all its complexities ;), I'd recommend the O'Reilly Sendmail [book](http://www.oreilly.com/catalog/sendmail3/index.html).  That's how I got most of the basics down pat.  The [FAQ](http://www.sendmail.org/faq/) maintained by the Sendmail folks is also pretty helpful.

If you don't mind me asking.  How many users will you be serving with this MTA? If it's a small-moderate sized setup, I'd go along with the other posters in recommending [Postfix](http://www.postfix.org).  It's easy to use, has most of the sendmail equivalents, and just seems to work well (mostly out of the box).

Hope this helps :)!

---

### Post by nocturn on 2005-11-30
[QUOTE=ndtoan13]What about sendmail? Anyone have tried it yet?[/QUOTE]

Sendmail has a bad reputation regarding security... that is why people are running to Postfix/Exim etc.

---

### Post by ndtoan13 on 2005-11-30
Why you said :
[QUOTE=nocturn]Sendmail has a bad reputation regarding security... that is why people are running to Postfix/Exim etc.[/QUOTE]
I mean where is the *bad reputation regarding security*?
I agree it is not good QoS, but it is good choice for huge users MTA.

My user is rasing year by year. I pretend to server about 5-10 thoundsand users for some years (they are all my students), then the number will be much more, so I have to work with this *complex and hard to "dive into." * :( 

I am also working on other MTA like Mdaemon (windows) ... but with the huge users, I have to try some opensoure MTA and of course the QoS is not so good!

Thank you Denton for your recommend book. I will get one and try my first step with Sendmail.

Another thing I wonder is about spam mail, do anyone have experience about this? Now I have to make spam filter rule by .. hand (this is because I have no rule for anycase!!:confused: ), and it is not enough to prevent such a thing like spam email.

---

### Post by J.C. Denton on 2005-11-30
[QUOTE=ndtoan13]Why you said :

I mean where is the *bad reputation regarding security*?
I agree it is not good QoS, but it is good choice for huge users MTA.

My user is rasing year by year. I pretend to server about 5-10 thoundsand users for some years (they are all my students), then the number will be much more, so I have to work with this *complex and hard to "dive into." * :( 

I am also working on other MTA like Mdaemon (windows) ... but with the huge users, I have to try some opensoure MTA and of course the QoS is not so good!

Thank you Denton for your recommend book. I will get one and try my first step with Sendmail.

Another thing I wonder is about spam mail, do anyone have experience about this? Now I have to make spam filter rule by .. hand (this is because I have no rule for anycase!!:confused: ), and it is not enough to prevent such a thing like spam email.[/QUOTE]
The [Wikipedia](http://www.wikipedia.org) [article](http://en.wikipedia.org/wiki/Sendmail#Vulnerabilities) on sendmail details some of the security vulnerabilities.  For spam filtering, I'd look at [SpamAssassin](http://spamassassin.apache.org/), regardless of what MTA you end up using.

---

### Post by LordHunter317 on 2005-11-30
Sendmail has a formerly poor security track record, is impossible hard to configure and is slower than just about everything else.

It is not to be used for new setups.

Use postfix or Exim4.

---

### Post by Warpnow on 2005-11-30
I am also new to Ubuntu, and relatively knew to linux. I reccomend the linux cookbook by O'reilly, it has step by step directions for a lot of things, including how to setup a postfix server with pop3, imap and webmail.

---

### Post by davebradford on 2005-12-01
the best way to setup an e-mail server is to use q-mail and theres a pretty damn good guide just go to debian based systems.

[http://www.qmailrocks.org/](http://www.qmailrocks.org/)

---

### Post by LordHunter317 on 2005-12-01
No, qmail is buggy, obsolete, and refuses to be maintained by the only person who can.

Qmail is not to be used for new installs either.

**Use Postfix, or exim4**.

---

### Post by bluefrog on 2005-12-03
[http://www.howtoforge.com/taxonomy_menu/1/4](http://www.howtoforge.com/taxonomy_menu/1/4)


postfix clamav courier spamassin (you're not obliged to install mysql...)

---

### Post by hagen00 on 2005-12-05
Use Postfix.

[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

This link should give you more than enough help.

---

### Post by Jimzilla on 2005-12-08
[FONT="Arial"][SIZE="4"][COLOR="Blue"]Theres a very good howto on this here [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier")I went with this and simply edited the mysql tables to taste.[/COLOR][/SIZE][/FONT]

---

