---
title: "Postfix, Dovecot, Sasl and MySQL"
date: 2007-07-03
forum: Server Platforms
---

### Post by Verifier on 2007-07-03
I've followed the following guides:
[http://www.ubuntu-forums.org/showthread.php?t=398866](http://www.ubuntu-forums.org/showthread.php?t=398866)
[http://adomas.org/2006/08/postfix-dovecot/](http://adomas.org/2006/08/postfix-dovecot/)

I can't login into SMTP.  I tested by doing this:
```

root@www:/etc/dovecot# perl -MMIME::Base64 -e 'print encode_base64("jonas\0jonas\0MYSECRETPASSWORD");'
am9uYXMAam9uYXMAc25tZHNoa2gx
root@www:/etc/dovecot# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.mydomain.se ESMTP Postfix (Ubuntu)
auth plain am9uYXMAam9uYXMAc25tZHNoa2gx
535 Error: authentication failed

```

I've also tried to use thunderbird (using "Use TLS where available" checkbox).Didnt work either.

From postfix warn log:
```

e
Jul  3 17:31:50 www postfix/smtpd[7063]: warning: SASL authentication failure: Password verification failed
Jul  3 17:31:50 www postfix/smtpd[7063]: warning: localhost[127.0.0.1]: SASL plain authentication failed

```

Should the passwords be plaintext in the mysql table? Or md5 encoded or something like that?
Got any hints? :p

---

