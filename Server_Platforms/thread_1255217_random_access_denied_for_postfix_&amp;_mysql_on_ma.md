---
title: "random access denied for postfix &amp; mysql on mailserver"
date: 2009-09-01
forum: Server Platforms
---

### Post by elfstone2 on 2009-09-01
Hello,
I tried to do a mailserver setup according to [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) including postfix, mysql and maildrop.

In 50% of the cases, everything works fine, but in the other 50% of the mails I get, something goes wrong.

```
Sep  1 13:02:14 vserver2400 authdaemond: failed to connect to mysql server (server=localhost, userid=mail.): Access denied for user 'mail.'@'localhost' (using password: YES)
Sep  1 13:02:14 vserver2400 authdaemond: authmysql: TEMPFAIL - no more modules will be tried
```

First I noticed, that the username should be "mail"and not "mail."
In mysqllog i found:

```

49 Connect     Access denied for user 'mail        '@'localhost' (using password: YES)

```


Where does the . or the additional spaces come from? I double checked all configfiles for spaces, there are non. Also, the strange thing is, that it works in approx. 50% of the emails I get.

Any Ideas?
Cheers,
Thomas

---

