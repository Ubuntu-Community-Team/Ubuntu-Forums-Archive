---
title: "Dealing with spam"
date: 2012-03-26
forum: Server Platforms
---

### Post by Etnica on 2012-03-26
I run a SMTP server using Postfix. I get about two spam mails a day.

When I receive an unsolicited e-mail, I forward the source code of the e-mail to the administrator of the sending ISP (from WHOIS) via e-mail, and tell them if I receive spam frequently from their network that I will be block their range.

Well, I have now accumulated quite allot of IP ranges on my block list from mostly Vietnam, Pakistan, Indonesia and Russia.
It is actually quite effective, however, I don't like blocking ranges because I feel I am indiscriminately shooting innocent people.

I was wondering if its possible to make it so Postfix will lookup the sender MX record during message delivery, and if it doesn't match the IP address the mail is being delivered from, then reject it?

---

### Post by nsnidanko on 2012-03-29
It is highly unrecommended to reject email this way because a lot of hosts, such as mass mailers from a big companies, don't always send out email from the same server as it says in the mx record. Some companies with high email volume have one or more servers for inbound mail (defined within mx record) and one or more servers for outbound email.

To tighten your postfix refer to the following:
 [http://www.cyberciti.biz/tips/postfix-spam-filtering-with-blacklists-howto.html](http://www.cyberciti.biz/tips/postfix-spam-filtering-with-blacklists-howto.html)

Also look into more advanced spam filtering with packages like spamassassin (check out MailScanner).

---

### Post by Habitual on 2012-03-29
I'd suggest abuse@ISP of whois output.
Most abuse teams are fully staffed departments these days, Thanks to spam.

Are you sure it's not a forged (sender-from...) email?

---

### Post by SeijiSensei on 2012-03-29
A large amount of spam is sent by compromised desktop computers that have been corralled into botnets. I bet if you look carefully at the Received headers in the spam you receive, you'll see the sending server is not the ISPs actual mail server, but a random client machine.  

Here's an example from a message my inbound server was sent today:  mm-27-43-121-178.dynamic.pppoe.mgts.by.  Names with things like "dynamic" or "ppp" or "pppoe" in them are almost always compromised desktops.  There's really little chance that the administrators of this domain in Belarus will react to messages sent to "abuse@mgts.by".

At only two spams a day, I'd just ignore them.  Yesterday my server processed a couple thousand, and I'm just supporting about a dozen or so domains.

Like nsnidanko, I strongly endorse [MailScanner]("http://www.mailscanner.info/").  It's a very powerful program that will scan all inbound mail for viruses using a scanner like ClamAV and scan for spam using SpamAssassin.  I use it myself and on the email gateways I build for clients.

---

### Post by webservervideos on 2012-03-29
I spent a lot of time adding smtpd restrictions to postfix. Took a while to get it right.
I added greylisting with postgrey.

That alone knocked my spam down to about 10 to 15 a day.
Adding domain names to the access file pretty much knocked the rest out.

I did find that each time I added a new preventive technique the mail dropped off to almost zero for hours....then it would start again. Rinse repeat.

It seems like these giant spammers, commercial and crooked, have a system where they go to your server by going after easy fruit. If you block that, then they use a different set of botnets...and so on.

Eventually if you stop all that junk then they start spamming via more 'honest' means of commercial bulk emailers that have kept themselves off blacklists and do not alert spam assassin.

If you get to the point of a fully postfix setup and greylisting, feel free to add my spammers list to your access file..
[www.bobhoffman.com/spammers.html](www.bobhoffman.com/spammers.html)

I do not use spamassassin except to tag a file. I have not had one piece of spam through in days with over 2 on the spam scale....

fighting spam is a start of a long battle of learning how to setup your mailserver.

---

