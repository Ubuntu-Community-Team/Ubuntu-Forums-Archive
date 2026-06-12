---
title: "Changing ServerTokens with no effect"
date: 2010-02-07
forum: Server Platforms
---

### Post by Znarkus on 2010-02-07
Hi!

In Ubuntu 9.10 I can't get apache directive ServerTokens to work. My httpd.conf looks like below.

```
ServerName server.mydomain.com
ServerSignature Off
ServerTokens Prod
```

ServerName solved startup warnings, but ServerTokens doesn't take. Both Firebug and nmap reports "Apache/2.2.12 (Ubuntu)"

Could someone also tell my how to globally turn off indexes? :)
**Edit:** Solved the second problem, but still need help with the main problem.

---

### Post by gavinj44 on 2010-03-17
bump!

---

### Post by dudumomo on 2010-03-17
You can use the /etc/apache2/conf.d/security file.
And modify these value in it.

---

