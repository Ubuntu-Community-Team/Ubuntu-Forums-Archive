---
title: "Ubuntu MailServer"
date: 2015-04-30
forum: Server Platforms
---

### Post by pancho5 on 2015-04-30
Hello!

For the past 13 months I have become acclimated to Lubuntu, now Ubuntu which I thoroughly enjoy so far.  Glad I got away from Windows XP.

Sometime in the next couple months, I'm going to acquire another HP laptop that has a wider monitor along with the HP Pavilion dm4 that I have now.  Well, what I want to do is convert my HP Pavilion dm4 to a Ubuntu mail server.  Why??  Just because...no big reason.  So that I know how to do it.  After I get it up and running for awhile and able to send/receive email successfullly, I will probably want to wipe out the software and just load 14.04 LTS.  Kind of a PC/Laptop enthusiast.

So, my question to all of you is how difficult will it be for me to do?  I have NEVER installed a mailserver before.  I have skimmed over the Ubuntu MailServer documentation.  Is there anything else I should do or does anyone have any recommendations of what or WHAT NOT to do??

Please advise.
Pancho B

---

### Post by sandyd on 2015-04-30
Moved to *Server Platforms*

---

### Post by nerdtron on 2015-05-01
> **pancho5 said:**
> Hello!


So, my question to all of you is how difficult will it be for me to do?  I have NEVER installed a mailserver before.  I have skimmed over the Ubuntu MailServer documentation.  Is there anything else I should do or does anyone have any recommendations of what or WHAT NOT to do??

Please advise.
Pancho B

How hard? depends on what things you want to setup. 

For a newbie, installing a complete email server, with webmail can get complicated unless, you have someone create a script for you to install and configure everything.
See: [http://iredmail.org/](http://iredmail.org/)

And installation on a fresh (ubuntu server, even on a VM) takes about 30minutes. Install instructions with screenshot here: [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

It will install a lot of things so after the installation you may want to test and experiment on the system.

---

### Post by TheFu on 2015-05-04
Installing postfix is pretty easy - the hard part is usually convincing the rest of the world that your email server is valid.  That happens by getting a registrar'd domain, $.  Then you have to setup world-wide DNS records, A, CNAME and MX, $.  And finally, your ISP has to provide static IPs and allow in/out SMTP traffic to your "server" on port 25.  Most home ISPs won't do this.

Technically, you can run an MTA on DHCP addresses, but no other email server will accept email from those addresses.  This is because of the spam problem - blocking DHCP addresses is so common as to make running an MTA at home worthless.

Generally, the easiest, best solution for running an email server is to get a VPS for $5/month and setup everything there. That solves the static IP and ISP problems, then you just need to buy a domain and DNS service - $20-$40/yr.  A minimal VPS is all you need - 384MB of RAM for postfix is fine.

MTA is the server-to-server part of email. Postfix, sendmail, exim, qmail are all MTAs - you only need 1. Postfix is probably the right level of security, features, and ease of configuration for 99% of the world. Sendmail should only be used by paid professionals running extremely complex configuration with 20+ domains.  I've never used exim or qmail.

An MTA is only for server-to-server stuff and for a client to send email.  For a client to read email, you'll want a mail client to provide an imaps interface.  Dovecot or couriermail are the normal choices for this - then webmail or a thick client like thunderbird can be used.

Don't be an open relay. That will get your IP/domain banned worldwide in less than a day. Often, getting off that banded list is impossible.

Clear as mud?  [http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email](http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email) is an article I wrote about this years ago. I still run Zimbra, thought it has been updated to new releases about 6 times since then. Zimbra has much greater server hardware requirements - CPU, RAM, disk ... but it isn't a simple SMTP/IMAPS server.

---

### Post by pancho5 on 2015-05-05
TheFu,

Thank you for your most valuable input!

---

