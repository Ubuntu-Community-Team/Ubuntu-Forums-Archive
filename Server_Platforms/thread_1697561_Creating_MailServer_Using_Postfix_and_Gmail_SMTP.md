---
title: "Creating MailServer Using Postfix and Gmail SMTP"
date: 2011-03-01
forum: Server Platforms
---

### Post by CoffeyLover on 2011-03-01
Hi there everyone,

So I recently created a webserver to host my website, using a Ubuntu 8.10 based system. (With some help from my experienced brother of course).

I now want to create a mailserver to go along with my website. In setting up postfix to work with gmail smtp servers, I ran into a lot of permission errors. When viewing my "mail.log file, I receive the following:

```
blake@GUServer:~$ cat /var/log/mail.log | tail
Feb 28 21:21:54 GUServer postfix/postmap[1510]: fatal: open database /etc/postfix/transport.db: Permission denied
Feb 28 21:22:31 GUServer postfix/master[1653]: fatal: bind 0.0.0.0 port 25: Address already in use
Feb 28 21:23:32 GUServer postfix/postdrop[1660]: warning: unable to look up public/pickup: No such file or directory
Feb 28 21:33:24 GUServer postfix/postmap[1726]: fatal: open sasl_passwd: No such file or directory
Feb 28 21:33:29 GUServer postfix/postmap[1727]: fatal: open sasl_password: No such file or directory
Feb 28 21:33:47 GUServer postfix/postmap[1728]: fatal: open /etc/postfix/sasl_password: No such file or directory
Feb 28 21:34:06 GUServer postfix/postfix-script[1732]: fatal: the Postfix mail system is not running
Feb 28 21:34:12 GUServer postfix/postfix-script[1809]: starting the Postfix mail system
Feb 28 21:34:12 GUServer postfix/master[1810]: fatal: bind 0.0.0.0 port 25: Address already in use
Feb 28 21:39:56 GUServer postfix/postdrop[1911]: warning: unable to look up public/pickup: No such file or directory

```

Does anyone have any suggestions??

Thanks!

---

### Post by HermanAB on 2011-03-01
Howdy,

You basically have two options:
1. Go to the Postfix project web site and start reading, then go to the Apache web site and continue reading, then go to the Roundcube website and read some more, then go to the Dovecot website...
2. Go to the Citadel website and install a complete mail system using the Easy Install script in about 20 minutes.

Postfix is a great way to learn how a mail server works, but I gave up with it years ago, since I have better things to do with my time.

---

### Post by dipeshmehta on 2011-03-01
> **CoffeyLover said:**
> I now want to create a mailserver to go along with my website. In setting up postfix to work with gmail smtp servers

You may check [http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10) and follow required steps only as you already have configured apache. You may also try to set it up from the scratch.

To relay your mails through gmail smtp, please check [http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)

Hope this helps.

---

