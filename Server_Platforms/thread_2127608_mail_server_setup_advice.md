---
title: "mail server setup advice"
date: 2013-03-20
forum: Server Platforms
---

### Post by MakOwner on 2013-03-20
I'm sure this one has been beat to death, but unfortunately, I'm at the point where I'm going to have to set up and admin my own mail server.  Not that enthusiastic about the extra work, but there it is.  I'm looking for some advice from those that manage internet exposed mail servers.
I plan on utilizing this guide [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer) and trying to fgiure out the most appropriate setup.  (I notice this tutorial appears a bit dated -- it appears to have been last updated in 2009)
Any pointers on updates with reccomnendations which applications to select for ease of use/security would be greatly appreciated.


I need to be able to send and receive mail from yahoo and gmail through my mail server.  Can anyone point me at "best practices for dummies" for ensuring I won't have any issues with the larger mail providers passing my email?
I just saw an article about google now validating DNSSEC.  Anyone know of a good primer or how to - is this even critical yet?

I own my own (actually several) domains that all point to my business account through verizon fios.  
I already run a simple webserver behind a firewall, and I have set up a rudimentary squirrelmail setup in the past -- I quickly took it down because I was overwhelmed with incoming spam. 
This time around I have a little better hardware and hope to run something in from of the mail server to weed out some of the spam.  

Anyone ever dealt with Verizon support trying to do this?  
Can I get any assistance from them? 
Are they just as oblivious about things like this as they are about local infrastructure issues?

I have a spare Poweredge 850 that I plan to use for this.  
I use one of the more common linux based NAT firewall appliances. Would it be better to put this host in a DMZ or just open specific ports to be redirected to this host in the firewall?

---

### Post by JKyleOKC on 2013-03-20
I've used postfix for about 10 years now, and while its documentation is a bit difficult to follow at first, the wizard that's included in the DEB packages for *buntu now makes it pretty easy to set up and get running out of the box. You can tweak the configuration later as you become experienced with it.

Be warned that many ISPs block port 25, the standard SMTP port, to discourage spamming and botnets. I don't know whether Verizon does or not; my own ISP (AT&T) blocks the port but will remove the block on special request. Alternate ports exist and you can use them if necessary, but this is part of the tweaking I mentioned above.

You'll also need to verify that your server does not allow itself to be used as a mail relay. I get a few hundred attempts to do so on my Postfix server every month; I've tweaked the configuration to make certain they all fail, and refuse excessive connection attempts from the same address in a short period of time...

---

### Post by MakOwner on 2013-03-20
> **JKyleOKC said:**
> 
You'll also need to verify that your server does not allow itself to be used as a mail relay. I get a few hundred attempts to do so on my Postfix server every month; I've tweaked the configuration to make certain they all fail, and refuse excessive connection attempts from the same address in a short period of time...


This is one of my primary concerns -- know of any easy to find/use configuraiton checking/hardening utilities?

---

### Post by JKyleOKC on 2013-03-20
You can check your server at [http://www.mailradar.com/openrelay/](http://www.mailradar.com/openrelay/) to find out whether it's open. As I recall, the wizard that installs for all *buntu versions sets up the configuration as being hardened; however it's been a while since I did an installation and I don't really recall whether that was done by the wizard, or later as I was tweaking things...

EDIT: Changed the link; ORDB, which I used to test my server, has been off line for years!

---

### Post by MakOwner on 2013-03-20
I got as far as installing the Mail Delivery Agent -- it looks like the [https://help.ubuntu.com/community/MailServerCourierSpamAssassin](https://help.ubuntu.com/community/MailServerCourierSpamAssassin) link is a complete build, or is that supposed to be done on top of postfix?

Since I had already gotten Postfix and Clamav running, I started with the dovecot install.

None of the dovecot instructions really match up to the what is installed, and critical bits are missing completely.

Edit: -- I stunmbled through it, but I suspect the age of that how to is starting to show.

---

### Post by JKyleOKC on 2013-03-21
Undoubtedly true!

I can't help with dovecot; I've installed qpopper to provide a local pop3 capability and don't use any AV program at the Xubuntu level. Instead, I run Microsoft Security Essentials on all the Windows VMs in my systems. Since only a few non-Windows baddies are known to be in the wild, I simply rely on taking care with email and browsing to keep out of trouble.

---

### Post by MakOwner on 2013-03-21
> **JKyleOKC said:**
> Undoubtedly true!

I can't help with dovecot; I've installed qpopper to provide a local pop3 capability and don't use any AV program at the Xubuntu level. Instead, I run Microsoft Security Essentials on all the Windows VMs in my systems. Since only a few non-Windows baddies are known to be in the wild, I simply rely on taking care with email and browsing to keep out of trouble.

I was looking at the POP3Agregator page [https://help.ubuntu.com/community/POP3Aggregator](https://help.ubuntu.com/community/POP3Aggregator) and found this interesting, but it looks like this will essentially take over the dovecot configuraiton - or at it looks like it to me.
It would be useful to have other PO# services aggregated here, at least while I transition.  

Know of any pointers to somethign that would walk me through a setup of doing aggregation to a postfix/dovecot/spamassassin/clamav setup?

---

### Post by smtp on 2013-03-22
Perhaps this one could help: [https://help.ubuntu.com/10.04/serverguide/postfix.html](https://help.ubuntu.com/10.04/serverguide/postfix.html)

---

### Post by SeijiSensei on 2013-03-22
> **MakOwner said:**
> I was looking at the POP3Agregator page [https://help.ubuntu.com/community/POP3Aggregator](https://help.ubuntu.com/community/POP3Aggregator) and found this interesting, but it looks like this will essentially take over the dovecot configuraiton - or at it looks like it to me.

That article asserts that GetMail has more "flexibility" than fetchmail but gives no actual examples of why the author believes that.  If you need to download mail from multiple POP3 accounts, I'd choose [fetchmail]("http://fetchmail.berlios.de/").  It's been widely used for a long time and was written by well-known FOSS coder Eric Raymond.  

Tools like fetchmail do not "take over" dovecot.  They log into the remote account, download the messages, and hand them to the local SMTP exchanger (Postfix, sendmail, exim, etc.) for delivery to local accounts.  You'd still need dovecot to provide the client-side delivery services to programs like Thunderbird.

The most important things to know about all mail server software for Ubuntu is that connections from anywhere besides the machine on which they are running are disabled by default.  For Postfix, the "mynetworks" parameter only allows connections from the localhost address, 127.0.0.1.  If you want to support multiple users on a network, you need to add the subnet address for the network to this directive, e.g., 192.168.1.0/24.  For dovecot, check that the "listen" directive is set to "*" in dovecot.conf.

---

### Post by CharlesA on 2013-03-22
I am kinda in the same boat as the OP. I recently moved my website to a VPS and got the webserver and php setup via Nginx instead of Apache and am still in the process of figuring out getting the mail portion up and running.

I am currently running Postfix for sending info from my server - Update notifications, contact form submissions, etc, but I haven't had a much luck figuring out dovecot vs courier vs whatever. I'm sorta leaning toward dovecot and using sasl + SSL for smtp and imap, but most of the howtos are either a few years old or way over my head.

I also read about DomainKeys, which is a "need to have" to help combat spam, apparently.

@OP: I found iRedMail works ok but I decided not to use it because I had a hell of a time trying to convert it from Apache to Nginx. Their website is here:
[http://www.iredmail.org/](http://www.iredmail.org/)

---

