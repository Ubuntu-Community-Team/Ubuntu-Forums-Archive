---
title: "Help, Setup SPam filter"
date: 2007-09-04
forum: Server Platforms
---

### Post by bgsneeze on 2007-09-04
Hello, Does anyone have a good howto for setting up a spam email filter/firewall?  I am trying to setup a filter that will sit in front of an exchange 2003 server. I would like the filter to check for spam and for viruses transparently. If it has a web interface for reviewing logs that would be great, if it could cache the email, incase of a false positive, that would be great too. Basicly I would like to construct something like a Baracuda Spam Firewall, but use all open source/ Ubuntu packages if possible.
Thanks 
Bgsneeze

---

### Post by Brazen on 2007-09-04
We use Trend Micro InterScan Message Security with Spam filtering for our email filtering and it works good, but expensive.  When we put it in a few years ago it was largely regarded as the best, and it did block probably 99% of our spam, but in the last few months we have been getting increasing amounts of it.

If you wanna go open source, you'll want to start with SpamAssassin and set it up as an "email proxy" or "email gateway" (just two ways of saying the same thing): [http://spamassassin.apache.org/](http://spamassassin.apache.org/)

---

### Post by bgsneeze on 2007-09-05
Does anyone know of a how-to for setting up spamassassin? Is there anyway to add anti-virus scanning to this, by using clamav?

---

### Post by Brazen on 2007-09-05
there are howtos on the spamassasin site and you can probably find more with google.  I think even howtoforge has some howtos on it.  And yes you should be able to also scan your emails for viruses.

---

### Post by erwall on 2007-09-05
yep, howtoforge has lotsa good howto's on this.  There is a new one up there for using assp on Etch, which would work for you on Ubuntu no problem I would think.

[http://howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch](http://howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch)

then

[http://howtoforge.com/assp_clamav_postfix_debian_etch](http://howtoforge.com/assp_clamav_postfix_debian_etch)

I plan on redoing my spam box too which is currently FC4 w/amavis, postfix, dcc, pyzor, razor, clamav and has been working damn well for a couple years now.  Hard to replace something that isn't broken tho!  Good luck!

---

### Post by Mr. C. on 2007-09-06
Mail servers and anti-spam/anti-virus systems are by their nature inherently complex, and do not lend themselves to one-shot HowTos.  Although you may find many, and can use them for initial configuration and setup, the correct strategy is to learn how these systems work, and configure the system according to your needs.

Many people recommend not placing an Exchange server directly on the WAN, and instead using a more robust mail server such as postfix with an anti-virus/anti-spam gateway relaying to the Exchange server.

I have had excellent success with an amavisd-new / postfix combination, with amavisd-new managing the anti-virus / anti-spam scanning duties.  There are very good resources available that explain in as much detail as you require how the systems work, and best practices. Consider The Book of Postfix, the amavisd-new site, postfix site, as well as clamav and spamassassin.

MrC

---

### Post by bgsneeze on 2007-09-20
ok, i have looked at several articles on setting up spamassassin, and clamAV. I can't seem to find articles where the software is setup to relay the email to an Exchange server. I just want a standalone server that sits filtering the incoming e-mail, and then relays the good stuff to exchange, if it were to also have a cache of the filtered mail that would allow me to push through a blocked message that would be good too. While I have used Linux for a few years, I am by no means a guru at mail servers. I would be very happy with any help I can get. Please help, I am clueless when it comes to email servers.

---

### Post by gfowler on 2007-09-21
Try this link.  I've been using it for about a year to relay to a 2K Exchange.

[http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://www.howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)

Jerry

---

