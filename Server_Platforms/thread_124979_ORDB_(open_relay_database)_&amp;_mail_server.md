---
title: "ORDB (open relay database) &amp; mail server"
date: 2006-02-02
forum: Server Platforms
---

### Post by Zelut on 2006-02-02
I was wondering if anyone had any experience using ORDB with a mail server.  I currently run a small mail server/webhost and I want to cut down on spam (who doesn't, right?)  Currently I have spamassassin installed which nicely tags any spam as such but I would like to completely block known spammers from touching my machines.

From what I'm reading [www.ordb.org](www.ordb.org) keeps a listing of known spam relays & can block those (I would use this as part of postfix).

Would love to hear feedback on pros & cons of this idea &/or personal experience.

Thanks

---

### Post by robert_pectol on 2006-02-03
Highly recommended in my opinion!  I've been using ORDB and the SBL-XBL list from Spamhaus on my mail servers for a couple of years now.  Just using the blacklists alone seems to block over 90% of the spam that would have been downloaded and delivered to our users!  Beyond that, a good filter (such as Spamassassin) can nicely handle the ones that slip through.  With all that in place, it's rare to get even one piece of spam per week!  The only, "false positives" we see are when a user's ISP's mailserver has ended up on the blacklist for one reason or another, and that user tries to send one of our users an e-mail.  Most ISP's are real quick to "fix" whatever it is that caused them to get blacklisted since their users begin complaining when their mails are being refused.  The fact is, many organizations are jumping on board with the use of reputable blacklists, such as the ones I mentioned above.  The more that use them, the more effective they become.

Now, having said all that, if you (or any of your users) absolutely cannot afford any false positives, then blacklisting probably shouldn't be used.  A nicely "tweaked out" Bayesian filter with the option to save suspected spam for further review, is probably a better approach in that instance.  Luckily, all of our users are aware and in support of our use of the blacklists, regardless of the slight chance of a false positive.  If you can use them, they'll save you from wasted bandwidth (your mailserver will sever the connection before the delivery begins), cpu cycles (for the spam filtering mechanisms, delivery, etc.), and the aggrivation that spam brings in general.  Anyway, I hope that helps you a little.

---

### Post by Zelut on 2006-02-03
Thanks for the good advice.  I actually setup the filter to try out last nite about 5:00 and so far I've stopped 36 spam messages to one domain!  (I wrote a little script to grep the mail log for notices).  I think I'm going to love this filtering!

I will make sure my users are aware of the filtering.  I'm sure they'll more appreciate the lack of spam than the occasional lost email.

---

