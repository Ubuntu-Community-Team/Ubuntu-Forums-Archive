---
title: "How to create and mount a file-based encrypted volume?"
date: 2008-07-09
forum: Security
---

### Post by dsplabs on 2008-07-09
Is is possible to create a file-based encrypted volume with dm_crypt/luks?

i.e. I want to create a file and format it as an encrypted filesystem, then I want to mount it... like f.e. you would mount a cd image:

```
mount -o loop cd_image.iso /mnt/iso
```

---

### Post by HalPomeranz on 2008-07-09
Frankly, I'm not sure if you can do it with dm_crypt, but you can do it with Truecrypt, which is available in the repositories ("sudo apt-get install truecrypt").  See the Truecrypt docs at [www.truecrypt.org/docs](www.truecrypt.org/docs).

---

### Post by Gamma746 on 2008-07-09
Check out [http://forums.gentoo.org/viewtopic-t-163762-start-0.html?sid=ed7ffc3fac81d63d4f7537730a82e948](http://forums.gentoo.org/viewtopic-t-163762-start-0.html?sid=ed7ffc3fac81d63d4f7537730a82e948).  It's written for Gentoo, so the procedure that you should use will be slightly different.  (For one, you can ignore the kernel config stuff.)

---

