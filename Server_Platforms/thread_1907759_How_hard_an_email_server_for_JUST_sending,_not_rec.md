---
title: "How hard: an email server for JUST sending, not receiving?"
date: 2012-01-12
forum: Server Platforms
---

### Post by garfonzo on 2012-01-12
Hey folks:

I need to send upwards of a thousand emails every now and then for business purposes. I have a Python program that handles creating the emails based on the recipient. For now, I connect to my Gmail account and send all the email through Gmail. The problem is that Gmail puts limits on how many emails you can send in a 24 hour period. 

I'm wondering how hard it would be to set up a mail server for ONLY sending emails, never receiving? What address would the emails be sent from? What kind of maintenance would I need to worry about? Is it worth the effort?

Thanks

---

### Post by HermanAB on 2012-01-12
You can use nullmailer and forward through your ISP mail server (until they shut down your account for spamming).

Nullmailer is the easiest way to send mail - Google is your friend.

---

### Post by spynappels on 2012-01-12
> **HermanAB said:**
> (until they shut down your account for spamming)

And they WILL do that unless you are on a connection/contract which explicitly allows you to send mass emails for legitimate marketing or other purposes. You also run the risk of being blacklisted by other watchdogs, not just your ISP.

---

### Post by dazman19 on 2012-01-12
i set up exim4. 

it was extremely easy. If you google it you will find an example.  I did this only the other day, it was on debian6 squeeze. But I restricted the IP's that could connect to the mail server. Can use ranges too: like 192.168.22.0/24 etc. but if one of the machines on that range gets hacked and sends spam then you can get blacklisted aswell.

---

### Post by surfer on 2012-01-12
also postfix should work.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

