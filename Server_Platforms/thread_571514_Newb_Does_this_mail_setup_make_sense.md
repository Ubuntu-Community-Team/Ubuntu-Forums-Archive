---
title: "Newb: Does this mail setup make sense?"
date: 2007-10-09
forum: Server Platforms
---

### Post by Smartin on 2007-10-09
Hi,

I'm wanting to set up a central mail-store using Cyrus. This is mainly for access inside my LAN but if I can get to my mail from outside, that would be a bonus. I have dyndns set up already.

I also want some really good spam filtering.

What I *don't* need is an outgoing smtp server. It will only get hacked and start spewing spam. Don't want to go there.

So... I was thinking: Fetchmail to pop the mail from my ISP, passing the mail to Mailscanner for spam filtering and then ending up in Cyrus for me to read.

Does Postfix have to be in the mix? I'm hoping not as my brain hurts just writing this...

Perhaps it needs to be there to pass the mail from one app to another...?

Any good pointers/howto's ?

Thanks!

Simon

---

### Post by HermanAB on 2007-10-09
You don't need a MTA like Postfix if you use mail clients that send directly to the ISP mail server.

Here is a rather old Procmail guide that more or less describes what you want to do:
[http://www.aeronetworks.ca/procmail-howto.html](http://www.aeronetworks.ca/procmail-howto.html)

Cheers,

H.

---

### Post by Smartin on 2007-10-09
> **HermanAB said:**
> You don't need a MTA like Postfix if you use mail clients that send directly to the ISP mail server.

Here is a rather old Procmail guide that more or less describes what you want to do:
[http://www.aeronetworks.ca/procmail-howto.html](http://www.aeronetworks.ca/procmail-howto.html)

Cheers,

H.

Herman,

Many thanks for that. I'll check it out.

Simon

---

### Post by HermanAB on 2007-10-09
I've run a half-baked system like that for years, then upgraded to a full blown postfix with spamassassin and clamav and nowadays I run  Citadel, which is the best thing ever.  It only takes about 20 minutes to install and it is zero maintenance, so check it out: [http://www.citadel.org](http://www.citadel.org) (budget a couple hours if you add SpamAssassin and ClamAV, since you have to test it properly).

Citadel is self contained, has a database back-end, it is secure and it Just Works (TM).  Just run Easy Install and la voila...

Cheers,

H.

---

### Post by Smartin on 2007-10-09
Herman,

Thanks for that but why is the above setup half-baked?

Did you change your mind as regards postfix? Should I be using it rather than procmail?

The other thing I don't understand is which end to start from. Do I start with configuring fetchmail or the other end with Cyrus?

I'm wanting to learn about setting these things up so I'm happy to tinker with the various apps as opposed to something like Citadel.

Thanks again!

Simon

---

### Post by HermanAB on 2007-10-09
Well, just half-baked as opposed to full featured - kinda lazy-man's mail system, but it will work alright.

A full featured Postfix system turned out to be a lot of hassle to install and maintain.  I used it for about 5 years, so it is good, but compared to Citadel it kinda pales.  

If you want to configure Postfix to do what Citadel does, then you need the following:
postfix, smtp-auth, amavisd-new, spamassassin, clamav, roundcube, dovecot, mysql, apache, webcal, webmin and virtualmin and then it is still not as nice and configuring that fat lot of schtuff will keep you busy for about 2 weeks full time, as opposed to 1 hour or so with Citadel.  

So basically, I switched to Citadel since I just don't have the time to waste on other methods. 

As a bonus, Citadel is more efficient and scales better - it uses less CPU and much less disk space since it saves each message only once, no matter how many users it goes to.

Cheers,

H.

---

### Post by Smartin on 2007-10-09
> **HermanAB said:**
> 

So basically, I switched to Citadel since I just don't have the time to waste on other methods. 

H.

Herman,

Hmmm, fair enough...

And I can still hook up something like Mailscanner to do the anti-spam/virus stuff?

Simon

---

### Post by HermanAB on 2007-10-09
Citadel has a direct hook for SpamAssassin and uses a special little SpamAssassin script to hook ClamAV:
[http://www.citadel.org/doku.php/documentation:citadel_with_spamassassin_and_clamav](http://www.citadel.org/doku.php/documentation:citadel_with_spamassassin_and_clamav)

It really can't be much easier, so it is worth playing with it a bit.  See this somewhat older guide (It is even easier now than when I wrote that):
[http://www.aeronetworks.ca/citadel-howto.html](http://www.aeronetworks.ca/citadel-howto.html)

I had it running on my laptop before I installed it on a server.

Cheers,

H.

---

