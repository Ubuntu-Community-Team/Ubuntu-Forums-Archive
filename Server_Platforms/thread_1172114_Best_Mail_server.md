---
title: "Best Mail server?"
date: 2009-05-28
forum: Server Platforms
---

### Post by ZeleD on 2009-05-28
Hey guys'n'gals!
 
I was wondering if there was any mailserver that works best.
 
I know qmail, and have been using it for the past years on my old *nix box, but I failed to get spam and virus scanning to work with it (was a Suse OS 10).
 
I have multiple domains so it must support virtual domains, pop3 and webmail.
 
It must have some sort of support with spam checking either using spamassasin or any other similiar OpenSource project.
 
Virus checking option is also something I need.
 
It doesnt have to be RPM packed.

---

### Post by regala on 2009-05-28
> **ZeleD said:**
> Hey guys'n'gals!
 
I was wondering if there was any mailserver that works best.
 


postfix

---

### Post by iponeverything on 2009-05-28
I like qmail first and postfix second. I had no problems getting the virus scanning working with qmail.. It has a been a few year since I set it up and don't remember what I was using to scan to the mail.

---

### Post by grantemsley on 2009-05-28
I'd vote for postfix as well.  Mostly because it's the one I've found the most guides for configuring.

Postfix only handles the SMTP side of things.  For pop/imap, I use courier.  Most webmail clients will talk IMAP to the server on localhost, so that is easy to do.  Squirrelmail or Roundcube are two I've used.

Spamassassin can do your spam filtering.  You can get it up to tag emails as they come in (I can lookup how to set it up if you need, just PM me).

---

### Post by ZeleD on 2009-05-28
Thanks for responses.
 
I will give postfix a chance and see if I can get it working :)
 
QMail got its own pop3d and I already use squirrelmail for my current system.
 
I've checked postfix.org to get initial data, but I failed to see how users and domains are created.
 
Is it through the *nix users system ? separate database ? Any webenabled admin tools for it or do I need to use shell for it ?

---

### Post by grantemsley on 2009-05-28
I do most of my configuration through ISPConfig, which will manage postfix users.

---

### Post by regala on 2009-05-28
> **ZeleD said:**
> Thanks for responses.
 
I will give postfix a chance and see if I can get it working :)
 
QMail got its own pop3d and I already use squirrelmail for my current system.
 
I've checked postfix.org to get initial data, but I failed to see how users and domains are created.
 
Is it through the *nix users system ? separate database ? Any webenabled admin tools for it or do I need to use shell for it ?

you add some lines in /etc/postfix/main.cf

virtual_alias_domains = my.virtual.domain
virtual_alias_maps = hash:/etc/postfix/my.virtual.domain

in /etc/postfix/my.virtual.domain you put the pairs "alias address" one by line, and run postmap /etc/postfix/my.virtual.domain to regenerate the my.virtual.postfix.db file. Reload postfix configuration, and you're done.

---

### Post by tricolorpoa on 2009-05-28
Why didn't try zimbra?

