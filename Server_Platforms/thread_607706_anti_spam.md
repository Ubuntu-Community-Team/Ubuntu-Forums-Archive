---
title: "anti spam"
date: 2007-11-09
forum: Server Platforms
---

### Post by starboyhull on 2007-11-09
Hi guys,

Not sure if anyone can offer any advise on this subject but i'll ask anyway.

We support quite a few small businesses and as everyone they are receiving more and more spam and its becoming a bit of a problem, we have looked at messagelabs and others like them, but their pricing starts to get a bit out of control when a customer has 2 domains or more.

I have been using ubuntu on my laptop and its working great, so I thought the server version might be equally as good but after doing a search around I havent been able to find anything that I could setup as an antispam gateway for our customers, can anyone offer any suggestions???


Thanks in advance

Karl

---

### Post by Wallace on 2007-11-09
SpamAssassin works quite well, there's a package for it too. It can be a bit fiddly to setup, but the results are good.

Another option is amavis-new, which does SpamAssassin processing too but can do virus scanning as well.

I used to use SpamAssassin (using the spamd option) but switched to amavis-new, using the info in Flurdy's howto guide (it's a little out of date now but most of it is still valid).

---

### Post by kwambus on 2007-11-09
Sounds like setting up an email gateway would be a good solution for you.

This would involve setting the MX entries in the domains you deal with to point to the "Virus/Email" gateway server, built on Ubuntu. Then these mails are forwarded to their respective email servers when processed.

Works very well for us in a similar situation. In my experience you have two alternatives. There are "turn-key" VMWare Appliances which could run easily on your Ubuntu server running the free VMWare server package, for more information see:

[http://www.vmware.com/appliances/directory/542](http://www.vmware.com/appliances/directory/542)

Alternatively you can build one for yourself from scratch. Though this does require a fairly solid knowledge of Mail Transfer agents and configuration via the command line.

Packages to look at are:

SpamAssassin, Postfix (or other MTA), Postgrey, MySQL and MailScanner, ClamAV, Pyzor & Razor

You can find the details for MailScanner at:

[http://www.mailscanner.info/](http://www.mailscanner.info/)

Other useful links:

[http://www.itslot.com/how_to_build_a_spam_filtering_mail_gateway](http://www.itslot.com/how_to_build_a_spam_filtering_mail_gateway)
[http://www.howtoforge.com/greylisting_postfix_postgrey](http://www.howtoforge.com/greylisting_postfix_postgrey)

Hope that at least points you in the correct direction. I built a gateway not too long ago that works very effectively, cuts 4,500 daily incoming mails to just 200 or so deliverables.

Good luck.

---

### Post by starboyhull on 2007-11-09
Thanks for that, we have a reasonable knowledge of mail systems and setting the mx records up, just the linux side of things we are new too.....

Plus trying to find something thats either free or cheap :)

Ill give some of the suggestions a try.......


Thanks

Karl

---

### Post by ubnuturero on 2007-11-09
I'm Using  postgrey  and  very good  results

---

### Post by HermanAB on 2007-11-09
Hmm, you can set up Postfix with Amavisd-new, Spam Assassin and Clamav, with DCC, Razor, SpamHaus and Spamcop RBLs.  To get that lot working will take you 1 to 2 weeks.

Alternatively, you can take the easy way out and install Citadel by using their Easy Install Script and then following their simple instructions to set up SpamAssassin with ClamAV and the RBLs and have it all running in about an hour:  [http://www.citadel.org](http://www.citadel.org)

If you get stuck see the other Citadel threads, or read this older guide first: [http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)  The important thing is to *first* get the DNS set up *properly* with MX, A and PTR records, before you start.

Cheers,

Herman

---

### Post by tavasti on 2007-11-22
Any comments about qpsmtpd?

  Package: qpsmtpd
  Section: universe/mail

  Description: Flexible SMTP daemon for network-level spam detection
   This is a replacement SMTP damon which installs alongside a mail delivery
   and transport system such as Exim, Postfix or Qmail, or used as an SMTP
   proxy for a remote/DMZ MTA.

more with 'apt-cache show qpsmtpd' or at [http://smtpd.develooper.com/](http://smtpd.develooper.com/)

---

