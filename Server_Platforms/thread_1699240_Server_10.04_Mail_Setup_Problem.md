---
title: "Server 10.04 Mail Setup Problem"
date: 2011-03-03
forum: Server Platforms
---

### Post by tangerine0469 on 2011-03-03
First off i want to say that I am a bit new to running a linux server. I have my server set up to host websites and am trying to host email as well. 

I did a bunch of searching on the web and i perused through the documentation that comes with ubuntu server, postfix and mysql and feel really lost...

I followed this tutorial: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and got through the basic setup including putting some email addresses, domains and aliases into the database.

I can telnet into localhost on 25 and can only get as far as "EHLO Mail.mydomain.com" after that i get an unresponsive telnet session.

Any suggestions as what i could be doing wrong? I know you probably need me to provide more information so just let me know what you need.

---

### Post by bsntech on 2011-03-03
I don't know if you are already set on using PostFix, but I have a solution that includes a crapload of functionality that I use my hosting systems.

I use the Exim4 mailing system and use a database that holds the locations of mailbox directories, aliases, etc.  It is incorporated into the horde webmail system.

[http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/312-howto-virtual-domains-with-apache2-mysql-dovecot-with-quotas-horde-vacation-passwd-imp4-k.html]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/312-howto-virtual-domains-with-apache2-mysql-dovecot-with-quotas-horde-vacation-passwd-imp4-k.html")

---

### Post by elico on 2011-03-03
did you by any chance copied the codes from the site?

you will might have problem because of that.

if you want to understand i really recommend the follow:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

just to make sure you can make your server run with no sophisticated settings.
then get into 
[http://www.kernel-panic.it/openbsd/mail/mail1.html](http://www.kernel-panic.it/openbsd/mail/mail1.html)
the only different  between OPENBSD and ubuntu is how you install the package
just use the 
[PHP]apt-get postfix courier-base courier-doc courier-imap courier-imap-ssl courier-pop courier-ssl courier-authlib courier-authlib-mysql courier-authlib-userdb postfix-mysql libsasl2-2 libauthen-sasl-perl[/PHP]

and you will might want to look at:
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

---

### Post by tangerine0469 on 2011-03-04
> **elico said:**
> did you by any chance copied the codes from the site?

you will might have problem because of that.

if you want to understand i really recommend the follow:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

just to make sure you can make your server run with no sophisticated settings.
then get into 
[http://www.kernel-panic.it/openbsd/mail/mail1.html](http://www.kernel-panic.it/openbsd/mail/mail1.html)
the only different  between OPENBSD and ubuntu is how you install the package
just use the 
[PHP]apt-get postfix courier-base courier-doc courier-imap courier-imap-ssl courier-pop courier-ssl courier-authlib courier-authlib-mysql courier-authlib-userdb postfix-mysql libsasl2-2 libauthen-sasl-perl[/PHP]

and you will might want to look at:
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

I had used some of the codes from the site but i have undone all of the changes that i made and started fresh with workaround, i get all the way up to telneting into the local host and i get an  error when i try to send the test email: postfix/smtpd[7767]: warning: connect #1 to subsystem public/cleanup: Connection refused.

---

### Post by tangerine0469 on 2011-03-04
This is the full error:

Mar  4 09:25:57 computercrasherz postfix/smtpd[7881]: warning: connect #1 to subsystem public/cleanup: Connection refused
Mar  4 09:26:07 computercrasherz postfix/smtpd[7881]: warning: connect #2 to subsystem public/cleanup: Connection refused
Mar  4 09:26:17 computercrasherz postfix/smtpd[7881]: warning: connect #3 to subsystem public/cleanup: Connection refused
Mar  4 09:26:27 computercrasherz postfix/smtpd[7881]: warning: connect #4 to subsystem public/cleanup: Connection refused
Mar  4 09:26:37 computercrasherz postfix/smtpd[7881]: warning: connect #5 to subsystem public/cleanup: Connection refused
Mar  4 09:26:47 computercrasherz postfix/smtpd[7881]: warning: connect #6 to subsystem public/cleanup: Connection refused
Mar  4 09:26:57 computercrasherz postfix/smtpd[7881]: warning: connect #7 to subsystem public/cleanup: Connection refused
Mar  4 09:27:07 computercrasherz postfix/smtpd[7881]: warning: connect #8 to subsystem public/cleanup: Connection refused
Mar  4 09:27:17 computercrasherz postfix/smtpd[7881]: warning: connect #9 to subsystem public/cleanup: Connection refused
Mar  4 09:27:27 computercrasherz postfix/smtpd[7881]: warning: connect #10 to subsystem public/cleanup: Connection refused
Mar  4 09:27:37 computercrasherz postfix/smtpd[7881]: fatal: connect #11 to subsystem public/cleanup: Connection refused
Mar  4 09:27:38 computercrasherz postfix/master[1804]: warning: process /usr/lib/postfix/smtpd pid 7881 exit status 1
Mar  4 09:27:38 computercrasherz postfix/master[1804]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

---

### Post by NetworkSlacker on 2011-03-07
HI there tangerine, I too have a mail server based off that tutorial([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)) and I would like to say that based on my own personal experience I had to redo it a few time until I got it right. If you having trouble with the basic set-up it is quite possible you missed a step(based on my own experience again) use the testing area of the guide to help you. 

As far as your logs go, where exactly are you seeing this? This could be some issue with your shorewall configuration. Here is something to note: shorewall acts a little differently than described in the documentation so be careful.

---

### Post by tangerine0469 on 2011-03-10
> **NetworkSlacker said:**
> HI there tangerine, I too have a mail server based off that tutorial([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)) and I would like to say that based on my own personal experience I had to redo it a few time until I got it right. If you having trouble with the basic set-up it is quite possible you missed a step(based on my own experience again) use the testing area of the guide to help you. 

As far as your logs go, where exactly are you seeing this? This could be some issue with your shorewall configuration. Here is something to note: shorewall acts a little differently than described in the documentation so be careful.

That was in /var/log/mail.log.

I ended up finding the problem...it seems that i am still not used to making sure user permissions are set correctly...once i reset them my email started flowing through. [email]j.stapleton@computercrasherz.com[/email] is a lagit email at last! :D
Thanks every one for your help!

---

### Post by Dutchbeer on 2011-05-24
> **tangerine0469 said:**
> That was in /var/log/mail.log.

I ended up finding the problem...it seems that i am still not used to making sure user permissions are set correctly...once i reset them my email started flowing through. [email]j.stapleton@computercrasherz.com[/email] is a lagit email at last! :D
Thanks every one for your help!



Got the same problem. how did you resolve it?

---

