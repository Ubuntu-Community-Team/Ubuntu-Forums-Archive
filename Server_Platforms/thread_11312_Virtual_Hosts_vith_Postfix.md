---
title: "Virtual Hosts vith Postfix"
date: 2005-01-15
forum: Server Platforms
---

### Post by KupernikuZ on 2005-01-15
Hi.
I'm hosting a few domains on my server at the moment (running RedHat). I want to change to Ubuntu, and at the moment I'm working hard to find out how to setup postfix to handle multiple hosts.  <-- That's what I wrote earlier today. 
I'm not sure how I setup Postfix on Ubuntu, cause the docs seems to be for an RedHat lookalike :-(

I need postfix to transport mails for about 10 users on 6 domains.
I also need a pop3 server. At the moment I'm using Qpopper on RedHat, bu I can't get i work on Ubuntu. 


Can someone give me a hint, om how I cant get those mailservers running on Ubuntu?

Or can someone give a hint to another mailserver, that can do the same?

Regards 
KupernikuZ

---

### Post by KupernikuZ on 2005-01-18
Well.. I got Postfix up and running now.
I can send mails from the outer world to the users on their domains, hosted on my server.
Had to set    relayhost=*my.isp.smtp.com* 
and wrote my own virtual file and made a virtual.db file.

The only problem now is, that i cant connect to my server from the WAN-side to my Ubuntu server on port 110 (pop3).
I tried by "telnet mail.mydomain.com 110" and the connection just refused.
When I'm trying it on my RedHat server Ive got "+OK Qpopper...."

Hmm....

---

### Post by cpinto on 2005-01-19
Checkout this howto:
[http://high5.net/howto/](http://high5.net/howto/)

it's really simple to follow and put your server up&running in no time (it's also very easy to maintain as well!)

---

### Post by JackDog on 2005-01-21
If you are setting up vhosting with postfix checkout this guide:
[http://www.gentoo.org/doc/en/virt-mail-howto.xml](http://www.gentoo.org/doc/en/virt-mail-howto.xml)

It shows you how to "easily" setup postfix, courier and mysql to all play nice. What you are left with is a DB backend that is very easy to add domains, users, and virtual addresses to. Its also automatic, no reloading. courier and postfix can both auth with the same mysql table. No need to create system users. Also, it shows you how to setup sasl so you can send mail remotely (STARTTLS + AUTH) without setting up an open relay. If you are in the mood you can also setup PAM to use the mysql table for a secondary auth so your users can login to the system. 

I have been running this setup for over a year with out a reboot or an outage from any of the components involved. I highly recommend it, makes management of the server an absolute breeze.

---

### Post by az on 2005-01-21
Ripped from another thread:

By default postfix listens only on localhost. You should look at /etc/postfix/master.cf

Re: Make Postfix Listen to Outside Connections 

[http://ubuntuforums.org/showthread.php?t=10781](http://ubuntuforums.org/showthread.php?t=10781)


You need to change 
127.0.0.1:smtp inet n -	 -	 -	 -	 smtpd
to
smtp inet n -	 -	 -	 -	 smtpd



ra1 rocks!

---

### Post by KupernikuZ on 2005-01-23
Thnx. Problem solved.
The alias file was hidden in the /etc, not in the /etc/postfix.
That was the first thing, and so it was allthrough: the postfix files in ubuntu was not always there where the postfix manual thought they were. That was the problem, could I see.

---

