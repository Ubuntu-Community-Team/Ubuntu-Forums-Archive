---
title: "my vhost with 10.04"
date: 2010-05-02
forum: Server Platforms
---

### Post by Vegan on 2010-05-02
```
DocumentRoot "/www/developer"
ServerName contract-developer.tk
ServerAlias www.contract-developer.tk
<Directory "/www/developer">
	allow from all
	Options +Indexes
</Directory>
```

Any mistakes?

---

### Post by zemon_ on 2010-05-02
Is your web directory root not /var/www

---

### Post by Vegan on 2010-05-02
I moved it to /www and changed the default document to there as well

I am using this folder structure as a simple way to manage a few sites I develop.

---

### Post by Ryan Dwyer on 2010-05-02
It looks fine. Are you having problems?

---

### Post by Vegan on 2010-05-04
I was having some errors, seems to be all fixed now

seems I was attempting to upgrade to samba4 that was the problem

---

