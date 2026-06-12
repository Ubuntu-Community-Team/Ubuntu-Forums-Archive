---
title: "Sendmail problem in 7.04 server"
date: 2008-06-30
forum: Server Platforms
---

### Post by kthdsn on 2008-06-30
Hi all,

I have 7.04 installed on my server and I have some php email forms on my websites hosted on the server.  I have sendmail running.  I didn't change any of the setup for sendmail, just had it however it came.  Things used to be fine, people could send me email through my email forms no problem.

Today I realised that I hadn't received any emails from my sites for a while, I don't know how long.  I have however received mail from a php script that runs from a cron job, and sends email to me and several other people.  Just not from my email forms.

I checked my mail.log and this is the line from one of the emails that I didn't receive:

```
Jun 30 18:54:55 kthdsn sm-mta[5972]: m5UNQtuJ001414: to=<Kate@goalorganiser.com>, ctladdr=<root@kthdsn.com> (0/0), delay=00:28:00, xdelay=00:00:16, mailer=esmtp, pri=390351, relay=mail4.zoneedit.com. [66.223.51.217], dsn=4.7.1, stat=Deferred: 450 4.7.1 Client host rejected: cannot find your hostname, [208.100.55.237]

```

I use zoneedit for DNS and it catches all my emails and forwards them to my gmail.  The IP address it couldn't find is the address of my server.

I have no idea what that means or what to do about it.  I've tried google but everything I found was WAY over my head.  If anyone could explain it in plain english (and to a girl :)) I'd really appreciate it.

Thanks!

---

### Post by windependence on 2008-07-01
Install postfix, you will be way happier and way more secure. It is a drop in replacement for sendmail so it will work just like sendmail but is way easier to config and much safer.

What is zoneedit?

-Tim

---

### Post by kthdsn on 2008-07-01
Thanks, I'll try postfix.  I think I've used it before when I shared a server with a more techie friend.

Zoneedit is a DNS service that I use because it's very simple to understand and manage.  It works in plain english which is more than I can say for my domain provider!

---

### Post by kthdsn on 2008-07-01
I'm getting the same errors with postfix.  It seems that I haven't been receiving emails since January (I'm clearly not very observant), there are undelivered messages in /var/mail/root starting from January 1st.

I was looking on some other forums to try and find out more, and I'm wondering if there's a problem with my IP address.  On one forum a person said that they were getting the same error even though their host was right, so I checked mine:

```
host 208.100.55.237
Host 237.55.100.208.in-addr.arpa not found: 2(SERVFAIL)

```

That doesn't look good, although I have no idea what it means.  Can anyone explain this to me?

---

