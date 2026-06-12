---
title: "Need help setting up mail/router and more"
date: 2005-08-08
forum: Server Platforms
---

### Post by Mugendai on 2005-08-08
I'm trying to set up this Ubuntu box to match, and hopefully beat this Windows box that is full of expensive software.

I want to get these things set up, these ways:

web, (Apache2 is already set up and running, I was already using that in Windows)

mail, trying to match Kerio Mail Server, which means, POP/IMAP, SMTP, SSL, SpamAssassin, Anti-Virus, and a very good webmail.
I've got the POP/IMAP(Courier), SMTP(Postfix), SSL, SpamAssasin, and Anti-Virus(ClamAV) part going. 
What I've been working on is getting a nice webmail going.  The main thing I am wanting from the webmail is tha ability to configure per user dropmail style content filtering.  Kerio let users configure filter rules that could check any of the headers for whatever, with rules like, begins with, ends with, and contains, as well as check the mail size, and attachment status.  It could also reject the mail, returning it to the sender(or some form of response to the sender).
I would really like to get an equivelent system set up.

router/firewall, again I am trying to matcha  Kerio product, Winroute Firewall.
KWF has a GUI admin system that I can access from across the network(important since I dont plan on being near the server for admin[have TightVNC already]).  It is a  very nice system allowing me to control all aspects of the fw/router, including DHCP server, DNS forwarder, statistics of connections, who is connected how, and it has a very nice rule set.  I love the way it's rule system works.  There is one kind of rule.  You can set it's source(which can be an interface, host network, range, user), destination, source port, destination port(ports can be set as protocals, port ranges, and can be set as TCP, UDP, ICMP, any and TCP/UDP), behavior(permit, drop, deny), nat(you can have it nat source or destination, or both addresses, to specific addressess, addresses of interfaces, and it supports DNS lookups), packet inspector(for things that need special handling, like HTTP[if you wanna filter/proxy it], ftp[to deal with port mode source address nating], etc.), and logging options.  Oh and I can simply enable/disable the rules if I need too, without actually deleting them.
I really like the idea that I can say, if the packet comes from here, to there, then route it here.  I could have two packets on the same port NATed differently based on origiona source/destination.  And could configure whether or not to dump the packet at the same time, with one rule.
It also has an HTTP transparent proxy that I can inspect webpages for content with, and remove content I dont want, as well as cache content.
Also has some nice spoofing prevention.

ftp, my current FTP on windows doesnt even do all that I want done(Filezilla).
I want to be able to throttle trafic, have symlinks followed, make virtual, not system users, permit for resuming of downloading and uploading, control the permissions of access for all paths, and be able to set path rules using atleast wildcards, if not full on syntax matching(ex. "/ftproot/dropboxes/*/upload" ).  Oh and I would liek to be able to see who is on, doing what, see statistics and be able to kick/ban people from some admin system.

hotline, (you prolly never even heard of this, and it shouldnt be a problem to get setup)

a dynamic dns updater, really the only domain I want to update is my main domain, which is a real domain, served by NameCheap, the updater would need to be compatible with that.  But I think even in this case, with a lil help I should be able to do it with a cron job, cause all it actually does to do the update is access a URL.  I just type in this web address including my domain, password key thing, and the new address, and it is updated like that.


Any input on any of this stuff would be very very much welcome.  The most important parts to me are the mail, and and router/firewall.  I'de love to be able to admin these things graphically(especially the firewall), but I would be willing to forgoe that for text files, if the text files are just as easy/powerful.

---

### Post by tonym on 2005-08-12
One thing you might consider for the firewall is shorewall.  It is configured by text files but is powerful and well documented.

---

