---
title: "dovecot and postfix errors"
date: 2015-09-21
forum: Server Platforms
---

### Post by andrew264 on 2015-09-21
Hello all!

I am somewhat new to Linux/Ubuntu, and I'm trying to set up a mail server on a hosted Virtual Personal Server through LithiumHosting.com
I followed the instructions at arstechnica.com for how to do this (at [http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/](http://arstechnica.com/information-technology/2014/03/taking-e-mail-back-part-2-arming-your-server-with-postfix-dovecot/))
I have my VPS running Ubuntu 12.04 LTS x86_64 Minimal, with Dovecot for IMAP, Postfix for SMTP, along with SpamAssassin, ClamAV, and Sieve.

After completing parts 1-3 of the instructions, I am not able to log onto my mail accounts using Thunderbird or Apple Mail.  Filezilla and TightVNC both connect to the server fine though.

I am able to send mail to my personal (gmail) account using the sendmail command, but I cannot log onto my user accounts and I can't seem to find the test mail that I've sent to my user accounts.  I believe I have Postfix and/or Dovecot configured incorrectly.

I believe I have the relevant ports unblocked in ufw.

When checking mail.log, I see the following:
```
Sep 21 20:54:14 mail postfix/smtpd[2471]: connect from (my IP)
Sep 21 20:54:14 mail postfix/smtpd[2471]: warning: connect to Milter service unix:/spamass/spamass.sock: No such file or directory
Sep 21 20:54:14 mail postfix/smtpd[2471]: warning: connect to Milter service unix:/clamav/clamav-milter.ctl: No such file or directory
Sep 21 20:54:14 mail postfix/smtpd[2471]: warning: connect to Milter service unix:/opendkim/opendkim.sock: No such file or directory
Sep 21 20:54:14 mail postfix/smtpd[2471]: lost connection after CONNECT from (my IP)
Sep 21 20:54:14 mail postfix/smtpd[2471]: disconnect from (my IP)

Sep 21 20:54:14 mail postfix/smtpd[2475]: warning: cannot get RSA private key from file /etc/ssl/private/ssl-key-decrypted-mail-blyouprint.key: disabling TLS support
Sep 21 20:54:14 mail postfix/smtpd[2475]: warning: TLS library problem: 2475:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:331:


Sep 21 20:52:32 mail dovecot: imap-login: Fatal: Can't load private ssl_key: Key is for a different cert than ssl_cert
Sep 21 20:52:32 mail dovecot: master: Error: service(imap-login): command startup failed, throttling for 2 secs
```

Any suggestions or help would be appreciated.  Thanks so much! ):P

---

