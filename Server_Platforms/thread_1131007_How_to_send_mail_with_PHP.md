---
title: "How to send mail with PHP"
date: 2009-04-20
forum: Server Platforms
---

### Post by leemid on 2009-04-20
Hi,
I'm trying to get a PHP script to send mail using the mail() function. I don't need anything special, just to mail the contents of a form to a user. I've installed sendmail and it seems to work up to a point but then I find the following error in the logs:

```
Apr 20 16:32:00 mkalimu sm-mta[5516]: starting daemon (8.14.3): SMTP+queueing@00:10:00
Apr 20 16:35:49 mkalimu sendmail[6552]: n3KFZnHK006552: from=www-data, size=103, class=0, nrcpts=1, msgid=<200904201535.n3KFZnHK006552@mkalimu>, relay=www-data@localhost
Apr 20 16:35:50 mkalimu sm-mta[6553]: n3KFZnc6006553: from=<www-data@mkalimu>, size=314, class=0, nrcpts=1, msgid=<200904201535.n3KFZnHK006552@mkalimu>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Apr 20 16:35:50 mkalimu sendmail[6552]: n3KFZnHK006552: to=xxx@yyy.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30103, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (n3KFZnc6006553 Message accepted for delivery)
Apr 20 16:35:51 mkalimu sm-mta[6555]: n3KFZnc6006553: to=<xxx@yyy.com>, ctladdr=<www-data@mkalimu> (33/33), delay=00:00:02, xdelay=00:00:01, mailer=esmtp, pri=120314, relay=mx00.1and1.co.uk. [212.227.15.169], dsn=4.0.0, stat=Deferred: 421 unable to verify sender domain
Apr 20 16:35:51 mkalimu sm-mta[6555]: n3KFZnc6006553: to=<xxx@yyy.com>, ctladdr=<www-data@mkalimu> (33/33), delay=00:00:02, xdelay=00:00:01, mailer=esmtp, pri=120314, relay=mx01.1and1.co.uk. [212.227.15.134], dsn=4.0.0, stat=Deferred: 421 unable to verify sender domain
```

'Mkalimu' is the name of the server I'm using to test sending mail. I guess the receiving server (which I presume is 'mx01.1and1.co.uk') can't resolve that server name and refuses the message. However I don't know how to change it!

If anyone can help me with this you'll have my eternal gratitude. I know it's something simple, I just can't figure it out. If not, thanks for looking!

Lee

---

### Post by nandemonai on 2009-04-20
Pretty sure most mail servers want a fully qualified domain name before they'll accept incoming mail.

Helps prevent spam.

---

### Post by HermanAB on 2009-04-20
If you already have a working mail server somewhere (maybe your ISP mail server), then you can use nullmailer to forward cruft from a web application.  Nullmailer only has two things to configure: Who you are and where to send the message to.  There is nothing simpler than that.  Some mild googling will find it.

---

### Post by leemid on 2009-04-21
Right, I seem to have sorted it. The mail server wants a FQDN, so nandemonai thank you for that. I modified my /etc/hosts file in the style of [this howto]("http://www.howtoforge.com/perfect-server-ubuntu-8.10-p3"), created a matching subdomain with my hosting provider and it all works jolly well.

HermanAB, many thanks telling me about nullmailer. It's just the thing I'm looking for, and I have a feeling I'll be using that elsewhere in my web apps!

Cheers everyone, and thanks for your quick replies!

Lee

---

