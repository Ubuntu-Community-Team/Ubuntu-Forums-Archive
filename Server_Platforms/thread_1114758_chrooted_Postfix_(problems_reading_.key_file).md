---
title: "chrooted Postfix? (problems reading .key file)"
date: 2009-04-03
forum: Server Platforms
---

### Post by tkhobbes on 2009-04-03
Hi all

I followed the postfix guide here:
[https://help.ubuntu.com/8.10/serverguide/C/postfix.html]("https://help.ubuntu.com/8.10/serverguide/C/postfix.html")

However, Postfix does not seem to be able to read the .key-file, as indicated in /var/log/mail.err:

```
Mar 26 22:40:30 eee-box dovecot: Fatal: imap-login: Can't load private key file /etc/ssl/private/smtpd.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
```

I googled a bit, and stumpled upon this explanation:
[http://archive.netbsd.se/?ml=postfix-users&a=2009-01&t=9711361]("http://archive.netbsd.se/?ml=postfix-users&a=2009-01&t=9711361")
...which again pointed me back to this document:
[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

I think this is the solution; however, looking into /var/spool/postfix, there is no /var directory, so I am not entirely sure whether the set up is correct on my box... I think postfix should run chrooted (at least, master.cf seems to indicate this), and the command
```
dpkg-statoverride --force --update --add root sasl 755 /var/spool/postfix/var/run/saslauthd
```
rails because there is no /var/spool/postfix/var/run7saslauthd.

I am a little confused, as I am not deep enough in the openssl matter - the only thing I want to achieve is having a postfix that
a) delivers mail to local recipients
b) relays all other mail to my ISP's mail server....

Thanks!

---

### Post by tkhobbes on 2009-04-08
*bump* anyone?

---

