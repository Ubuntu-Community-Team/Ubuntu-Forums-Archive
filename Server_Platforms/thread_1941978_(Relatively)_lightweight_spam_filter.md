---
title: "(Relatively) lightweight spam filter?"
date: 2012-03-16
forum: Server Platforms
---

### Post by MattBD on 2012-03-16
Hi,

I've got a VPS I'm using to aggregate my mail from several accounts, and I'm looking for a spam filter. I've tried SpamAssassin and while it does a good job, it brings the whole server to a crawl, so I'm trying to find something that's a bit lighter.

Can anyone recommend an alternative spam filter that uses less resources?

---

### Post by webservervideos on 2012-03-16
> **MattBD said:**
> Hi,

I've got a VPS I'm using to aggregate my mail from several accounts, and I'm looking for a spam filter. I've tried SpamAssassin and while it does a good job, it brings the whole server to a crawl, so I'm trying to find something that's a bit lighter.

Can anyone recommend an alternative spam filter that uses less resources?

assuming you are using postfix I would keep spamassassin if it is local, but add a ton of stuff to postfix smtpd restrictions on client, helo, recipient and the like. Then add some rbl and rhsbl lists to it.... for me, settings in postfix brought my 1000 junk mail a day server down to about 10. Quite effective and I only tag spam, not delete it so I can add other domains if need be.  I would do this on the vps though...not sure exactly what you mean about aggregating the various servers.

---

### Post by MattBD on 2012-03-17
Sorry, I really should have gone into more detail! My bad.

The setup I have isn't a full-blown mail server. Instead, I'm using fetchmail to download emails from several different email accounts in order to aggregate them in one place, and I'm using procmail to deliver them to several folders. I do have msmtp set up so that I can send emails from that server, but I don't intend to install a proper mail server like Postfix because the VPS only has 128M of RAM.

I still need a spam filter, however, and SpamAssassin is just too hefty, therefore I just wanted to know if anyone else can recommend a filter that's a bit lighter?

---

### Post by HermanAB on 2012-03-17
Howdy, 

The trick is to use RBLs to avoid receiving a flood of spam in the first place.  Standing knee deep in a sewer trying to catch the occasional real email is very inefficient.

So, I run a Citadel mail server with Spamassassin, Clamav and three RBLs: bl.spamcop.net, zen.spamhaus.org and dsn.rfc-ignorant.org

---

