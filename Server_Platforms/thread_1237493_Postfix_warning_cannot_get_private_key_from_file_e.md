---
title: "Postfix: warning: cannot get private key from file /etc/postfix/FOO-key.pem"
date: 2009-08-11
forum: Server Platforms
---

### Post by umaxtu on 2009-08-11
I'm running my own ubuntu server with LAMP and since I'm running wordpress on it I wanted to be able to send mail so users could register and such.

I'm using Google Apps for my email so I followed [this]("http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html") tutorial. Which would work allright except when sending to a yahoo email address(which is the most popular email service isn't it?) so i dug into the logs and I found the following 
```
Aug 11 10:22:56 l2fserve postfix/pickup[28778]: 958E12034: uid=33 from=<www-data>
Aug 11 10:22:56 l2fserve postfix/cleanup[29179]: 958E12034: message-id=<778b9fe62c84306250b5962829574d7b@links-2-fun.com>
Aug 11 10:22:57 l2fserve postfix/pickup[28778]: 0B7752032: uid=33 from=<www-data>
Aug 11 10:22:57 l2fserve postfix/cleanup[29179]: 0B7752032: message-id=<3edc8ed4ce1e38fb555423a72d8f8db5@links-2-fun.com>
Aug 11 10:22:57 l2fserve postfix/qmgr[27767]: 0B7752032: from=<www-data@links-2-fun.com>, size=582, nrcpt=1 (queue active)
Aug 11 10:22:57 l2fserve postfix/qmgr[27767]: 958E12034: from=<www-data@links-2-fun.com>, size=604, nrcpt=1 (queue active)
Aug 11 10:22:57 l2fserve postfix/smtp[29185]: warning: database /etc/postfix/sasl_passwd.db is older than source file /etc/postfix/sasl_passwd
Aug 11 10:22:57 l2fserve postfix/smtp[29185]: warning: cannot get private key from file /etc/postfix/FOO-key.pem
Aug 11 10:22:57 l2fserve postfix/smtp[29185]: warning: TLS library problem: 29185:error:0B080074:x509 certificate routines:X509_check_private_key:key values $
Aug 11 10:22:57 l2fserve postfix/smtp[29185]: cannot load RSA certificate and key data
Aug 11 10:22:57 l2fserve postfix/smtp[29186]: warning: database /etc/postfix/sasl_passwd.db is older than source file /etc/postfix/sasl_passwd
Aug 11 10:22:57 l2fserve postfix/smtp[29186]: warning: cannot get private key from file /etc/postfix/FOO-key.pem
Aug 11 10:22:57 l2fserve postfix/smtp[29186]: warning: TLS library problem: 29186:error:0B080074:x509 certificate routines:X509_check_private_key:key values $
Aug 11 10:22:57 l2fserve postfix/smtp[29186]: cannot load RSA certificate and key data
Aug 11 10:22:58 l2fserve postfix/smtp[29186]: 958E12034: to=<mxpaluska@links-2-fun.com>, relay=smtp.gmail.com[209.85.201.111]:587, delay=2.3, delays=0.98/0.3$
Aug 11 10:23:06 l2fserve postfix/smtp[29185]: 0B7752032: to=<mxpaluska@yahoo.com>, relay=a.mx.mail.yahoo.com[67.195.168.31]:25, delay=9.5, delays=0.71/0.41/7$
Aug 11 10:23:06 l2fserve postfix/qmgr[27767]: 0B7752032: removed
Aug 11 10:27:58 l2fserve postfix/smtp[29186]: 958E12034: conversation with smtp.gmail.com[209.85.201.111] timed out while sending RCPT TO
Aug 11 10:27:58 l2fserve postfix/cleanup[29189]: CF4D22032: message-id=<20090811142758.CF4D22032@l2fserve>
Aug 11 10:27:59 l2fserve postfix/qmgr[27767]: CF4D22032: from=<>, size=2500, nrcpt=1 (queue active)
Aug 11 10:27:59 l2fserve postfix/bounce[29188]: 958E12034: sender non-delivery notification: CF4D22032
Aug 11 10:27:59 l2fserve postfix/qmgr[27767]: 958E12034: removed
Aug 11 10:28:00 l2fserve postfix/smtp[29186]: CF4D22032: to=<www-data@links-2-fun.com>, relay=smtp.gmail.com[209.85.201.111]:587, delay=1.1, delays=0.2/0/0.7$
Aug 11 10:33:00 l2fserve postfix/smtp[29186]: CF4D22032: conversation with smtp.gmail.com[209.85.201.111] timed out while sending RCPT TO
Aug 11 10:33:00 l2fserve postfix/qmgr[27767]: CF4D22032: removed
Aug 11 12:07:50 l2fserve postfix/pickup[29677]: AF2722033: uid=33 from=<www-data>
Aug 11 12:07:50 l2fserve postfix/cleanup[30140]: AF2722033: message-id=<ff5a6cd4c6c5d259229444ce9a3bcebf@links-2-fun.com>
Aug 11 12:07:50 l2fserve postfix/qmgr[27767]: AF2722033: from=<www-data@links-2-fun.com>, size=610, nrcpt=1 (queue active)
Aug 11 12:07:50 l2fserve postfix/pickup[29677]: E1E922032: uid=33 from=<www-data>
Aug 11 12:07:50 l2fserve postfix/cleanup[30140]: E1E922032: message-id=<313ada057ed201065048db403c718dc5@links-2-fun.com>
Aug 11 12:07:51 l2fserve postfix/smtp[30145]: warning: database /etc/postfix/sasl_passwd.db is older than source file /etc/postfix/sasl_passwd
Aug 11 12:07:51 l2fserve postfix/smtp[30145]: warning: cannot get private key from file /etc/postfix/FOO-key.pem
Aug 11 12:07:51 l2fserve postfix/smtp[30145]: warning: TLS library problem: 30145:error:0B080074:x509 certificate routines:X509_check_private_key:key values $
Aug 11 12:07:51 l2fserve postfix/smtp[30145]: cannot load RSA certificate and key data
Aug 11 12:07:51 l2fserve postfix/qmgr[27767]: E1E922032: from=<www-data@links-2-fun.com>, size=588, nrcpt=1 (queue active)
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: warning: database /etc/postfix/sasl_passwd.db is older than source file /etc/postfix/sasl_passwd
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: warning: cannot get private key from file /etc/postfix/FOO-key.pem
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: warning: TLS library problem: 30146:error:0B080074:x509 certificate routines:X509_check_private_key:key values $
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: cannot load RSA certificate and key data
Aug 11 12:07:52 l2fserve postfix/smtp[30145]: AF2722033: to=<mxpaluska@links-2-fun.com>, relay=smtp.gmail.com[209.85.201.111]:587, delay=1.4, delays=0.34/0.1$
Aug 11 12:07:55 l2fserve postfix/smtp[30146]: E1E922032: to=<maxp.upe@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.147.27]:25, delay=4.4, delays=0.38/$
Aug 11 12:07:55 l2fserve postfix/qmgr[27767]: E1E922032: removed

```

the part that personally concerns me the most is this part
```
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: warning: database /etc/postfix/sasl_passwd.db is older than source file /etc/postfix/sasl_passwd
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: warning: cannot get private key from file /etc/postfix/FOO-key.pem
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: warning: TLS library problem: 30146:error:0B080074:x509 certificate routines:X509_check_private_key:key values $
Aug 11 12:07:51 l2fserve postfix/smtp[30146]: cannot load RSA certificate and key data
```

Can anyone help me?

---

### Post by shoutbox on 2011-08-05
I'm having the same issue but without external database...

I also ran into a bug but lost the id:number.

Tried to compile the latest openssl but found out my lack of competence to do that. So I failed pack to apt-get -version 0.9.8o Jun 2010.

Wish I could update the openssl and see if this problem goes away.

All functions but client auth work marvelleously :P

(EDIT)
I've found too set's of instructions to use to name a key file. One to assign .key and another to assign .pem...I've tried both and stick with the .key file for now.

---

