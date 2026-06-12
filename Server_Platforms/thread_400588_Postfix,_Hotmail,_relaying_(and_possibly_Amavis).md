---
title: "Postfix, Hotmail, relaying (and possibly Amavis)"
date: 2007-04-03
forum: Server Platforms
---

### Post by xadium on 2007-04-03
Hi

I've got a Postfix server happily running on my floor which is successfully filtering incoming email and sending outgoing email.  I've got a virtually static IP (but not quite, DNS handled by dyndns.org) on my nice, domestic, home cable modem connection.

The issue is that I'm often blacklisted by large email providers who assume that mail coming from dynamic IP blocks hosted by ISPs are probably spam from 0wned Windows boxes.  To avoid this I am looking to continue sending email via my **Postfix -> Amavis -> Postfix -> Big Out There** route unless I get a bounce/unable to deliver, at which point I fall on the mercy of my ISPs own less reliable but more trustworthy SMTP server **Postfix -> Amavis -> Postfix -> Big Out There <- Bounce Back -> Requeue with ISP**

Hopefully that makes sense.  I've tried playing with fallback_relay/smtp_fallback_relay but it never seems to trigger (logs below).  I'd be grateful for an example of how setting this should work because I can only find a thousand copies of postconf(5) smtp(8) etc.  Currently I just have *smtp_fallback_relay=smtp.isp.com:25* in my main.cf.

Thanks

Example log from bounce:
 
```
Apr  3 22:56:12 xadium postfix/smtpd[23307]: connect from localhost.localdomain[127.0.0.1]
Apr  3 22:56:12 xadium postfix/smtpd[23307]: E7CB98D070: client=localhost.localdomain[127.0.0.1]
Apr  3 22:56:12 xadium postfix/cleanup[23311]: E7CB98D070: message-id=<53482.192.168.1.4.1175637372.squirrel@xxxxx>
Apr  3 22:56:13 xadium postfix/qmgr[23287]: E7CB98D070: from=<xxx>, size=4963, nrcpt=1 (queue active)
Apr  3 22:56:13 xadium postfix/smtpd[23307]: disconnect from localhost.localdomain[127.0.0.1]
Apr  3 22:56:18 xadium postfix/smtpd[23323]: connect from localhost.localdomain[127.0.0.1]
Apr  3 22:56:18 xadium postfix/smtpd[23323]: A42828A5D1: client=localhost.localdomain[127.0.0.1]
Apr  3 22:56:18 xadium postfix/cleanup[23311]: A42828A5D1: message-id=<53482.192.168.1.4.1175637372.squirrel@xxxx>
Apr  3 22:56:18 xadium postfix/qmgr[23287]: A42828A5D1: from=<xxx>, size=5387, nrcpt=1 (queue active)
Apr  3 22:56:18 xadium amavis[20190]: (20190-05) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <xxxx> -> <xxxx>, Message-ID: <53482.192.168.1.4.1175637372.squirrel@xxxxx>, mail_id: AKskyA-SF6SI, Hits: -1.033, queued_as: A42828A5D1, 5587 ms
Apr  3 22:56:18 xadium postfix/smtp[23312]: E7CB98D070: to=<xxxxx>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.9, delays=0.1/0.18/0.01/5.6, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=20190-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as A42828A5D1)
Apr  3 22:56:18 xadium postfix/qmgr[23287]: E7CB98D070: removed
Apr  3 22:56:18 xadium postfix/smtpd[23323]: disconnect from localhost.localdomain[127.0.0.1]
Apr  3 22:56:19 xadium postfix/smtp[23324]: A42828A5D1: to=<xxxxx>, relay=mx3.hotmail.com[65.54.244.72]:25, delay=0.86, delays=0.08/0.03/0.57/0.19, dsn=5.0.0, status=bounced (host mx3.hotmail.com[65.54.244.72] said: 550 Your e-mail was rejected for policy reasons on this gateway. Reasons for rejection may be related to content such as obscene language, graphics, or spam-like characteristics (or) other reputation problems. For sender troubleshooting information, please go to http://postmaster.msn.com.  Please note: if you are an end-user please contact your E-mail/Internet Service Provider for assistance. (in reply to MAIL FROM command))
Apr  3 22:56:19 xadium postfix/smtp[23324]: A42828A5D1: lost connection with mx3.hotmail.com[65.54.244.72] while sending RCPT TO
Apr  3 22:56:19 xadium postfix/cleanup[23311]: 904908D06F: message-id=<20070403215619.904908D06F@xxxxx>
Apr  3 22:56:19 xadium postfix/qmgr[23287]: 904908D06F: from=<>, size=8008, nrcpt=1 (queue active)
Apr  3 22:56:19 xadium postfix/bounce[23327]: A42828A5D1: sender non-delivery notification: 904908D06F
Apr  3 22:56:19 xadium postfix/qmgr[23287]: A42828A5D1: removed
Apr  3 22:56:19 xadium postfix/local[23328]: 904908D06F: to=<xxxxx>, relay=local, delay=0.08, delays=0.02/0.02/0/0.03, dsn=2.0.0, status=sent (delivered to maildir)
Apr  3 22:56:19 xadium postfix/qmgr[23287]: 904908D06F: removed

```

---

### Post by astrogazer on 2007-04-04
I cannot give you a definite answer on why Hotmail is bouncing your mails but I can speculate.

a. You do not have SPF records, Hotmail is known to use them. Altough I doubt this is
the reason you might try it as it is very easy to implement.

b. Your reverse IP resolution is not the same as the your domain-and there is no way
you can fix this since you have a dynamic IP.

c. The IPs you are being given by your ISP have been used by other users before you
and they might have blacklisted for sending spam.

d. Set the same hostname for incoming mail (MX record) and your outgoing server (HELO).

---

### Post by xadium on 2007-04-04
Hi

Thanks for the response, in turn:

(a)  I have and it is.  I'm now mooting DKIM in case that will make the slightest different, I'm guessing not <sigh>

(b)  Aye.  Ach.

(c)  Aye.  I have checked for this and it doesn't seem to be (I used the trustedsource.org website Microsoft refer to in their unhelpful guidance on [http://postmaster.msn.com](http://postmaster.msn.com) and it looks good from there.  I've had the IP for something approaching a year or so..)

(d)  Is this something I haven't done?  I've changed so much now I've started to lose the plot - what do I need to compare, my MX record in DNS versus my SMTP banner?

Thanks for your advice!

Ali

---

