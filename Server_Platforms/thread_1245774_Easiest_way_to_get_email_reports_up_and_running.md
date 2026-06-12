---
title: "Easiest way to get email reports up and running?"
date: 2009-08-20
forum: Server Platforms
---

### Post by nerr on 2009-08-20
Hey everybody, I'm almost embarassed to ask this, but whenever I attempt to use mail or mutt to send mail from my server to any other email inbox, it never gets received.  mutt logs the mail in the "sent" file in my home directory, but it never shows up in the mailbox on the other end.  I've never experimented with command-line mail before, but if I can make it work, the possibilities are endless!

I do use iptables, but even with all the rules flushed, no dice. What could be wrong?  I'm curious to know if the fact the mail is being sent "from" an address called "nerr@mydomain.hsd1.mi.comcast.net" could be the problem, since Comcast's server is listed instead of my own domain.   Can anybody point a new user in the right direction?  It'd be much appreciated.

Example commands I've tried:

```
df -Th | mail -s "testmail" me@mydomain.com
apcaccess status | mutt -s "testing" me@mydomain.com
```

---

### Post by andrew.46 on 2009-08-21
Hi nerr,

> **nerr said:**
> Hey everybody, I'm almost embarassed to ask this, but whenever I attempt to use mail or mutt to send mail from my server to any other email inbox, it never gets received.  mutt logs the mail in the "sent" file in my home directory, but it never shows up in the mailbox on the other end.  

You would normally use a sending agent like msmtp to actually *send* the mail that is composed by mutt. Do you have something like this in place? Once this is set you can reference it from your ~/.muttrc with:

```
set sendmail="/usr/bin/msmtp"  # Use msmtp rather than sendmail
```

which is my own setting. My apologies if you already have something like this in place :-).

Andrew

---

### Post by nerr on 2009-08-21
Actually I do not have anything like that in place.  Hahaha, see, I knew I was missing something.  I thought mail/mutt were all-in-one solutions, but I suppose I forgot that Ubuntu Server is only meant to have what you want to have on it, and not another load of software you might not need.

Thanks for the advice, I will have to do some work on it when I get home today.

---

### Post by grantemsley on 2009-08-21
In the windows world, it's normal for all mail programs to speak SMTP directly, and be configured to send through your email provider's SMTP server.

In the linux world, your computer runs it's own mail server and every program uses that.  The mail server is either configured to send out through the internet directly to the recipient, or (in the case of a home server, especially ones with a dynamic IP address as they are usually in spam blacklists) to send through your email or ISP's SMTP server.

The great thing about this is you only have to set that up once - then every program on the system can send mail.

---

### Post by wplate on 2009-08-21
> or (in the case of a home server, especially ones with a dynamic IP address as they are usually in spam blacklists) to send through your email or ISP's SMTP server.

I am setting up an Ubuntu server that sits behind our router with a private IP address for intranet access.  Reading your post it sounds like I need to configure sendmail to send mail via our email host's SMTP server (because right now the one test email I've sent is stuck, deferred, in the queue).  How do I configure this?

I have Ubuntu 9.04 installed with webmin.

---

### Post by andrew.46 on 2009-08-21
Hi grantemsley,

> **grantemsley said:**
> In the windows world, it's normal for all mail programs to speak SMTP directly, and be configured to send through your email provider's SMTP server.

Mind you I believe that newer versions of mutt can be compiled with direct smtp support but I will admit that I have not experimented with this, for the most part because I am a firm believer in the old ways :-). And of course mutt supports IMAP as well these days....

> In the linux world, your computer runs it's own mail server and every program uses that.  The mail server is either configured to send out through the internet directly to the recipient, or (in the case of a home server, especially ones with a dynamic IP address as they are usually in spam blacklists) to send through yourr email or ISP's SMTP server.

I have always been too lazy to set this all up but perhaps one day :-). The lazy linux way to do this has been to set up a small Mail Sending Agent (MSA) such as ssmtp, msmtp or esmtp and probably a few others I cannot think of and leave an *external *server to do the grunt work. An example on these forums is this guide:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

But my hat is off to anybody who sets the whole thing up *properly*. Perhaps when I have my next vacation I should too...

Andrew

---

### Post by cariboo on 2009-08-22
Install logwatch, and it will automagically install an MTA for you, it will even pop up an ncurses app that will make setting it up pretty easy.

---

