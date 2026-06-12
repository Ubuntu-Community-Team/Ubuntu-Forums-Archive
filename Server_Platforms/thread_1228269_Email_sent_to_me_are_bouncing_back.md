---
title: "Email sent to me are bouncing back"
date: 2009-07-31
forum: Server Platforms
---

### Post by Twizzle on 2009-07-31
My home server downloads my emails from 1and1 via POP3 and then I access them from my server via IMAP. I use fetchmail, postfix and zarafa.

I was recently having problems sending emails after an upgrade,  but could recieve them ok. After a bit of help I changed my main.cf file to this:

```

myhostname = mail.MYSERVER.co.uk
mydomain = MYSERVER.co.uk
myorigin = $mydomain

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smtp_auth
smtp_sasl_security_options = noanonymous
relayhost = auth.smtp.1and1.co.uk

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = thegcs.co.uk, localhost.localdomain, localhost
# allow local network, localhost, and local IPV6 addresses
mynetworks = 192.168.1.0/24 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

mailbox_command = /usr/bin/zarafa-dagent "$USER"

```

Sending emails is working just fine but after a few hours of cyber silence, I checked and found that I can no longer recieve emails.

I tried from a seperate webaccount and it bounced back basically saying that it could not deliver to [email]me@localhost.MYSERVER.co.uk[/email].

I can see from the text that it finds its way to my server ok but then my server is obvioulsy trying to send it on to [email]me@localhost.MYSERVER.co.uk[/email] which bounces.

Is there any way I can fix this?

I was thinking about the aliases file but don't know enough about it at the moment and also think that might be a bit of a round about solution.

---

### Post by fakrulalam on 2009-08-02
Hi, 
The best way of checking SMPT service is to manually telnet port 25, send mail and check the maillog. Could you please also check the MX entry for the domain MYSERVER.co.uk.

---

