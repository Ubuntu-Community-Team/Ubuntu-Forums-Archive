---
title: "Postfix/Roundcube: Sender address rejected: need fully-qualified address"
date: 2012-07-14
forum: Server Platforms
---

### Post by mailalot on 2012-07-14
Hello,

I've used tasksel to install the mail services on my brand new ubuntu 12.04 powered dedicated server. Further I've installed roundcube webmail client.
The system is basically working (mails can be send/received using imap), expect when i trying to send an email to my isp, which causes the following error message in /var/log/mail.log

Jul 15 01:59:21 one postfix/smtp[2019]: 0D0399C025F: to=<my@myisp.com>, relay=sm01.myisp.com[x.x.x.x]:25, delay=0.56, delays=0.4/0/0.06/0.1, dsn=5.5.2, status=bounced (host sm01.myisp.com[x.x.x.x] said: 504 5.5.2 <contact@localhost>: Sender address rejected: need fully-qualified address (in reply to RCPT TO command))

The question is, how can postfix be persuaded to use the domain name instead of localhost?

Thanks in advance for any advice.

---

### Post by mailalot on 2012-07-15
I ended up adding the following to /etc/postfix/main.cf

myorigin = /etc/mailname
mydomain = mydomain.com

/etc/mailname also contains mydomain.com

[URL="http://serverfault.com/questions/407865/how-to-fix-postfix-sender-address-rejected-need-fully-qualified-address-in-re"]Here's a little bit more detailed information:
[/URL][http://serverfault.com/questions/407865/how-to-fix-postfix-sender-address-rejected-need-fully-qualified-address-in-re](http://serverfault.com/questions/407865/how-to-fix-postfix-sender-address-rejected-need-fully-qualified-address-in-re)

---

