---
title: "[SOLVED] i686?"
date: 2008-12-27
forum: The Cafe
---

### Post by pinged on 2008-12-27
I've been wondering what would happen if you typed this in:

```
sudo apt-build upgrade
```

Would it optimize your architecture for i686 or leave it at i386?

Just curious

EDIT:
```

$ uname -a
Linux linux 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686 GNU/Linux

```

EDIT: Does this mean ubuntu is already i686? If so why is it shown as i386???

Thanks for the quick replys

---

### Post by sdennie on 2008-12-27
It would compile your software for a few days and then once it was finished, you would reboot to find that it's no faster.  :)

---

### Post by steveneddy on 2008-12-27
In your terminal please post the output of:

```
uname -a
```

---

