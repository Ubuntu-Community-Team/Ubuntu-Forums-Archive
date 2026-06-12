---
title: "Mail server query"
date: 2010-02-02
forum: Server Platforms
---

### Post by Rich78 on 2010-02-02
Hi, I've never setup a mail server before in Linux and I've decided to give it a go using Exim4.

I've pointed my MX records on my host control panel to point to my server by IP, which I assume is correct to route mail to my mail server?

I can send mail from my mail server to my googlemail account via command line and I receive it fine, showing the correct domain where it came from etc.

However receiving seems to be a different issue, I get no bounce back to suggest there was a problem when I send mail to the new mail server but the mail command when I'm logged in as the user expecting the mail shows no mail for user x.

Anything I'm doing wrong?  MX records correct?

Thanks

---

### Post by quietas on 2010-02-02
I've used Exim3 and upgraded to 4, then replaced it with Zimbra. Exim while it works is a pain in the rear. It works, but it's horrible to setup and run. Other misght say they love it, but really it's old tech. I'd really recommend taking a look at something like Zimbra for it's simplicty and rich set of features.

---

### Post by Rich78 on 2010-02-02
Thanks, sent you a pm :)

---

### Post by Rich78 on 2010-02-02
Got another issue with this, decided to stick with Exim4 for the time being as I'm making progress however I've noticed mail stacking up in the queue which appear to be internally generated from some sort of Cron job?  But the Cron seems to be from my DNS host which is really throwing me as to why and how this is happening, I swapped the MX records back to their default ones so it shouldn't be pointing to this server anymore but maybe it's still not finished propagating through yet.

Only detail I've masked with fictitious in the below are my domain name and my server name all other info is valid.

Return-path: <root@mydomain.com>
Envelope-to: [email]root@mydomain.com[/email]
Delivery-date: Tue, 02 Feb 2010 22:10:01 +0000
Received: from root by my-serv-01 with local (Exim 4.69)
	(envelope-from <root@mydomain.com>)
	id 1NcQwb-0005OC-8B
	for [email]root@mydomain.com[/email]; Tue, 02 Feb 2010 22:10:01 +0000
From: [email]root@mydomain.com[/email] (Cron Daemon)
To: [email]root@mydomain.com[/email]
Subject: Cron <root@mydomain.com> ntpdate -u tick.xtrahost.co.uk
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <E1NcQwb-0005OC-8B@my-serv-01>
Date: Tue, 02 Feb 2010 22:10:01 +0000

---

### Post by quietas on 2010-02-02
If I remember from here you need Exim as the MTA to get the mail on to your server and then Courier IMAP to get the mail into user folders.

I found this quickly after remembering that I had a Exim/Courier combo back when we used it years back. [http://blog.edseek.com/~jasonb/articles/exim4_courier/index.html](http://blog.edseek.com/~jasonb/articles/exim4_courier/index.html)

---

### Post by Rich78 on 2010-02-03
Thanks again :D  Will look into it this evening.  I think I'm mistaking it as a total exchange solution.

---

### Post by Rich78 on 2010-02-03
Fresh eyes on this and just to update, the Cron is actually a time sync with my server hosting provider not my DNS host.

I'm confused why this mail is being generated though as it doesn't look to be an error.

---

### Post by Rich78 on 2010-02-05
Fixed with editing crontab and marking ntpdate with a silent flag -s.

Also added Bind9 and configured DNS to start receiving mail.

---

