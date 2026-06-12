---
title: "can the LVM encryption passphrase be changed?"
date: 2012-06-25
forum: Security
---

### Post by stupidquestion on 2012-06-25
Just curious!

---

### Post by Cheesemill on 2012-06-26
Yes. For more information see:
```
man cryptsetup
```

I think the option you need would be:
```
cryptsetup luksChangeKey /dev/sd?
```

---

