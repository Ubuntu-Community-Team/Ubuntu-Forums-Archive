---
title: "How to diagnose outgoing smtp on Gutsy with Posfix"
date: 2008-04-09
forum: Server Platforms
---

### Post by Poleh on 2008-04-09
Hi folks

am running Gutsy with Postfix and Courier IMAP/POP3 which has been working swimingly for 3 weeks now.

Recently I have noticed that mail doesn't seem to get through to some/all hotmail accounts for some reason. I have checked my /var/log/mail.log|err|info for information but it doesn't seem to give me much, or I don't understand it. Here's a sample (usernames and IP's changed where applicable):

```

Apr  9 22:19:18 server1 postfix/smtpd[11176]: 453BA2F40AB: client=unknown[x.x.x.x], sasl_method=LOGIN, sasl_username=username
Apr  9 22:19:18 server1 postfix/cleanup[11214]: 453BA2F40AB: message-id=<001201c89a2b$e059ec80$a10dc580$@com>
Apr  9 22:19:18 server1 postfix/qmgr[6692]: 453BA2F40AB: from=<someone@address.com>, size=1586, nrcpt=1 (queue active)
Apr  9 22:19:19 server1 postfix/smtp[11215]: 453BA2F40AB: to=<anaddress@hotmail.com>, relay=mx4.hotmail.com[65.54.244.232]:25, delay=1.4, delays=0.15/0/0.59/0.63, dsn=2.0.0, status=sent (250  <001201c89a2b$e059ec80$a10dc580$@com> Queued mail for delivery)
Apr  9 22:19:19 server1 postfix/qmgr[6692]: 453BA2F40AB: removed

```

Am I correct in understanding that this is the INCOMING log from me connecting with my mail client? Where does one find the outgoing SMTP log information for postfix? Or is there a place to turn on more verbose logging?

I must stress, all other mail appears to be delivered fine, seems that it's just hotmail for some reason ... which indicates it's probably not my system, but I would still like to see the logs to see what's going on.

Thanks in advance.

---

### Post by MJN on 2008-04-09
That log snippet is showing the message being delivered, at least as far as the Hotmail boundary. The '250  <001201c89a2b$e059ec80$a10dc580$@com> Queued mail for delivery' output is the last thing the Hotmail server said to your server and confirms acceptance of the mail... at least into its queue for scanning/delivery.

They will perform a multitude of spam tests post-acceptance and so it is likely that your messages are failing (one of) these tests. One would however hope that they'd send a non-delivery report (which may contain some clue as to why delivery failed) but whether they do or not is completely up to them. Furthermore, given that some of their scanning is done after the SMTP stage they may silently drop suspected spam in order to minimise the risk of backscatter to what might be forged From: addresses.

Mathew

---

### Post by ginge6000 on 2008-04-09
I seem to remember reading somewhere that Hotmail won't accept mail from a dynamic ip.  Is this the case for your server?

---

### Post by Poleh on 2008-04-10
Thanks for your replies folks, as I suspected that's the SMTP outgoing transaction in the logs so all good. And no I don't have a dynamic IP address - and funnily enough the problem seems to have disappeared, at least for now.

One remaining question, is there an option to turn on more verbose logging for postfix?

---

### Post by MJN on 2008-04-11
Sure - add **-v** (or even **-vv**) to the **smtpd** command in the line that starts **smtp** in /etc/postfix/master.cf

Hence, it'll read something along the lines of:

```
smtp      inet  n       -       -       -       -       smtpd -v
```Mathew

---

