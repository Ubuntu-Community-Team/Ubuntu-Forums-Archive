---
title: "LAMP Multiple Quiestions"
date: 2009-04-08
forum: Server Platforms
---

### Post by DogoJosho on 2009-04-08
Hi,
I have multiple questions for LAMP server. 

I pretty much have the server up and running i just have some finishing touch questions.

First of all I'm running Apache 2.2.9, PHP 5.2.6 and MySQL 5.0.67

(ubuntu 8.10)

My questions are what I think simple

I want to know first of all, can i put a page up where my users can sign up for a user account so they can get into some of the features like e-mail?

And another question is how do I get my mail past my DynamicDNS server?

Web Address: [http://joshscommunity.zapto.org](http://joshscommunity.zapto.org)

Thanks,
Dogo Josho

---

### Post by hyper_ch on 2009-04-09
(1) you may want to have a look at the perfect server howto guides from falko over at [http://www.howtoforge.com](http://www.howtoforge.com)  -  especially the new ones dealing with ISPConfig 3

(2) to send email from a MTA on a dynamic server you will need to relay the email through an existing static email server - most likely your ISP.

---

### Post by vikto on 2009-04-09
Hi, i have a simple question. Installed ubuntu 2 days ago and lamp yesterday. I get this prompt Windown every time I try to open localhost/test.php "You have chosen to open" What should Firefox do with this file? Open with or Save file.
How do I associate my php files to open. Help will be appreciated.

---

### Post by DogoJosho on 2009-04-09
first of all thanks for the second posters help, but forthis guy:
> Hi, i have a simple question. Installed ubuntu 2 days ago and lamp yesterday. I get this prompt Windown every time I try to open localhost/test.php "You have chosen to open" What should Firefox do with this file? Open with or Save file.
How do I associate my php files to open. Help will be appreciated.
It menas you php-apache mod isnt configured with apache!
Check install guide for more help

---

### Post by Cretin_Yes on 2009-04-09
make sure you've restarted your apache daemon after installing PHP.  I had the same problem myself, but went a bit overboard for linux and rebooted (those windows habits!).  It worked fine for me after that.

---

### Post by daboroe on 2009-04-09
reconfigure the php stuff for apache. It is saying like the others have said that php and apache are not configured to talk to each other nicely.

---

