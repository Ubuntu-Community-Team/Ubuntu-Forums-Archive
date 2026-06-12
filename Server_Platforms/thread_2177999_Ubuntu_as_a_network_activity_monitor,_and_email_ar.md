---
title: "Ubuntu as a network activity monitor, and email archiver ?"
date: 2013-10-01
forum: Server Platforms
---

### Post by c0d3sl1ng3r on 2013-10-01
I'm starting to get to grips with Ubuntu - doing well with AD integration and file server roles in live networks :)

A project is just beginning to implement a network activity monitor (does not need to include internet usage - this is currently logged in detail using pfsense/squid etc) and, separately, an email archiving system which will need to store a copy of all inbound and outbound emails for compliance purposes. Disgruntled employees have caused headaches in the past and the current commercial solution is going to cost thousands to renew, with significant ongoing maintenance costs.

I am looking at Enkive [http://enkive.org/](http://enkive.org/) and Piler [http://www.mailpiler.org/en/index.html](http://www.mailpiler.org/en/index.html) to fulfil email archiving roles.

My question really is, are there simple routes to achieve similar results to Enkive and Piler using Ubuntu server and can it perform network activity monitoring.

I am guessing the answer is that, yes, it can be done, but that it shouldn't be done unless you really know what you're doing.

Not looking for a walk-through here - just feasibility and which packages might be utilised.

Network is predominantly Windows server 2008/2003 with in-house Exchange 2007. Client computers are mainly Windows XP and Windows 7, with a few Apple Macs and my Linux box :)

Two Ubuntu servers currently serve over a million files to several hundred users - yours truly is making some inroads here :)

This is a fairly open ended project so getting a solution in place is more important than when.

Thoughts very gratefully received :)

---

### Post by SeijiSensei on 2013-10-01
[Ntop](http://www.ntop.org/) is a nice graphical utility to monitor traffic if that is what you mean by "network activity monitoring."  Perhaps you can expand on what you want this application to do.

I built a gateway for a client that uses [MailScanner]("http://www.mailscanner.info/") to scan all inbound mail for viruses and spam before it gets to the Exchange server.  MailScanner lets you define methods for archiving all the mail it sees as well.  If you configure Exchange to relay all the outbound mail through the box, it will archive those messages as well.  (In my case, the client is a health center, and we took advantage of MailScanner's "Message Content Protection" system to quarantine outbound messages that might contain "patient health information" which cannot be sent in plain-text because of HIPAA rules.)

Both of these are in the repositories.

---

### Post by c0d3sl1ng3r on 2013-10-01
Brilliant stuff, many thanks !

Network activity monitoring is all about file access, who does what, where and for how long, that sort of thing.

As stated we already run a ferocious pfsense box that gives us a ton of web-related usage data per user, but we really want a very detailed picture of who does what, why and when across the LAN.

Your mailscanner gateway sounds very much along the lines of what we would like to implement for archiving/compliance purposes. Renewal on our ageing GFI product is going to be horribly expensive and for what we use it for I am happy to research, build and test an Ubuntu based system or look more closely at the likes of Enkive and Piler.

We use a hosted SPAM/antivirus scanning solution for inbound email so we get a ***minute*** amount of crap coming through each month :)

Thanks for your reply though - it's given me some possible directions to explore :)

---

### Post by SeijiSensei on 2013-10-03
I wrote a PHP application for the same client that imports each night's squid log into a PostgreSQL database and provides the admins a web interface to track usage.  It sounds like you're talking about tracking every single packet from every single user.  Ntop might help with that, as I recall, since I think it will report traffic by IP and port.  We don't bother with that level of detail because the iptables rules I wrote limit considerably what the users can do.  For instance, we ban all traffic to the Internet that employ both source and target ports about 1023.  That alone blocks a lot of bandwidth eaters like torrents and gaming.  We also block traffic to sites like Facebook with a combination of squid ACL rules to intercept HTTP packets and iptables rules that block HTTPS traffic to the FB servers.

---

