---
title: "[Apache2] How to remove machine information"
date: 2006-12-15
forum: Server Platforms
---

### Post by tekrei on 2006-12-15
Hello, I want to remove machine information from directory listing page in apache 2. Please look at screen shot. I want to remove or simplify information given in surrounded red area. Thanks for help.

---

### Post by mipedja on 2006-12-15
Hi,
you need to set ServerTokens to prod in your apache2.conf file.

---

### Post by tekrei on 2006-12-17
Thank you very much.

---

### Post by chrisfay on 2006-12-17
You may also want to disable directory browsing so you're files aren't shown like that:

```
Options -Indexes
```

Stick it within a *Directory* tag..

---

