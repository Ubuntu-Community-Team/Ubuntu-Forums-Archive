---
title: "Postfix and relaying"
date: 2009-04-15
forum: Server Platforms
---

### Post by tkhobbes on 2009-04-15
Hi all

I finally managed to properly set up postfix - with the help of this doc: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Now - e-mails to the internet are delivered, this is working. however, e-mails to localdomains are not delivered, for some reasons they seem to be relayed to my ISP (at least, I get error messages from their mailserver complaining about "unrouteable addresses"....)

Can someone point me into the right direction?

---

### Post by dipeshmehta on 2009-04-16
Hi...

For local domain, mails do not need to be relayed through ISP.  What is in your /etc/hosts file? and please paste error message from your mail.log

Dipesh

---

### Post by tkhobbes on 2009-04-16
Here's /etc/hosts:

```
127.0.0.1       localhost
127.0.1.1       eee-box.zuhause.own     eee-box
```

and here's part of /var/log/mail.log:

```
Apr 16 18:10:57 eee-box postfix/smtpd[4836]: cannot load Certificate Authority data
Apr 16 18:10:57 eee-box postfix/smtpd[4836]: warning: TLS library problem: 4836:error:02001002:system library:fopen:No such file or directory:bss_file.c:122:fopen('/etc/ssl/cacert.pem','r'):
Apr 16 18:10:57 eee-box postfix/smtpd[4836]: warning: TLS library problem: 4836:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:125:
Apr 16 18:10:57 eee-box postfix/smtpd[4836]: warning: TLS library problem: 4836:error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
Apr 16 18:10:57 eee-box postfix/smtpd[4836]: connect from unknown[10.10.10.101]
Apr 16 18:11:01 eee-box postfix/smtpd[4836]: 18B5B1DC05F: client=unknown[10.10.10.101], sasl_method=PLAIN, sasl_username=thomas
Apr 16 18:11:01 eee-box postfix/cleanup[4840]: 18B5B1DC05F: message-id=<49E75890.7070309@hobbes.ch>
Apr 16 18:11:01 eee-box postfix/qmgr[4565]: 18B5B1DC05F: from=<mail@external.com>, size=535, nrcpt=1 (queue active)
Apr 16 18:11:01 eee-box postfix/smtpd[4836]: disconnect from unknown[10.10.10.101]
Apr 16 18:11:01 eee-box postfix/local[4841]: 18B5B1DC05F: to=<mail@internal.own>, relay=local, delay=0.56, delays=0.45/0.01/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Apr 16 18:11:01 eee-box postfix/qmgr[4565]: 18B5B1DC05F: removed
Apr 16 18:11:01 eee-box dovecot: imap-login: Login: user=<thomas>, method=PLAIN, rip=10.10.10.101, lip=10.10.10.5, TLS
Apr 16 18:11:01 eee-box dovecot: IMAP(thomas): Connection closed bytes=386/49
```

(note: external.com is looked after by my ISP, and internal.own is my own "network")

---

