---
title: "Where to put a P7B certificate for all my programs?"
date: 2016-10-06
forum: Security
---

### Post by azzamite on 2016-10-06
Hello guys

I imported the certificate this way:
```
certutil -d sql:/home/me/.pki/nssdb/ -A -t TC -n thisone.p7b -i thisone.p7b
```

But after that, only Chrome is recognizing it, neither Firefox nor wget will use it, so I suspect plenty of other stuff that may require it will fail too.

What's the appropriate way of importing it?

Do I need to add some environment variable maybe?

---