[http://www.zimbra.com](http://www.zimbra.com)

---

### Post by LEO_Servers on 2009-05-28
If your using suse 0S 10.what then you are probly using e-directory if so have you thought about using group wise?

---

### Post by rhcm123 on 2009-05-28
If your on ubuntu, just copy-paste the commands from the documentation:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

It gives a rundown on all mail servers kept in the repository. Postfix is the default MTA for ubuntu, and it is heavily supported, with blacklisting, spam filtering, virus scanning, etc. Dovecot is the primary server for ubuntu, but i prefer courrier for ease to setup and virtual users support.

try whatever you feel's best after reading the guide, it's what i used to set it up. and if you need web access, use squirrelmail (see bottom of guide) as OpenWebMail is now defunct.

---

### Post by phoenixlipo on 2009-05-29
Hi,

Best Mail Server is an ultra fast SMTP/POP3 server program. You can send mail from any mail client that is complaint with SMTP protocol using this server. You can also configure it to be your local mail server. It will accept mail on your behalf and store it, until your users will retrieve it using POP3. It is simple, light-weight, powerful, and contains a lot of security features and options that allow you to protect the server from DDoS attacks as well as safely block spam and spammers. SMTP and POP3 servers work as NT services therefore they will keep working in the logoff mode. You can have multiple SMTP gateways in your server if you travel a lot with your laptop.

thanks,

---

### Post by ZeleD on 2009-05-29
> **LEO_Servers said:**
> If your using suse 0S 10.what then you are probly using e-directory if so have you thought about using group wise?
 
Being a Novell server administrator in my day job, groupwise would be my preferred system.
 
One huge disadvantage of the Groupwise system is the pricing.

---

### Post by LepeKaname on 2009-05-29
I can't say which is better, but within the FREE alternatives, I have had a better experience with postfix (relatively easy and well supported). I have 4 servers with postfix and so far no problem.

---

### Post by LEO_Servers on 2009-05-30
squirrelmail I 2nd squirrelmail we use it at my college and its great for the massive student load

---

### Post by rhcm123 on 2009-05-30
> **LEO_Servers said:**
> squirrelmail I 2nd squirrelmail we use it at my college and its great for the massive student load

very easy to configure, i love the included perl script

---

### Post by LEO_Servers on 2009-06-01
[[SIZE=2][COLOR=#000000]rhcm123[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=676672")  nice post I actualy love that link ;p

---

### Post by albinootje on 2009-06-01
> **ZeleD said:**
>  I know qmail, and have been using it for the past years on my old *nix box, but I failed to get spam and virus scanning to work with it (was a Suse OS 10).

I've used qmail in the past for a while, also with ezmlm, and not so long ago I looked at ezmlm (with web interface) and qmail again, and moved mailinglists over to that, only to meet problems.
... Postfix and mailman is imho so much more pleasant and flexible to work with.
> 
I have multiple domains so it must support virtual domains, pop3 and webmail.

Try the postfixadmin/postfix/mysql/dovecot/squirrelmail combination.
> 
It must have some sort of support with spam checking either using spamassasin or any other similiar OpenSource project.
 
Virus checking option is also something I need.

You can always squeeze in anti-spam software, e.g. through amavisd-new. 
I moved away from amavisd-new and used some other filter to use Spamassassin, although I would love to use dspam in the future.

---

### Post by albinootje on 2009-06-01
Here's some howtos for postfixadmin+dovecot :
[http://rimuhosting.com/knowledgebase/linux/mail/postfixadmin](http://rimuhosting.com/knowledgebase/linux/mail/postfixadmin)
[http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL)
[http://bliki.rimuhosting.com/space/knowledgebase/linux/mail/postfixadmin+on+debian](http://bliki.rimuhosting.com/space/knowledgebase/linux/mail/postfixadmin+on+debian)
See also :
[http://ubuntuforums.org/showthread.php?t=1168240](http://ubuntuforums.org/showthread.php?t=1168240)

---

### Post by Cheesemill on 2009-06-01
I've successfully used this guide

[http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/)

To install a mail server hosting multiple domains on a Ubuntu Server 8.04 JeOS install (even though the guide is meant for Debian, it worked for me without any modifications).

Cheesemill


PS - But I substitute squirrelmail for roundcube, it's far better IMHO

PPS - I'm planning to rebuild my mail server on a Debian Lenny VM when the tutorial above is updated.

---

### Post by rhcm123 on 2009-08-11
> **LEO_Servers said:**
> [[SIZE=2][COLOR=#000000]rhcm123[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=676672")  nice post I actualy love that link ;p

its one of the best guides around for setting up a mail server. i actually had so many server death issues i thought about making that page into a bash script that i could use to re-configure my servers every time they died... :D

---

### Post by y@w on 2009-08-11
"Best" is a relative term, but I'd check out Zimbra if you're looking for something simple to get up and running quickly.

---

