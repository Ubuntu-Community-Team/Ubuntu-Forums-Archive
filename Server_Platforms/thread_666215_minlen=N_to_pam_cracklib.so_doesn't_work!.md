---
title: "minlen=N to pam_cracklib.so doesn't work!?"
date: 2008-01-13
forum: Server Platforms
---

### Post by emil.s on 2008-01-13
In my common-password:
```
password required         pam_cracklib.so minlen=11
password required         pam_unix.so use_authtok md5
```

But for some reason the standard value (9) applies. Why!? :confused:

---

### Post by emil.s on 2008-01-14
Now i even tried with one of the examples in the manual:
```
password  required pam_cracklib.so \
               difok=3 minlen=15 dcredit= 2 ocredit=2
password  required pam_unix.so use_authtok nullok md5

```

And with both ways on another machine... But with no success. :(

Can this be a bug? Anyone other who can try?

---

### Post by emil.s on 2008-01-17
*bump* No one!? :(

---

