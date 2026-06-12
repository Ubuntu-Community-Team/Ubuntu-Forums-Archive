---
title: "Postfix"
date: 2009-06-16
forum: Server Platforms
---

### Post by PJDouglas on 2009-06-16
Hi,

I've installed postfix and want to configure it to send all in inbound to exchange and send all outgoing messages from exchange to a smart host.

I currently have postifx configured to send all mail to the smarthost which works fine. Unfortunately I am not receiving any mail from the smarthost (inbound) to my exchange server.

I have checked mail.log but there is nothing logged to say mail is being rejected. 

What is the best way to configure postfix to accept all mail from my exchange and send to to the smarthost and accept all mail from the smarthost and forward it to my exchange?

Many Thanks

Paul.

---

### Post by iponeverything on 2009-06-16
Something is happening to the mail.

On different host install sendmail

```
sudo apt-get install sendmail-bin
```

then run 

```
sendmail -v user@host < /etc/hosts
```


Where user@host is something going to your exchange server and post the SMTP conversation.

---

