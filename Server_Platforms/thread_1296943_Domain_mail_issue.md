---
title: "Domain mail issue"
date: 2009-10-21
forum: Server Platforms
---

### Post by cristiace on 2009-10-21
Hello
   
  I have an issue. I have installed Ubuntu Server 9.04 and after that: Apache, MySQL, postfix, courier [pop/imap] Webmin [+Virtualmin] and Postfix. My main domain it’s PRIMARY_DOMAIN.COM
   
  I managed to configure all of the above and add with Virtualmin new domains to host. 
   
  My problem now is that when I’m adding a new email for a secondary domain the address is created like this: **username.SECONDARY-DOMAIN.EXT@PRIMARY_DOMAIN.COM** instead of **username@SECONDARY-DOMAIN.EXT** – and I didn’t manage to do this. How should I do this? I’m sure I’m doing something wrong, but can’t understand what.
   
  Also, when adding a new email account from command line, I cannot use it in SquirrelMail.
  From command line I’m adding a new user like this:

```
useradd -s /sbin/nologin username
passwd username
```Do any of you have an idea?
   
  Thanks

---

### Post by cristiace on 2009-10-22
No one knows? It's urgent :(


Thanks

---

