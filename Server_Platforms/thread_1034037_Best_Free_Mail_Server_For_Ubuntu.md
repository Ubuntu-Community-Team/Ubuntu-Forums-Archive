---
title: "Best Free Mail Server For Ubuntu"
date: 2009-01-07
forum: Server Platforms
---

### Post by Fireblazer on 2009-01-07
Hey,

I would like to setup a mail server so I can have a "*@fireblazer.net" address. I've been running Apache/PHP/MySQL for a while so I have experience in running servers, I just want to know which one would be the best mail server.

~ Fireblazer

---

### Post by ibutho on 2009-01-07
I don't think there is a best. The most common smtp servers are sendmail, postfix and exim. Any of them should be good enough. You may also need pop and imap servers and you can use dovecot and courier for this.

---

### Post by MAO on 2009-01-08
Zimbra is not the Best but Full functional [http://www.zimbra.com](http://www.zimbra.com)

My decision - Postfix, Dovecot, Horde, ClamAV, Amavis, SpamAssasin, PostfixAdmin and etc.

---

### Post by windependence on 2009-01-08
I'll second Zimbra, and also add Citadel to that list. the others by themselves are not a complete mail solution, and you will quickly find out just how fun it can be (NOT!) to get everything working in a complete package - OR you can install one of these in a half hour and be done.

-Tim

---

### Post by thefekete on 2009-01-08
If all you want is your own domain, it may be easier to get a google docs account. After that, you can either switch over when you're confident with your own server, or do a satellite setup where your personal server backs up your gmail or vice versa...

To answer your question though, I like postfix. Seems like the easiest to set up for me.

---

### Post by Fireblazer on 2009-01-08
Hey,

Thanks for all your suggestions, I think I'm going to look at Zimbra or Citadel. Also, how would Google Docs get me a domain, I thought it was just free web apps? Anyway, thanks again.

~ Fireblazer

---

### Post by hyper_ch on 2009-01-08
[http://www.google.com/apps/intl/en/business/index.html](http://www.google.com/apps/intl/en/business/index.html)

---

### Post by scorp123 on 2009-01-09
> **windependence said:**
> I'll second Zimbra +1!

Zimbra is nice. We use it too here.

---

### Post by linux_tech on 2009-01-09
[http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

---

### Post by linux_tech on 2009-01-09
Drupal may be another consideration

---

### Post by jrusso2 on 2009-01-09
There are so many Email servers for Linux its hard to say whats best.  But which ever one you choose it needs to be secured since people will try to hack or relay junk mail through it. 

So learn how to secure which ever one you decide on

---

### Post by martien on 2009-01-10
I dont like the packages like zimbra. I prefer to set whatever software i want.
For smtp i recommend postfix. For imap/pop3 server you can choose between courier and dovecot. Both courier and postfix have database support, so it should be easy for you to setup mail server.

---

### Post by charlesvallieres on 2009-01-10
Hi, maybe it won't answer your question...
If you own a domain, google has an app to get custom mail service.
[http://www.google.com/apps/intl/en/business/editions.html](http://www.google.com/apps/intl/en/business/editions.html)
Try it, it's awesome and it's free!

---

### Post by Fireblazer on 2009-01-11
Hey,

Thanks [charlesvallieres]("http://ubuntuforums.org/member.php?u=745535"), I'll check that out.
By database support, do you mean it will insert into a MySQL database?
Also, how hard would it be to just design my own? I'm pretty good at programming.
Anyway, thanks for all of yall's suggestions.

~ Fireblazer

---

### Post by albinootje on 2009-01-11
I recommend postfix with postfixadmin, and dovecot for imap/pop.

Sendmail and Exim are not at all easy imho (though I've heard that the commercial Sendmail is easy and comes with a GUI)
Qmail is pretty cool but not that very easy and flexible (even not with qmail GUI tools), and I don't like Zimbra and the Citadel suite.

The one thing I like about postfix is that the installation and configuration is straight-forward, and things like "transporting" email for a domain from one machine to another machine is really easy to understand and apply in the configuration files.

Just my 2 cents.
Kind regards from a happy postfix user :)

---

### Post by HermanAB on 2009-01-12
To me, Citadel is so easy to install, that using anything else just isn't worth the head-ache.  It takes about 20 minutes, which is unbeatable.

Cheers,

Herman

---

### Post by Greyed on 2009-01-12
> **albinootje said:**
> Qmail is pretty cool but not that very easy and flexible (even not with qmail GUI tools), 

qmail is a case study on how not to develop an MTA or a piece of FOSS software.

> The one thing I like about postfix is that the installation and configuration is straight-forward, and things like "transporting" email for a domain from one machine to another machine is really easy to understand and apply in the configuration files.

On the other hand its qmail-esque 1-program-per-task make smtp-time spam/virus filtering a mind bender.  Exim is a tad harder to set up but once set up the more advance stuff is relatively easy to perform.

FWIW I've been running my own mail domain for just over of 10 years now.  All 10 on Exim and the current chain is
Exim (MTA/MDA) w/SMTP time rejection
ClamAV (virus filtering)
SpamAssassin (spam filtering)
Dovecot (POP/IMAP)
Squirrelmail (webmail)

---

### Post by albinootje on 2009-01-12
> **HermanAB said:**
> To me, Citadel is so easy to install, that using anything else just isn't worth the head-ache.  It takes about 20 minutes, which is unbeatable.

I've tried the Citadel suite because I wanted to test a lot of groupware solutions, mainly for having a shared calendar (web and/or via thunderbird).
I found the installation of the Citadel suite not that difficult but the layout is too ancient looking. I cannot deliver that to my users.

And about the citadel smtp server, the 20 minutes is including imap/pop ?
I really want Maildir format mailboxes for my users, and after starting with postfixadmin years ago, I really favor the virtual mail users setup.
I can create mail-admins which can then create new mail-users, delete mail-users, create mail-aliases, edit mail-aliases etc all through a web interface. Awesome.

How does citadel handle that ? Can it work with LDAP or SQL ?
Just wondering.

---

### Post by albinootje on 2009-01-12
> **Greyed said:**
> qmail is a case study on how not to develop an MTA or a piece of FOSS software.

In my opinion you're doing injustice to the qmail project. Looking at the history of MTA it was a response to the security problems of the ancient Sendmail. Security in the very broad sense, not just about security exploits. Concerning that the Maildir format, which qmail uses by default, has been a very good new thing in computer history.

On the one hand it's a pity that Mr. Bernstein did use a restrictive license for qmail, but on the other hand it's a bit understandable that he didn't want the high quality code results to be forked so easily.
Since a while the license of qmail has changed, in the future the qmail installer would no longer be in the non-free section of Debian.

---

### Post by albinootje on 2009-01-12
> **Greyed said:**
>  [postfix] On the other hand its qmail-esque 1-program-per-task make smtp-time spam/virus filtering a mind bender.  Exim is a tad harder to set up but once set up the more advance stuff is relatively easy to perform. 

Configuring amavisd-new and postfix is really easy.
I don't like amavisd-new not so much myself, I'm using some spamfilter script to work with postfix, clamsmtp and spamassassin.

---

### Post by Greyed on 2009-01-12
> **albinootje said:**
> In my opinion you're doing injustice to the qmail project. Looking at the history of MTA it was a response to the security problems of the ancient Sendmail. 

Which does not alter my opinion one whit.  Yes, security was a problem in those days.  Regardless my statement stands that qmail is a case study in how not to write an MTA.  Its handling of mail is abysmal and while other MTAs, including Sendmail, have been able to adjust to the current spam laden climate qmail's architecture leaves it utterly incapable of sanely approaching the problem.  I think that, if nothing else, proves my point.  Just because it was implemented as a reaction to another MTA's poor security does not mean that its implementation is worth spit.

---

### Post by albinootje on 2009-01-12
> **Greyed said:**
> Which does not alter my opinion one whit.  Yes, security was a problem in those days.  Regardless my statement stands that qmail is a case study in how not to write an MTA.  Its handling of mail is abysmal and while other MTAs, including Sendmail, have been able to adjust to the current spam laden climate qmail's architecture leaves it utterly incapable of sanely approaching the problem.  I think that, if nothing else, proves my point.  Just because it was implemented as a reaction to another MTA's poor security does not mean that its implementation is worth spit.

When is the last time you looked at qmail ?
There's anti-spam software for it, e.g. : [http://www.spamdyke.org/](http://www.spamdyke.org/)
Or are you talking about build-in anti-spam measures as rejecting unknown hosts, invalid helo commands etc. ?
Qmail has, through time, gotten a lot of add-ons.

Also, ezmlm (related to qmail) was a really interesting project at the time where mailman was not that popular yet.

---

### Post by maxidrom11 on 2009-01-12
sendmail

---

### Post by shepherdzw on 2009-04-01
Do not Que Mail with SENDMAIL...Send Mail with Qmail.

:popcorn:

Otherwise i would encourage novice admins to use sendmail. It is very easy to use and configure but the weakness is that you really need to know what you do and read a lot of white papers.

Sendmail is a bad mta because if you create an email [email]user@yourdomain.com[/email] that user becomes a system user for your server. That can be really a mess if you create users with weak passwords. Good recipe for trouble.

Other wise Qmail is for the smart admins. However as bread and butter gets substitutes i guess your bun and margarine is POSTFIX or EXIM as an MTA.

---

### Post by HermanAB on 2009-04-01
Citadel is best for lazy admins.  It installs in 20 minutes and just works with zero maintenance.  Compared to Citadel, anything else is a total waste of time.

---

### Post by kvizz on 2009-04-08
zimbra is not just mail server, it's collaboration suite. we used to have postfix, dovecot etc. but now really happy with zimbra. and the migration was pretty easy enough, though 95% of my corporate desktops are running windows (and no questions with migration from evolution/ubuntu from other 5%)

---

### Post by saravananwhizrx on 2012-09-01
Hi all, I'm new to this.
I'm searching for an open source email server, which does has an API support and unix platform (must).

I did saw citadel, but i'm not sure which is the best, can anyone help me?

Thanks in advance.

---

### Post by LHammonds on 2012-09-01
Zimbra.  Take a look in my sig for a step-by-step guide on how I have installed it...which was to replace MS Exchange.

LHammonds

---

### Post by xdracco on 2012-09-02
my preference is postfix and courier-imap.

---

