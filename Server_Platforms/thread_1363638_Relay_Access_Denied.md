---
title: "Relay Access Denied"
date: 2009-12-24
forum: Server Platforms
---

### Post by Skerit on 2009-12-24
So I followed the basic postfix install (here: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) )

But I can only send mails to the kipdola.info domain, not anywhere else!

This is the error I receive:

RCPT TO <address@kipdola.com> mislukt: <address@kipdola.com>: Relay access denied

---

### Post by kewlrichie on 2009-12-24
Check your mydestination= make sure your domain is in there or you can use $mydomain if you specified that in the /etc/postfix/main.cf file

---

### Post by Skerit on 2009-12-25
My domains were in order (have about 4 of them)

I wa smissing the smtp-authentication part.
All the information was on this wiki article (Authentication section):

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

