---
title: "TLS Not working"
date: 2016-07-04
forum: Security
---

### Post by silas2 on 2016-07-04
I've got an Ubuntu box running at Rackspace, I have a postfix mailserver which was working fine. I cloned the box but with a new IP and new server name and the postfix stopped accepting remote POP3/SMTP. I realised the certificate had the old server name in, and when I ran checktls.com it said:
```

[COLOR=#363636][FONT=&amp]TLS not available due to local problem [/FONT][/COLOR]
[COLOR=#363636][FONT=&amp]STARTTLS command rejected[/FONT][/COLOR]

```
I don't know for sure it that's causing the  'Relay Access Denied' but it can't be helping.
I remade the certificate with openssl, but I'm still getting the same error from checktls.com, what could I have done wrong in creating my certificate?

---

