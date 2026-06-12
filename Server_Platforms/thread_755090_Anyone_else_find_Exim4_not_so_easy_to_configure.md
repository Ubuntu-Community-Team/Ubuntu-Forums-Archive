---
title: "Anyone else find Exim4 not so easy to configure?"
date: 2008-04-14
forum: Server Platforms
---

### Post by voidPtr on 2008-04-14
I've configured Postfix in the past.  With all of the information on the web as well as a Postfix book, it was pretty straightforward and easy to grasp all of the concepts and set it up just how I wanted.  I may have spent 1 or 2 dedicated days to really get it down and understand the MTA.

Having recently purchased a Softlayer server running Debian Etch 4.0, I thought I'd give the default-installed Exim4 a try on the logic that if Debian uses that by default, it must be "good".  Everywhere you turn, Exim4 is being touted as "so easy" to configure, so I assumed it would be easy for me as well.

Yes, if the only thing you care about is which domains to receive mail for, which hosts to relay for, etc., then dpkg-configure exim4-config is super duper easy to use (but for that matter, so is the one for Postfix!).  

I understand how Debian has the monolithic / split options and how the main config file is produced.  My question regarding configuration is ... does anyone out there REALLY think editing the Exim4 config file is "easy"??  It looks like a nightmare to me.  Postfix is several orders of magnitude easier to configure in my opinion.  I referred to the "spec" on Exim4 thinking I could skim it and get my bearings, which ended up being in upwards of 400 pages.  I suppose if one dedicated a month to learning Exim4, maybe it would all make sense ... but I'm failing to see how super easy Exim4 is to configure.  The config file looked more like a source code file than a simple, easy to follow configuration file such as Postfix's master.cf. 

Yes, I will do the obvious and stick to what I know (Postfix), I just wanted to see if anyone else previously unexposed to Exim4 was up and running doing everything they could think of within a day or two (which is what it took for Postfix).  

Specifically, here are some things I can do easily in Postfix that I can't figure out in exim4:

- How to define an acceptable RCPT to list other than /etc/passwd.  As I see it, mail to irc, uudp, etc is accepted by Exim4 and left deferred (to be sent again and again for days consuming resources, why?).  In Postfix one just uses the local maps feature.

- How to define max mailbox size?  This is a simple one line config option in Postfix.

- Turning on anti-spam features and such seems to require writing complex code-like blocks of statements instead of simple switches like Postfix.

I realize this is an Ubuntu forum, but it's also, IMHO, a great forum to ask Linux related questions - and since Ubuntu comes from Debian, hey, whynot. :-)

Interested to hear experienced feedback from someone who has fiddled with both systems!

-vp

---

