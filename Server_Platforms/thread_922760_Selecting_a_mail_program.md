---
title: "Selecting a mail program"
date: 2008-09-17
forum: Server Platforms
---

### Post by Vegan on 2008-09-17
Reviewing mail programs on Linux.org reveals the usual crowd of programs.

I am looking for something that can work with web browser, and POP3 and yet as powerful as sendmail which is the popular choice at universities.

---

### Post by alastair on 2008-09-17
> **Vegan said:**
> Reviewing mail programs on Linux.org reveals the usual crowd of programs.

I am looking for something that can work with web browser, and POP3 and yet as powerful as sendmail which is the popular choice at universities.

There are many types of "mail programs" and, unfortunately, it can get confusing. It is often a good idea to see what comes as standard with the distribution and, if all else is equal, go with that. Something well supported and documented.

Mail programs include mail "servers", that transport email around - so-called MTA (mail transport agent) programs. Server to server e.g. Sendmail (but I would go with Postfix, or Exim). A program (e.g. Thunderbird email client) sends mail via such a server).

SMTP mail server : Postfix

For the user retrieving mail, you want a POP3 or IMAP server. This will make the mail available to you from a mail client. Use something like Dovecot for POP3 - or better, IMAP (and even IMAPS for "SECURE" IMAP).

POP3/IMAP : Dovecot

Access via browser - web mail? Maybe Horde or Squirrel Mail?

But you question about "Sendmail", "web browser" and "POP3" is confused. These things are all quite separate.

Alastair

---

### Post by schettj on 2008-09-17
Wow... postfix/dovecott/squirrelmail... yep, that's the trinity I'm running. Used to run sendmail, but I like postfix a lot better now that I'm over the transition.

---

### Post by Vegan on 2008-09-23
I notice that postfix is run by IBM so it has corporate support, means it will be fix if it fails.

Can postfix handle SMTP/POP3 at least for several domains as I have Apache running a basket of domains.

---

### Post by TomB19 on 2008-09-23
> **Vegan said:**
> Can postfix handle SMTP/POP3 at least for several domains as I have Apache running a basket of domains.

Yes.  You can get as carried away with virtual domains as you want.

---

### Post by jamesrfla on 2008-09-23
I use citadel and it works great. :guitar:

---

### Post by Vegan on 2008-09-23
Well I am influenced somewhat by IBM as the museum piece that is my web server is a real IBM PC 300 GL that still works.

I note that IBM developed postfix for their AIX flavor of Linux (*IX)

Reviewing the dox suggests postfix can manage with my desire to make my old PC perform like a madman.

---

### Post by artcancro on 2008-10-22
As others have suggested, it really depends on whether you want to go the componentized route or the turnkey mail system route.

For a componentized solution, nearly everyone agrees that Postfix is the killer MTA these days.  It's fast, reliable, and gets the mail where it needs to go.  Dovecot is a nice IMAP/POP server -- Cyrus is powerful but it's a bitch to administer, so probably not worth it for a small system.

On the other hand, if you just want to install one application and have a complete system up and running, you really can't go wrong with Citadel.  Everything from transport to standard server protocols to web UI is pre-integrated for you.

---

### Post by plasmafusion on 2008-10-22
it's [postfix]("http://www.postfix.org/")/[dovecot]("http://www.dovecot.org/")/[squirrelmail]("http://www.squirrelmail.org/") for me.
tried citadel but it interfered with too many of my boxes other services and i thought it was a bit clunky with it's processes using too many resources for my liking.
there's also [zimbra]("http://www.zimbra.com/") which has a nice interface and has an [open source version]("http://www.zimbra.com/community/downloads.html") (tried it on a vm and quite liked it).

---

### Post by Vegan on 2008-10-23
Well I have elected to use postfix, and dovecot for the mail solution. I am unsure if squirrel is adequate. I want something simple to administer.

I am the only IT guy here.

---

### Post by hyper_ch on 2008-10-23
you may even want to consider procmail for the local delivery... it's also nice...

I prefer: postfix / courier-imap / procmail / squirrelmail

---

### Post by ezacon on 2008-10-23
Configure and administer posfix, courrier, squirrel mail etc can be a nighmare without some interface.

I use Zinbra open source. It install postfix, apache etc from a single package. It dont use stadard package, so you cant have ubuntu posfix, apache etc packages. I run it on a virtual machine running on vmware server.
There is a package to download on the zimbra website for 8.04.

---

### Post by hyper_ch on 2008-10-23
administration postfix, courier, squirrelmail is no nightmare at all :)

---

### Post by plasmafusion on 2008-10-23
hyper_ch is right...all are very easy to manage and have a small memory footprint. there are various guides around if you're unsure.

---

### Post by hyper_ch on 2008-10-23
it takes a while to learn work with it but it's rewarding.

---

### Post by Vegan on 2008-10-27
OK I have postfix, and I added dovecot so I have POP3/SMTP covered?

Any config needed to get the main bound to user accounts.

---

### Post by hyper_ch on 2008-10-27
I don't use dovecot but a quick search revealed this:

[https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)

Futhermore I can recommend you [http://www.howtoforge.com](http://www.howtoforge.com) --> there are many great howtos for server stuff :)

---

### Post by alienprdkt on 2008-10-27
Here is a great how to guide I used just last week :)

Step by step guide to install Postfix
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey 

[http://flurdy.com/docs/postfix/index.html#top](http://flurdy.com/docs/postfix/index.html#top)

---

