---
title: "Mail Server Setup"
date: 2008-06-25
forum: Server Platforms
---

### Post by rdretina on 2008-06-25
Hello all,

I'm trying to configure Ubuntu Server 8.04 as an email server, but I'm not sure where to begin. I used tasksel to install the mail server packages, but I couldn't see any feedback on what packages were installed or how to configure them.

I searched the forums and looked at the Ubuntu Server Guide, but I'm still pretty lost. Could anyone point me to some documentation that explains what tasksel installed for me and how to configure it?

---

### Post by Buffalo Soldier on 2008-06-25
This would probably be a good place to start -> [https://help.ubuntu.com/8.04/serverguide/C/email-services.html](https://help.ubuntu.com/8.04/serverguide/C/email-services.html)

My personal preference is look for the official guide. When there's no official guide, then only I'll start searching at other places (howtoforge, debian wiki and etc).

---

### Post by rdretina on 2008-06-25
Thanks, Buffalo. I wasn't sure if the packages listed in the server guide were those that were installed with tasksel, but so far it looks like they are. Thanks for the direction!

---

### Post by q.dinar on 2008-07-16
hello.
i am not starting new topic. what should i do better?
title of this topic is good for my words/topic/theme.

today i very long time tried to make a mail server.

is here any several-click and write my username and password install?
what is the easiest install?

i have now "completely remove"d what i installed, because i had made many things incorrect i think.

now i have this plan. for first step i want just try to make pop3 server to which i could connect with a e-mail client - evolution or opera there i have installed.

i have ip address and domain name. no mx record. only an A record. i've read that if there is not any MX record then A record should work.

this server is this computer i am sitting at - desktop. ubuntu 7.10.

---

### Post by HermanAB on 2008-07-16
The problem is that most mail systems are built from a collection of Lego blocks and integrating it all is a chore and can take a week or two to set up.

A better option is to install Citadel, which is all in one and Just Works (TM). Go to [http://www.citadel.org](http://www.citadel.org) and run the Easy Install script and you should have a complete mail system in about 20 minutes.

Cheers,

Herman

---

### Post by windependence on 2008-07-16
Herman is right here. You will beat yourself up here trying to get everything right if you are fairly new to Linux. In fact even us seasoned veterans aren't too pleased with the prospect of putting all that stuff together.

I prefer Zimbra but Citadel is equally as good. Your choice.

-Tim

---

### Post by q.dinar on 2008-07-16
application that comes from special place for this version os and almost all other applications are in that place, that should be configured...
i still do not want citadel nor zimbra.
thanks.
i still hope i'll make it..

i'm planning to report here questions that will appear during installation...

1. may be that absence of mx record cause problem?



i think first step should be dealing with smtp. because as i know it is being used with pop3 and imap.

2. why smtp is being used though as i know smtp can be turned off and only pop3 or only imap4 can be used instead of it.

3. what smtp to use if should use it? there are in synaptic:smtpd, ssmtp, qpsmtp, proxsmtp, nbsmtp, msmtp-mta, msmtp, esmtp-run, esmtp, clamsmtp.

---

### Post by q.dinar on 2008-07-16
not only that. i have just searched "smtp" in names and descriptions, also there are:
courier-mta, courier-mta-ssl, exim-daemon-heavy(?), gnunet(?), mailfront(?), nail, sendmail, spampd, xmail, zope-securemailhost(?).

---

### Post by q.dinar on 2008-07-16
4. only nail support utf-8(unicode)?

---

### Post by q.dinar on 2008-07-27
what does install tasksel when installs mail-server?

---

### Post by q.dinar on 2008-07-27
not. it is regarding/relating "mail" it supports unicode, i think.

---

### Post by CaptSaltyJack on 2008-08-30
> **HermanAB said:**
> The problem is that most mail systems are built from a collection of Lego blocks and integrating it all is a chore and can take a week or two to set up.

Really?  I'm far from a Linux expert, and setting up a mail server was as easy as "sudo apt-get install exim4 exim4-config" then "sudo dpkg-reconfigure exim4-config", setting it up as a smart host, answering a few questions, and bam, it's done.  On top of that, "sudo apt-get install greylistd" and now I've got a nice anti-spam mechanism as well.

How does that take a week or two?

---

### Post by windependence on 2008-08-30
Look, if you aren't familiar with mail server configuration, and even if you are and you don't do it everyday, the package deals are just much easier. Do we have to split hairs here? You're gonna flame me for this but Exim is not necessarily main stream either. Most people use Postfix with some form of POP3 or IMAP server. That can be quite a bear to set up correctly. We are just givng them options just as you are.....

-Tim

---

### Post by CaptSaltyJack on 2008-08-30
I understand, Tim.  It all boils down to user preference.  For me personally, I found Postfix not so easy to set up, and Exim was a breeze.  And if I want IMAP, I just install dovecot.  I haven't tried the packaged ones like Zimbra or Citadel, so honestly I can't comment on those, but I'm sure they're both super easy to set up compared to Postfix or Exim.

---

