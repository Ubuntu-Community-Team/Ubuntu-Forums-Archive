---
title: "Yahoo keeps mark mail from my server as SPAM"
date: 2010-08-08
forum: Server Platforms
---

### Post by minhnghivn on 2010-08-08
I run my own VPS with a static IP. Mails from my server (Postfix) can go directly to Gmail, Hotmail inbox.

But with Yahoo, it keeps mark my mails as SPAM although my mails pass all the authentication tests:

- DKIM
- Domain key
- SPF

Maybe you would like to see Yahoo headers:

```

Received-SPF: **pass** (mta1161.mail.sk1.yahoo.com: domain of test@vietnamheavymotobiketravel.com designates 123.30.130.117 as permitted sender)
...
Authentication-Results: mta1023.mail.ac4.yahoo.com  from=vietnamheavymotobiketravel.com; **domainkeys=pass** (ok);  from=vietnamheavymotobiketravel.com; **dkim=pass** (ok)
...

```Any help is highly appreciated

Thanks
Nghi

---

### Post by lisati on 2010-08-08
Your server's IP might be listed in a [DNSBL]("http://en.wikipedia.org/wiki/DNSBL") somewhere that is triggering Yahoo's spam filter. 

Here are some places you can check:
[WhatIsMyIPAddress]("http://whatismyipaddress.com/blacklist-check")
[Debouncer]("http://whatismyipaddress.com/blacklist-check")
[BlacklistAlert]("http://www.blacklistalert.org/")
[lisati.homelinux.com/rbltest]("http://lisati.homelinux.com/rbltest") (you can add "?ip=x.x.x.x" to the URL, without the quotes and where x.x.x.x is the IP address of your server)

---

### Post by minhnghivn on 2010-08-08
I've checked it, only 5% of the spam databases list my IP as "spam source"... One thing, if any of the target Yahoo accounts replies to the "spam" message from my domain, then, the next time I send mail to them, my mail are not treated as spam (only for that Y! account)

So, how I can fix this? is there anything that i'm missing?

---

### Post by lisati on 2010-08-08
As far as I'm concerned Yahoo's spam filtering leaves something to be desired. I've contacted them several times about spam I've received and problems I've noticed with their servers' configuration, and usually get an automated response which is less than helpful.

---

### Post by minhnghivn on 2010-08-08
Maybe that's Yahoo policy that passing DKIM, DomainKey, SPF  test as well as not being listed in Spamhaus does not mean your email is accepted. Normally the policy is not disclosed because they are afraid that spammers will somehow find out the workaround to those filters.

The key is to figure out what Yahoo cares about... It's been annoying me for days...

Gmail does accept all my mails at the moment

---

