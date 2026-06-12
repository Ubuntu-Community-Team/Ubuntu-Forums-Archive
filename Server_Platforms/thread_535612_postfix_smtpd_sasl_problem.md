---
title: "postfix smtpd sasl problem"
date: 2007-08-26
forum: Server Platforms
---

### Post by Zarnce on 2007-08-26
I am setting up a postfix mail server.  I am unable to send email from an external machine (thunder bird).  Downloading mail through imap works.

Setup:
Postfix
Dovecot
SASL
TLS

When I try and send an email from a box on the network I get this error message in the syslog:
Aug 26 17:23:24 fileserver postfix/smtpd[8858]: fatal: no SASL authentication mechanisms

Has anyone seen this before?  I'm not even sure where to being looking.  I have gone over my config files multiple times and checked them against several howtos.  When I attempt to test by telnet the ack never appears.

Any help would be greatly appreciated.
Thanks
  Zarnce

---

### Post by a9k on 2007-08-27
You might want to read these:
[http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL]("http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL")
[http://www.postfix.org/SASL_README.html#server_dovecot]("http://www.postfix.org/SASL_README.html#server_dovecot")

That message means that while trying to start the fetch of email, the two machines couldn't agree on what security they were going to use.

Usually this is a config problem on the server in the SASL config. There can be problems in config in dovecot, postfix, or sasl.

Check in /etc/default/saslauthd, /etc/postfix/sasl/*, /etc/postfix/main.cf, /etc/dovecot/*

You should set "auth_verbose = yes" in /etc/dovecot/dovecot.conf to get some debug info in the log files.

---

