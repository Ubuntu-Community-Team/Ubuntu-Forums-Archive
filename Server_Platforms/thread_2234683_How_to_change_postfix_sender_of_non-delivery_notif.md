---
title: "How to change postfix sender of non-delivery notification"
date: 2014-07-16
forum: Server Platforms
---

### Post by peyu on 2014-07-16
Hi everybody,
I have a postfix server running with Ubuntu Server 12.04 LTS. 
I'm using smtp2go.com as a relay server, because my server has a dynamic ip address so all my emails get blocked by spamhauss if i send it directly.
Smtp2go use the "from address" to know if you can send an email or not. 
But in the case of the non-delivery notification, it seems that postfix is not setting anything in from:
```
Jul 16 11:12:27 batz postfix/bounce[2756]: 9F1913017EE: sender non-delivery notification: 1CE443017F3
Jul 16 11:12:27 batz postfix/qmgr[22039]: 1CE443017F3: from=<>, size=3242, nrcpt=1 (queue active)
Jul 16 11:12:27 batz postfix/qmgr[22039]: 9F1913017EE: removed
Jul 16 11:12:27 batz postfix/smtp[2750]: 1CE443017F3: to=<xxx@xxx>, relay=smtp2go.com[207.58.142.213]:2525, delay=0.66, delays=0.02/0/0.48/0.16, dsn=5.0.0, status=bounced (host smtp2go.com[207.58.142.213] said: 550 You must specify a sender address (in reply to MAIL FROM command))
```
After searching in postfix documentation, i saw you can modify the bounce template and define there the sender email (but I don't know if it's the send inside the mail or the real sender).
In [Bounce Manpage]("http://manpages.ubuntu.com/manpages/precise/man5/bounce.5.html"), it says:
> To create a customized bounce template file, create a temporary copy of
       the file /etc/postfix/bounce.cf.default and edit the temporary file.

But I don't have this file /etc/postfix/bounce.cf.default.

Any ideas?
Thanks.

---

### Post by lisati on 2014-07-16
Have a look here: [http://www.howtoforge.com/configure-custom-postfix-bounce-messages](http://www.howtoforge.com/configure-custom-postfix-bounce-messages)

You might have to scroll down the page to see an example of the contents of the bounce.cf file.

---

### Post by peyu on 2014-07-16
Thanks lisati !
I'll try and I report back.

---

### Post by SeijiSensei on 2014-07-16
Just make sure it uses a common non-delivery sender name like "postmaster@yourdomain" or "MAILER-DAEMON@yourdomain."  People like me have mail filters in place to handle non-delivery notices that look for standard names like postmaster.

---

### Post by peyu on 2014-07-22
It's what I suspected. I installed a custom bounce message, setting From: postmaster, but this field is only set in the message content. 
I still have the same problem:
```
Jul 22 12:06:42 batz postfix/bounce[15517]: EA036300079: sender non-delivery notification: B3820301828
Jul 22 12:06:42 batz postfix/qmgr[15456]: B3820301828: from=<>, size=3257, nrcpt=1 (queue active)
Jul 22 12:06:42 batz postfix/qmgr[15456]: EA036300079: removed
Jul 22 12:06:43 batz postfix/smtp[15512]: B3820301828: to=<xxx@xxx>, relay=smtp2go.com[207.58.142.213]:2525, delay=0.75, delays=0.03/0/0.57/0.16, dsn=5.0.0, status=bounced (host smtp2go.com[207.58.142.213] said: 550 You must specify a sender address (in reply to MAIL FROM command))
Jul 22 12:06:43 batz postfix/qmgr[15456]: B3820301828: removed
```
So any idea on how can I set "from" to something not empty ?

---

### Post by SeijiSensei on 2014-07-22
Well, as I suspected, that is the nature of the standard for non-delivery notifications.  Bounce messages use an empty envelope sender ("<>") to avoid bounce loops.  See RFC2821 for details, particularly [section 4.5.5](http://tools.ietf.org/html/rfc2821#section-4.5.5).

I'd have a talk with your relay host provider. Not relaying bounce messages with empty MAIL FROM addresses violates standards.

---

### Post by peyu on 2014-07-23
Thanks, I'll talk to them. I will also look for a way to send a copy of the bounced messages to a special account and then with sieve send it back to the original sender, so I can apply it if smtp2go is not able to change their service.

---

