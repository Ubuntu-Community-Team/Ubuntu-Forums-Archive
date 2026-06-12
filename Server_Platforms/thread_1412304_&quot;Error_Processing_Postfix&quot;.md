---
title: "&quot;Error Processing Postfix&quot;"
date: 2010-02-21
forum: Server Platforms
---

### Post by thetrevorharmon on 2010-02-21
I've been working on getting postfix installed on a server but can't seem to get it to install. Every time I install postfix I get this error:

```
 Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: skylinebydesign.hsd1.ut.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: skylinebydesign.hsd1.ut.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
You have mail in /var/mail/root

```

I looked at the new mail and it's a log of errors that the system encountered in trying to send a message. Can anybody help me with this problem?

---

