---
title: "Seeking recommendation on spam arrestor"
date: 2007-12-06
forum: Server Platforms
---

### Post by satimis on 2007-12-06
Hi folks,


Ubuntu 7.04 server amd64
Apache2
Postfix 2.3.8


Spam are found on Maildir. Following packages are on repo;
spamassassin
spamfilter
spamass-milter

Which of them would you recommend? Thanks.


smtpguard is also found on repo. Any folk tested this package before? What is your comment? 


B.R.
satimis

---

### Post by HermanAB on 2007-12-06
SpamAssassin with Spamhaus and Spamcop RBLs, plus ClamAV is pretty much the industry standard.

Cheers,

Herman

---

### Post by satimis on 2007-12-07
> **HermanAB said:**
> SpamAssassin with Spamhaus and Spamcop RBLs, plus ClamAV is pretty much the industry standard.
Hi Herman


Thanks for your advice.


Spamhaus and Spamcop are projects.  Googling brought me serveral documents.  


Spamhaus
========

[http://www.spamhaus.org/statistics/networks.lasso](http://www.spamhaus.org/statistics/networks.lasso)
The Spamhaus Block List
[http://www.spamhaus.org/sbl/](http://www.spamhaus.org/sbl/)


The Spamhaus Project
[http://en.wikipedia.org/wiki/The_Spamhaus_Project](http://en.wikipedia.org/wiki/The_Spamhaus_Project)


Postfix Antispam
[http://calum.org/posts/postfix-antispam](http://calum.org/posts/postfix-antispam)


Sample Procmail Recipes
A Hands-on How-toSM
[http://handsonhowto.com/pmail102.html](http://handsonhowto.com/pmail102.html)


the Procmail Filters Kit
[http://web.bilkent.edu.tr/mirrors/Sendmail/www.wolfenet.com/jhardin/procmail-kit.html](http://web.bilkent.edu.tr/mirrors/Sendmail/www.wolfenet.com/jhardin/procmail-kit.html)





Spamcop
=======
[http://www.spamcop.net/](http://www.spamcop.net/)
[http://spamcop.net/bl.shtml](http://spamcop.net/bl.shtml)

wiki
[http://en.wikipedia.org/wiki/SpamCop](http://en.wikipedia.org/wiki/SpamCop)


Welcome to the SpamCop Email System
[http://mail.spamcop.net/](http://mail.spamcop.net/)


etc.


Which of them shall I follow?  Please shed me some light.  TIA


B.R.
satimis

---

### Post by nutz on 2007-12-07
Yes indeed.

---

### Post by HermanAB on 2007-12-07
Install Postfix, then add the two RBLs to main.cf:

```
maps_rbl_domains = 
    bl.spamcop.net,
    xbl.spamhaus.org

smtpd_recipient_restrictions =
    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    reject_maps_rbl, 
    permit
```

See the guides here:
[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)

Specifically read up on postfix + amavisd-new + spamasassin.

You can get Amavisd-new here:
[http://www.ijs.si/software/amavisd/](http://www.ijs.si/software/amavisd/)

Amavisd-new makes setting up Spam Assassin and ClamAV very easy.

Hope that helps!

H.

---

### Post by satimis on 2007-12-08
Hi HermanAB,


Thanks for your advice.


> 
See the guides here:
[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)

Specifically read up on postfix + amavisd-new + spamasassin.

Whether you meant;

1)
Postifx w/ SASL + Courier IMAP w/ SSL + Maildrop + MySQL + SpamAssassin
[http://www.phparchitecture.com/howto_show.php?id=2](http://www.phparchitecture.com/howto_show.php?id=2)

OR

2)
Postfix+MySQL+Courier+SpamAssassin+Clamav+Amavisd-new+SASL+Maildrop+Squirrelmail  howto by Genco Yilmaz. Uses the postfixmanager user management tool.
Postfix Virtual
[http://www.postfixvirtual.net/](http://www.postfixvirtual.net/)

But I'm running Linux users on the mail server NOT virtual users.


> 
You can get Amavisd-new here:
[http://www.ijs.si/software/amavisd/](http://www.ijs.si/software/amavisd/)

Amavisd-new makes setting up Spam Assassin and ClamAV very easy.

Should I follow this doc installing Amavisd-new first before SpamAssassin?


TIA


Others noted.


B.R.
satimis

---

### Post by jflaker on 2007-12-08
> **HermanAB said:**
> SpamAssassin with Spamhaus and Spamcop RBLs, plus ClamAV is pretty much the industry standard.

Cheers,

Herman

My company uses a Barracuda Networks Spam Filter and the Blacklists are exactly that...........While spam filtering is never 100%, out of the 20K/day incoming messages, only a few get by on a daily basis.

---

### Post by HermanAB on 2007-12-08
Look at the Postfix howtos to get a general idea of how to do things, then head over to the amavisd-new site and follow their instructions.  It is really simple actually, since Amavisd-new is just a little Perl script that you extract and put somewhere.  When Amavis starts up, it scans your system to find ClamAV and SpamAssassin and automatically makes it all work together.

So in effect, you install SpamAssasin (spamd) and ClamAV (clamd and freshclam) separately, then Amavisd-new pulls it all together for you automagically.

What happens is that you configure Postfix with an extra listener (usually port 10025) and configure Amavisd-new to listen on a port (usually 10024).  Then when a message comes in on port 25, Postfix forwards it to Amavis on port 10024.  Amavis unpacks any zipped up attachments and calls Spam Assassin and ClamAV to analyze the schtuff.  When done, it forwards the message back to Postfix on port 10025.  Postfix decides where to deliver the message to: spambox, virusbox or usermailbox.

'Hope that helps!

Herman

---

