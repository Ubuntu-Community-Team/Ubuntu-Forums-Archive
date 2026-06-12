---
title: "Found a postfix + Gmail smarthost howto geared toward ubuntu"
date: 2007-01-01
forum: Server Platforms
---

### Post by modmans2ndcoming on 2007-01-01
I was looking around my news sites and found this how-to posted to Newsvine about setting up a postfix system that uses gmail as a smarthost and sends via port 587 to avoid port 25 blocking. It works for me... I am on edgy on a duron 1.1 GHz CPU. 

[Hope this helps folks out]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps")

---

### Post by K.Mandla on 2007-01-05
(Moved to Servers and Security. ;) )

---

### Post by maggotbrain on 2007-01-15
Thanks for posting the link to this article.
I've had this on my todo list since I discovered the article sometime last week, and just got it set up, this evening.

Since I had already had Postfix configured and operational on my local server, I was able to skip ahead to step 6 to get this working.

---

### Post by RichJacot on 2007-02-05
Thank you for the howto, but I'm getting the following and can't seem to google anything useful to get me headed in the right direction.

```
Feb  5 12:08:05 borg postfix/qmgr[18463]: 85D37281B7: from=<rjacot@borg.superpages.com>, size=599, nrcpt=1 (queue active)
Feb  5 12:08:06 borg postfix/smtp[20250]: setting up TLS connection to smtp.gmail.com
Feb  5 12:08:06 borg postfix/smtp[20250]: certificate verification failed for smtp.gmail.com: num=20:unable to get local issuer certificate
Feb  5 12:08:06 borg postfix/smtp[20250]: SSL_connect error to smtp.gmail.com: -1
Feb  5 12:08:06 borg postfix/smtp[20250]: warning: TLS library problem: 20250:error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed:s3_clnt.c:894:
Feb  5 12:08:06 borg postfix/smtp[20250]: 85D37281B7: to=<rich.jacot@gmail.com>, relay=smtp.gmail.com[72.14.247.109]:587, delay=3634, delays=3633/0.04/0.37/0, dsn=4.7.5, status=deferred (Cannot start TLS: handshake failure)

```

Does anyone have any ideas to get me head down the right path?

TIA

---

### Post by Kosh42 on 2007-04-17
I get the same problem:

```
Apr 17 14:40:01 vorlon postfix/smtp[17680]: setting up TLS connection to smtp.gmail.com
Apr 17 14:40:01 vorlon postfix/smtp[17680]: certificate verification failed for smtp.gmail.com: num=20:unable to get local issuer certificate
Apr 17 14:40:01 vorlon postfix/smtp[17680]: SSL_connect error to smtp.gmail.com: -1
Apr 17 14:40:01 vorlon postfix/smtp[17680]: warning: TLS library problem: 17680:error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed:s3_clnt.c:894:
Apr 17 14:40:01 vorlon postfix/smtp[17682]: setting up TLS connection to smtp.gmail.com
Apr 17 14:40:01 vorlon postfix/smtp[17680]: 7CD554A4555: to=<kosh42efg@gmail.com>, orig_to=<tim>, relay=smtp.gmail.com[66.249.93.109]:587, delay=0.35, delays=0.01/0.04/0.3/0, dsn=4.7.5, status=deferred (Cannot start TLS: handshake failure)
Apr 17 14:40:01 vorlon postfix/smtp[17682]: certificate verification failed for smtp.gmail.com: num=20:unable to get local issuer certificate
Apr 17 14:40:01 vorlon postfix/smtp[17682]: SSL_connect error to smtp.gmail.com: -1
Apr 17 14:40:01 vorlon postfix/smtp[17682]: warning: TLS library problem: 17682:error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed:s3_clnt.c:894:
Apr 17 14:40:01 vorlon postfix/smtp[17682]: 88B204A43D1: to=<kosh42efg@gmail.com>, orig_to=<root>, relay=smtp.gmail.com[66.249.93.111]:587, delay=0.36, delays=0.01/0.02/0.33/0, dsn=4.7.5, status=deferred (Cannot start TLS: handshake failure)

```

Any ideas?

---

### Post by modmans2ndcoming on 2007-12-03
I went back to this article and found a comment that fixes the problem:

> These warnings are because postfix doesn't know where to find the Thawte
certificate that gmail used to sign its own certificate. Ubuntu
includes it in its ssl package. You need to append it to the
cacert.pem file you generated earlier. 

cat /etc/ssl/certs/Thawte_Premium_Server_CA.pem >> cacert.pem " 

---

### Post by Oen386 on 2007-12-23
Wow.. glad I found this...

My problem is when I try the comment suggested I get...

```
:/etc/postfix# cat /etc/ssl/certs/Thawte_Premium_Server_CA.pem >> cacert.pem
cat: /etc/ssl/certs/Thawte_Premium_Server_CA.pem: No such file or directory

```

Help anyone?

---

### Post by Oen386 on 2007-12-23
Found the answer... its working great!

---

### Post by djotaku on 2008-03-05
Hey man!  Thank you sooo much!  I was following [this tutorial]("http://souptonuts.sourceforge.net/postfix_tutorial.html") and it didn't mention the Thawte.  I was able to take your suggestions and adopt it to my FreeBSD server - they are stored in ---

/usr/src/crypto/openssl/certs/thawteCb.pem
/usr/src/crypto/openssl/certs/thawteCp.pem

and using the cat .. >> command I was able to make it work.

I've been working on this off and on for about a year now and I finally got it solved.  Thanks a ton!

This is why I run Ubuntu on my laptop - you guys are a wonderful community!

---

### Post by mattm591 on 2008-03-20
When I run
"sudo echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf"

I get the error
"-bash: /etc/postfix/sasl/smtpd.conf: Permission denied"

Anyone got any ideas why this is?

Thanks

---

