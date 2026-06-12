---
title: "ClamAV question"
date: 2009-09-26
forum: Security
---

### Post by redsky1302 on 2009-09-26
I did a "sudo clamscan -r /" today and clamav reported 1 infected file. How do I check what that file is? I realise that I should have piped the output from clamscan into grep, but is there any log or something I can see if I didn't do so? Thanks!

---

### Post by wojox on 2009-09-26
Run it again:

```
sudo clamscan -r -i /
```

---

