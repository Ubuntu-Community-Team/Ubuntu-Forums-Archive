---
title: "qpopper broke courier-pop"
date: 2006-10-15
forum: Server Platforms
---

### Post by s3ntinel76 on 2006-10-15
Hi,
sadly I broke my working postfix/courier setup from: [http://flurdy.com/docs/postfix/#conf]("http://flurdy.com/docs/postfix/#conf")

I meant to install fetchmail (which I now have), but accidentally installed qpopper.

I have now run:

```
sudo apt-get remove qpopper
```

but this now leaves the server without pop3.
```

telnet locahost 143
``` indicates no reponse

and 
```

/etc/init.d/courier-pop start
```

returns [OK], but nothing shows in /var/log/mail.log

Any ideas where I should start looking to get courier popping ok?
(incidentally, IMAP works fine...)

---

