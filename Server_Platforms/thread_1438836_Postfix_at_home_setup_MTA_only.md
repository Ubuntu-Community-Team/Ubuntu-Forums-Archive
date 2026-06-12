---
title: "Postfix at home setup MTA only"
date: 2010-03-25
forum: Server Platforms
---

### Post by machine111 on 2010-03-25
Hi, I am new to the forum.
 
I have a problem setting up Postfix on my home (behind Router/firewall)  Ubuntu driven server, I have been trying for days now with no luck.
 
All I would like to do is use the ***server to send mail (MTA)***.  So while installing I configured it as a ***satellite system***.  
 
 
 **file:**
 
/etc/postfix/main.cf
 
[B]settings:
 [/B]
myhostname = mail.example.com
mydomain = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = $myhostname,localhost.$mydomain,localhost
relay_domains = $mydestination
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
relayhost = [smtp.broadband.rogers.com] 
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = has:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
 
 **created the sasl_passwd file:**
 
smtp.broadband.rogers.com username : password
 
 
 I have registered to my ISP account.

 **command: **
 
telnet 127.0.0.1 25
 
 [B]output: 
 [/B]
Connected to 127.0.0.1.
Escape character is '^]'.
220 mail.example.com ESMTP Postfix (Ubuntu)
 
 [B]
here is log after committing send:

[/B] Mar 25 13:49:01 mail postfix/pickup[23137]: 7F7F65C6DA: uid=1000 from=<user>
Mar 25 13:49:01 mail postfix/cleanup[23143]: 7F7F65C6DA: message-id=<20110345174901.7F7C65C6DA@mail.example.com>
Mar 25 13:49:01 mail postfix/qmgr[23138]: 7F7F65C6DA: from=<user@mail.example.com>, size=311, nrcpt=1 (queue active)
Mar 25 13:49:02 mail postfix/smtp[23145]: 7F7F65C6DA: to=<me@gmail.com>, relay=smtp.broadband.rogers.com[206.190.36.18]:25, delay=0.72, delays=0.35/0.08/0.26/0.03, dsn=5.0.0, status=bounced (host smtp.broadband.rogers.com[206.190.36.18] said: **553 From address not verified** - see [http://www.rogershelp.com/verify-email](http://www.rogershelp.com/verify-email) (in reply to MAIL FROM command))
Mar 25 13:49:02 mail postfix/cleanup[23143]: 2B56C6C6DC: message-id=<20100325174902.2B56C5C6DC@mail.example.com>
Mar 25 13:49:02 mail postfix/qmgr[23138]: 2B56C5F6DC: from=<>, size=2295, nrcpt=1 (queue active)
Mar 25 13:49:02 mail postfix/bounce[23146]: 7F7F75C6DA: sender non-delivery notification: 2B56C5C6CC
Mar 25 13:49:02 mail postfix/qmgr[23138]: 7F7F65C6DA: removed
Mar 25 13:49:02 mail postfix/local[23147]: 2B56C5C6DC: to=<user@mail.example.com>, relay=local, delay=0.63, delays=0.13/0.16/0/0.34, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 25 13:49:02 mail postfix/qmgr[23138]: 2B56C5C6DC: removed


I'm getting a **553 From address not verified**. I have tried what it suggested from the URL link, but it still doesn't work.

Any suggestions or pointers?

Help is appreciated!

---

### Post by KB1JWQ on 2010-03-25
Rogers has a weird thing about this.  You're SURE you've added [email]user@mail.example.com[/email] to their approval list?

Unfortunately it's not (directly) a postfix issue. :-/

---

### Post by machine111 on 2010-03-25
> **KB1JWQ said:**
> Rogers has a weird thing about this.  You're SURE you've added [EMAIL="user@mail.example.com"]user@mail.example.com[/EMAIL] to their approval list?

Unfortunately it's not (directly) a postfix issue. :-/

Thanks for the reply.
 
What I did was followed the steps outlined here: [http://www.rogershelp.com/yahoo/article.php?id=10H-F](http://www.rogershelp.com/yahoo/article.php?id=10H-F)

I assume this is what you are referring too to verify it.

It seems I need to put [EMAIL="user@mail.example.com"]user@mail.example.com[/EMAIL] for the e-mail field, I will not be able to get the verification code since I have not setup an MDA.

Any suggestions?

Thanks in advance.

---

### Post by KB1JWQ on 2010-03-25
Use another smarthost that'll accept traffic on port 587 (Rogers shouldn't touch this port)?  

Or set up an MDA to verify that email address.

---

