---
title: "IMAP server failed"
date: 2013-02-13
forum: Server Platforms
---

### Post by Elnison on 2013-02-13
hi guys I already did the [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/") guide in setting up mail server. and when I'm logging in roundcube I get the message "Connection to IMAP server failed" 
when I check the /var/log/mail.log here's the message
```
Feb 13 16:02:02 mail authdaemond: Authenticated: clearpasswd=xxxxx, passwd=ytk/mFs6yh9uI
Feb 13 16:02:02 mail imapd-ssl: chdir /var/spool/mail/virtual/elnison/: No such file or directory
Feb 13 16:02:02 mail imapd-ssl: elnison@hmd-c.com: No such file or directory

```

while in /var/log/roundcube/errors i get this message
```
[13-Feb-2013 08:02:01 UTC] PHP Deprecated:  Assigning the return value of new by reference is deprecated in /usr/share/php/MDB2.php on line 393
[13-Feb-2013 08:02:01 UTC] PHP Deprecated:  Assigning the return value of new by reference is deprecated in /usr/share/php/MDB2.php on line 2647
[13-Feb-2013 16:02:02 +0800]: IMAP Error: Login failed for elnison@hmd-c.com from 192.168.0.122. AUTHENTICATE PLAIN:  in /usr/share/roundcube/program/include/rcube_imap.php on line 205 (POST /roundcube/?_task=login&_action=login)

```

do you have any idea what my error is? thanks!

---

### Post by Elnison on 2013-02-13
bump!

---

