---
title: "Spam Originating from my Computer?"
date: 2012-12-06
forum: Security
---

### Post by hwttdz on 2012-12-06
I'm not too strong on mail configuration.  But I find it very convenient to be able to both send and receive mail on my computer.  This way I can get notifications about things like cronjobs & I can write scripts that process emails as text files.  

I currently have postfix set up as relay with a smarthost using google's smtp server.  I recently received a message addressed to postmaster which appeared to come from my username...  Here are the mail lines corresponding:

```
Dec  6 19:25:11 poseidon postfix/smtpd[31873]: connect from 82.158.242.105.dyn.user.ono.com[82.158.242.105]
Dec  6 19:25:12 poseidon postfix/smtpd[31873]: 39BC61000AC: client=82.158.242.105.dyn.user.ono.com[82.158.242.105]
Dec  6 19:25:12 poseidon postfix/cleanup[31905]: 39BC61000AC: message-id=<201212070122.10694@sudoremont.org.ua>
Dec  6 19:25:12 poseidon postfix/qmgr[1800]: 39BC61000AC: from=<dipivyr@sudoremont.org.ua>, size=881, nrcpt=1 (queue active)
Dec  6 19:25:12 poseidon postfix/cleanup[31905]: CC5BD1000BA: message-id=<201212070122.10694@sudoremont.org.ua>
Dec  6 19:25:12 poseidon postfix/qmgr[1800]: CC5BD1000BA: from=<dipivyr@sudoremont.org.ua>, size=1008, nrcpt=1 (queue active)
Dec  6 19:25:12 poseidon postfix/local[31915]: 39BC61000AC: to=<postmaster@myserver.info>, relay=local, delay=0.78, delays=0.72/0.02/0/0.04, dsn=2.0.0, status=sent (forwarded as CC5BD1000BA)
Dec  6 19:25:12 poseidon postfix/qmgr[1800]: 39BC61000AC: removed
Dec  6 19:25:12 poseidon postfix/smtpd[31873]: disconnect from 82.158.242.105.dyn.user.ono.com[82.158.242.105]
Dec  6 19:25:14 poseidon postfix/smtp[31916]: CC5BD1000BA: to=<joseph.myserver@gmail.com>, orig_to=<postmaster@myserver.info>, relay=smtp.gmail.com[173.194.76.108]:587, delay=1.7, delays=0.03/0.01/0.54/1.1, dsn=2.0.0, status=sent (250 2.0.0 OK 1354839914 f3sm6247225qaj.7)
Dec  6 19:25:14 poseidon postfix/qmgr[1800]: CC5BD1000BA: removed
Dec  6 19:28:33 poseidon postfix/anvil[31875]: statistics: max connection rate 1/60s for (smtp:82.158.242.105) at Dec  6 19:25:11
Dec  6 19:28:33 poseidon postfix/anvil[31875]: statistics: max connection count 1 for (smtp:82.158.242.105) at Dec  6 19:25:11
Dec  6 19:28:33 poseidon postfix/anvil[31875]: statistics: max cache size 1 at Dec  6 19:25:11
```

And here are the full mail headers:
```
Return-Path: <joseph.myserver@gmail.com>
Received: from poseidon (myserver & ipaddress)
        by mx.google.com with ESMTPS id f3sm6247225qaj.7.2012.12.06.16.25.13
        (version=TLSv1/SSLv3 cipher=OTHER);
        Thu, 06 Dec 2012 16:25:13 -0800 (PST)
Received: by poseidon (Postfix)
	id CC5BD1000BA; Thu,  6 Dec 2012 19:25:12 -0500 (EST)
Delivered-To: postmaster@myserver.info
Received: from sudoremont.org.ua (82.158.242.105.dyn.user.ono.com [82.158.242.105])
	by poseidon (Postfix) with SMTP id 39BC61000AC
	for <postmaster@myserver.info>; Thu,  6 Dec 2012 19:25:12 -0500 (EST)
Received: from [127.0.0.1] by 82.158.242.105 with HTTP;
	Fri, 07 Dec 2012 01:22:10 +0200
User-Agent: Thunderbird 2.0.0.23 (X11/20110312 qOs0VOufqrFDqvwAaX8uImH1eXtmIB)
Message-ID: <201212070122.10694@sudoremont.org.ua>
Date: Fri, 07 Dec 2012 01:22:10 +0200
From: Client Support <joseph.myserver@gmail.com>
Subject: Great Offer
To: postmaster@myserver.info
MIME-Version: 1.0
Content-Type: text/plain; charset=utf-8
Content-Transfer-Encoding: 7bit
```

First, how was someone able to send this message?  If I view the log it's clearly coming from a different ip & it's actually tagged with the user agent (though that might be forged?).  Second what can I do to prevent this from happening.  I'm happy if my mail server only accepts outgoing mail from my ip address (though something like ssh keys would be even better).

---

### Post by SeijiSensei on 2012-12-06
That's one of many common spamming tricks.  Remember that the From and To fields in any message can be forged at will.

If you are running Postfix simply to have the machine send you mail, go back to using the default configuration that only listens on the 127.0.0.1 address.  If you do not need to accept inbound mail from the Internet on this machine, then it should not be listening on any external IP addresses.

In main.cf, make sure the mynetworks directive looks like this:

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

---

### Post by lisati on 2012-12-06
You'll need to lock down your server to only accept mail for other domains from your network only: SeijiSensei is on the right track.

You can also report any spam that comes your way using services such as [Spamcop]("http://spamcop.net"), who can, amongst other things, help you identify the origin of the spam and thus who to complain to.

---

### Post by hwttdz on 2012-12-06
Thanks,
I think I've inherited my main.cf from a few too many upgrades.  So I think I'm probably missing a few more directives, like only accepting mail from my networks.  What's the equivalent for reject all, accept from my networks?

What's the difference between?
```
mynetworks_style = host
```
&
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```
the first sure seems simpler (I'm looking at /usr/share/postfix/main.cf.dist).

---

