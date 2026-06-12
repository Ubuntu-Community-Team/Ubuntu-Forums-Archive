---
title: "Postfix via ISP relay host Relay denied"
date: 2009-03-03
forum: Server Platforms
---

### Post by Volpesce on 2009-03-03
For ease of use I send all my outbound emails from my mail server via my ISP as a smart host. I have a working set up with sendmail that work already for years.
Now I want to migrate to a newer sever, and want to use postfix.

I am able to receive email to my own domain name.
Internal mails are dealt with correctly, and even mails which are send to recipients of the same ISP I use as a relay host are send.

However, if I want to send an Email to e.g. my work Email the email is bounced by my ISP with the following log entry..

> to=<name@other.isp>, relay=mail.my.isp[xx.xxx.x.xxx]:25, delay=0.16, delays=0.06/0.01/0.02/0.08, dsn=5.7.1, status=bounced (host mail.my.isp[xx.xxx.x.xxx] said: 554 5.7.1 <name@other.isp>: Relay access denied (in reply to RCPT TO command))

Sendmail has no issue's and is working fine.

What am I doing wrong with my postfix configuration.

```
postconf -n
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = $myhostname localhost.$mydomain localhost $mydomain
myhostname = host.own.domain
mynetworks = 127.0.0.0/8, 192.168.xx.0/24
myorigin = $mydomain
notify_classes = resource, software
proxy_interfaces = 192.168.xx.xx
recipient_delimiter = +
relay_domains = $mydestination
relayhost = [mail.my.isp]
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = 

```

Anyone any ideas.

---

