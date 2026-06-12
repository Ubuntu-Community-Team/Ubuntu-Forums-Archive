---
title: "Evolution unable to login mail server"
date: 2008-11-17
forum: Server Platforms
---

### Post by satimis on 2008-11-17
Hi folks,


I'm following;
[http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html)

to build a mail server running postfix virtual.  The server is now running able to send and receive mails.  But remote mail client 'Evolution' can't login the server to send/receive mails.


# tail /var/log/mail.log```

Nov 17 09:00:32 xen05 postfix/smtpd[6601]: warning: xen0.satimis.com[192.168.0.110]: SASL PLAIN authentication failed: authentication failure
Nov 17 09:00:48 xen05 postfix/smtpd[6601]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Nov 17 09:00:48 xen05 last message repeated 3 times
Nov 17 09:00:48 xen05 postfix/smtpd[6601]: warning: SASL authentication failure: Password verification failed
Nov 17 09:00:48 xen05 postfix/smtpd[6601]: warning: xen0.satimis.com[192.168.0.110]: SASL PLAIN authentication failed: authentication failure
Nov 17 09:00:54 xen05 postfix/smtpd[6601]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Nov 17 09:00:54 xen05 last message repeated 3 times
Nov 17 09:00:54 xen05 postfix/smtpd[6601]: warning: SASL authentication failure: Password verification failed
Nov 17 09:00:54 xen05 postfix/smtpd[6601]: warning: xen0.satimis.com[192.168.0.110]: SASL PLAIN authentication failed: authentication failure
Nov 17 09:01:03 xen05 postfix/smtpd[6601]: disconnect from xen0.satimis.com[192.168.0.110]
```


# grep smtpd_sasl_path /etc/postfix/main.cf```

smtpd_sasl_path = /etc/postfix/sasl;/usr/lib/sasl2

```


# grep pwcheck_method
/etc/postfix/sasl/smtpd.conf ```

pwcheck_method: auxprop

```


# find / name sasldb2 | grep sasldb```

/usr/lib/sasl2/libsasldb.la
/usr/lib/sasl2/libsasldb.a
/usr/lib/sasl2/libsasldb.so.2.0.22
/usr/lib/sasl2/libsasldb.so
/usr/lib/sasl2/libsasldb.so.2


# ls -al /usr/lib/sasl2/libsasldb.so
lrwxrwxrwx 1 root root 19 2008-11-07 10:03 /usr/lib/sasl2/libsasldb.so -> libsasldb.so.2.0.22

```


# ls -al /usr/lib/sasl2/libsasldb.so.2```

lrwxrwxrwx 1 root root 19 2008-11-07 10:03 /usr/lib/sasl2/libsasldb.so.2 -> libsasldb.so.2.0.22

```


# ls -al /usr/lib/sasl2/libsasldb.so.2.0.22```

-rw-r--r-- 1 root root 17980 2006-12-13 21:26 /usr/lib/sasl2/libsasldb.so.2.0.22

```


If changing the line as "smtpd_sasl_path = smtpd"

Still can't login


# tail /var/log/mail.log```

Nov 17 09:42:12 xen05 postfix/postfix-script: refreshing the Postfix mail system
Nov 17 09:42:12 xen05 postfix/master[2771]: reload configuration /etc/postfix
Nov 17 09:42:47 xen05 postfix/smtpd[7231]: connect from xen0.satimis.com[192.168.0.110]
Nov 17 09:42:55 xen05 postfix/smtpd[7231]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Nov 17 09:42:55 xen05 postfix/smtpd[7231]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Nov 17 09:42:55 xen05 postfix/smtpd[7231]: warning: xen0.satimis.com[192.168.0.110]: SASL LOGIN authentication failed: authentication failure
Nov 17 09:43:01 xen05 postfix/smtpd[7231]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Nov 17 09:43:01 xen05 last message repeated 3 times
Nov 17 09:43:01 xen05 postfix/smtpd[7231]: warning: xen0.satimis.com[192.168.0.110]: SASL LOGIN authentication failed: authentication failure
Nov 17 09:43:02 xen05 postfix/smtpd[7231]: disconnect from xen0.satimis.com[192.168.0.110]

```


Still fail.  "login authentication" and "plain authentication" same result.


Please help.  TIA


B.R
satimis

---

