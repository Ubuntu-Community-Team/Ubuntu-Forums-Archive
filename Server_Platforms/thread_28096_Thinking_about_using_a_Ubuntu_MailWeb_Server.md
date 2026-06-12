---
title: "Thinking about using a Ubuntu Mail/Web Server"
date: 2005-04-18
forum: Server Platforms
---

### Post by s0c0 on 2005-04-18
I've been thinking about setting up a Ubuntu web / mail server for work and I was wondering what the best/easiest email server package is.  I've heard sendmail is pretty common, but I would like you input before committing to this.

---

### Post by dataw0lf on 2005-04-18
Ubuntu has much more support for Postfix.  Sendmail is monolithic and poorly designed,  and although a bit easier than Postfix to setup, will teach you bad habits and, after a couple months, make you wish you picked Postfix.  :)  Getting the trend... ?

BTW, where in Utah are you at?  ;)

---

### Post by speedman on 2005-04-18
Postfix is the default MTA in Ubuntu and it is much more modular than sendmail.  Configuration options are split into several files for Postfix and unless you speak fluent SMTP it is easier to work with compared to sendmail.

Either MTA will serve you well, but as you can tell my personal preference is to use Postfix over sendmail.  :) 


Regards,

SM

---

### Post by shufla on 2005-04-19
Hi,

[QUOTE=s0c0]I've been thinking about setting up a Ubuntu web / mail server for work and I was wondering what the best/easiest email server package is.  I've heard sendmail is pretty common, but I would like you input before committing to this.[/QUOTE]

For real "mail server" you need more packages than just MTA. Look at [http://www.workaround.org/articles/ispmail-sarge/](http://www.workaround.org/articles/ispmail-sarge/) for example of "bigger" mail server tutorial.

So called "best" set of packages would be (read: I'm using them):
 - postfix (MTA, etc)
 - postfix-tls + sasl2-bin (SMTP-AUTH)
 - courier-imap[-ssl], courier-pop3[-ssl] - for MUAs
 - spamassassin, postgrey, clamav - SPAM and virus protection
 - sqwebmail OR squirrelmail - web based MUA

While using courier-* based stuff you'll need to use Maildirs, but that kind of configuration is quite simple.

Best regards,
Luke

---

### Post by speedman on 2005-04-19
[QUOTE=shufla]- courier-imap[-ssl], courier-pop3[-ssl] - for MUAs[/QUOTE]

Other than courier imap I would agree with shufla's recommendations.  Cyrus is the way to go.  No other package comes close to the performance and scalability of Cyrus for providing IMAP(S) services.


Regards,

SM

---

### Post by ScatterBrain on 2005-04-19
[QUOTE=s0c0]I've been thinking about setting up a Ubuntu web / mail server for work and I was wondering what the best/easiest email server package is.  I've heard sendmail is pretty common, but I would like you input before committing to this.[/QUOTE]

It really depends on what you want the mail server to do as to the final configuration, but like the others who have responded, I would put POSTFIX at the center of it all.

If you're looking to create a server for a single domain, I would setup a server similiar to the one described [HERE](http://www200.pair.com/mecham/spam/spamfilter20041003.html).  Just don't setup postfix to forward all incoming mail to another server.  That way the mail server can filter for SPAM and Viruses.

If you're looking for a more complex setup, then I'd follow shufla's comments.  But that's a much more involved setup.

---

### Post by Klunk on 2005-05-16
I have just gone through a similar exercise.

I opted for :-

Fetchmail - to pull email from a POP3 server
Amavis - to integrate antivirus and antispam software
ClamAV - for anti-virus
SpammAssassin - for antispam, although I still need to get this working
Postfix - for SMTP processing
Cyrus IMAP - for server side mail access

I use this with Evolution, Thunderbird or Outlook depending on which machine I am connecting from.

All of this was with minor tweeks to the standard Ubuntu packages.

---

### Post by LordHunter317 on 2005-05-16
[QUOTE=dataw0lf]and although a bit easier than Postfix to setup,[/quote]**HAHAHAHAHAHA**
No. 

Sendmail uses m4 for it's configuration file.   It has to be **compiled** before sendmail can be run with it.

Postfix uses plain text configuration.

There is no way you can ever even remotely say sendmail is eaiser to configure, unless your idea of a configured MTA is "open-relay to the world".

Btw, just for the OP's gratification:  Courier may be eaiser than Cyrus for a single user setup.  Cyrus is a powerful, complicated IMAP daemon and isn't worth it for a single-user site, in my experience.

---

### Post by Beernut on 2005-05-16
I just installed a Hula server it's working pretty well and was easy to setup.  Hula is still under developement but the email services are fully functional.  

[http://hula-project.org](http://hula-project.org)

---

