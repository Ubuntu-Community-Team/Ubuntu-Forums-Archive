---
title: "Email server"
date: 2006-12-08
forum: Server Platforms
---

### Post by mulligan.can on 2006-12-08
G'day,
I was wondering if it is possible to setup an email server that can grab emails off a pop3 webserver and can then store them locally so that multiple devices/pc's can access it.

I have a phone, laptop and desktop pc that I would like to be able have the same access to emails on. I would like a central repository of them all on the desktop pc which would then be able to serve them out to my laptop and phone (or anything that connects the network).

Is this possible? And am I explaining that well enough?

Regards, Mulligan

---

### Post by Sarisar on 2006-12-09
[Something like this]("http://souptonuts.sourceforge.net/postfix_tutorial.html")?

Been playing around a little with this myself but can't quite get things working.  Basically you use fetchmail to get the email, postfix to run as a mail server to organise things and then even something like squirrelmail to allow a web-based front end to it.  The instructions go into more detail.

If you find a good howto, let me know will you  :)

---

### Post by mulligan.can on 2006-12-09
Thanks a lot mate. That looks quite promising. Gives me something to start with anyway :D

Again, thanks a lot.

---

### Post by MJN on 2006-12-09
Remember any IMAP client (as Squirrelmail is) will be perfect for this - you can then run whatever client you want on each access PC and will always have the same view of e-mails (i.e. those sent from one PC will appear in the Sent folders on all the others).

Mathew

---

### Post by mulligan.can on 2006-12-09
Ok, so what I'm thinking is that I need something like the following:

Getting the emails into the system:
pop3 --> getmail/fetchmail --> dovecot/imap system
                           --> webmail server

Sendingemails:
postfix

Am I even close with that? I would like to have a decent level of security in the entire system. Also remote webmail access would be nice in addition to imap support.

Does anyone have any pointers on how to set this up?

---

### Post by mulligan.can on 2006-12-10
Ok, decided to start from the ground up.

Present idea is to use getmail and dovecot to as the basic ground work for the system. Not sure how to configure them at this point.

Have set up Apache, MySQL and PHP5 (that at least is something I could to easily :)) and plan on using them to run a webmail front end (probably squirrel mail).

If anyone can give me some pointers on how to configure getmail and dovecot to pull email down from a pop3 server and then run as a local imap email process it would be much appreciated.

---

### Post by chrisfay on 2006-12-10
> Present idea is to use getmail and dovecot to as the basic ground work for the system. Not sure how to configure them at this point.

Postfix should be the foundation of your mail server providing MTA server functions. 

> If anyone can give me some pointers on how to configure getmail and dovecot to pull email down from a pop3 server and then run as a local imap email process it would be much appreciated.

Dovecot does not 'pull email from a pop3 server', it is your pop3 server. 

Dovecot is both an IMAP and POP3 server for delivering/viewing mail to an email client. Webmail uses the IMAP protocol to view email on your server while Outlook or Thunderbird (or whatever you use) can utilize either or. 

You could also use Fetchmail for maintaining a central repository for your mail. I have never used this so not positive on its configuration.

Postifx is responible for receiving mail and delivering it to your mail folders locally on the server or relaying it to another SMTP server via a relayhost. 

I would start by going over the Postfix official documentation, then if necessary, proceed into some Postfix/Dovecot specific howto's. Configuring a functioning mail server is not 'extremely' difficult; but you need to make sure your MX record routes to your servers ip, your router is portforarding all necessary ports (IMAP 143, POP3 110, SMTP 25) to your server and that your relay settings are configured so you're not an open relay. 

Good luck....

---

### Post by gjtoth on 2006-12-10
Axigen is coming out soon with a server that will do all you require.  What you are basically requiring is a server with a built-in pop3 client.  At least that's the way it appears to me.

Until Axigen comes out with the built-in client, there was something up on Freshmeat.net called, "fetch & deliver" or something like that.  That may fill the bill for you.

---

### Post by druhboruch on 2006-12-10
I am using a combination of Zimbra and imapsync from reps.
I setup imapsync as a cron job to deliver external mail to Zimbra.

---

### Post by jados1ms on 2008-07-02
Currently my company is using Dovecot as an IMAP email server. We are currently setting up exchange to take its place, but since we have been using Dovecot we have had no problems. I want to try and keep Dovecot as our front end email server and use exchange 2007 as a back end email system. Is there away to keep Dovecot on the front end and have it relay email to exchange 2007 and then the users attached to exchange can get there mail from there. Is this possible and if so, how do I go about doing this? Any help would be great fully appreciated.

---

### Post by MJN on 2008-07-02
It sounds like you might need to read post #7 again. Dovecot is not an email server in the sense of being responsible for the delivery/relaying of mail.

Mathew

---

