---
title: "Problems with postfix - please take a look"
date: 2012-01-15
forum: Server Platforms
---

### Post by Nailox on 2012-01-15
Hi. On a fresh install VPS with Ubuntu 10.10 Im trying to install a mail server. It has sendmail running by default. I stop it and remove it from /etc/init.d Then I install postfix and two things happen: 

1. When I try "postconf -e 'inet_protocols = all' I get:  IPv6 support is disabled: Address family not supported by protocol

I set it to inet_protocols = ipv4 and the error doesnt show anymore

2. I get this in mail.log ```
postfix/master[3952]: fatal: bind 0.0.0.0 port 25: Address already in use

``` 
I guess its some conflict with sendmail.

In mail.log I also see this ```
postfix/master[5772]: terminating on signal 15

```

When I try to send mail to gmail I get this is mail.log ```
postfix/smtp[5929]: connect to gmail-smtp-in.l.google.com[173.194.69.27]:25: Connection timed out

```

Im using this howto [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Ive used this exact same configuration on another VPS with Ubuntu and everything was working. The only difference I can think of is that on  this VPS (the one with the problems) Sendmail was enabled by default. 

Can you help me with this ? Thanks.

---

