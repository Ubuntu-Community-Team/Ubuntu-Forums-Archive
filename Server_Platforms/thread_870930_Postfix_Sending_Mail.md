---
title: "Postfix Sending Mail"
date: 2008-07-26
forum: Server Platforms
---

### Post by Black Mage on 2008-07-26
In postfix, when I send an email, instead of the domain name 'myname@mydomain.com' it sends the whole server address: 'myname@myserver.mydomain.com'. How can I modify Postfix so it just sends 'myname@mydomain.com' ?

Btw, I am using squirrelmal to send the mail...

---

### Post by pdwerryhouse on 2008-07-27
Try adding this to your /etc/postfix/main.cf file:

```
myorigin = $mydomain
```

---

