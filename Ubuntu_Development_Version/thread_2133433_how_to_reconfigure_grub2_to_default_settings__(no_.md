---
title: "how to reconfigure grub2 to default settings ? (no wait before boot)"
date: 2013-04-08
forum: Ubuntu Development Version
---

### Post by Andre-D on 2013-04-08
Somehow my 13.04 installation would not boot, so I fixed grub2 using an automated bootfix cd. 
now it boots fine, but wait for 4 sec each time,

I'd like to reset the grub2 to the default ubuntu settings, and since ubuntu is the only OS choice, it should just boot instantly.

---

### Post by zika on 2013-04-08
Edit /etc/default/grub and change```
GRUB_TIMEOUT=4
``` to```
GRUB_TIMEOUT=0
```
After that do```
sudo update-grub
```If You need check also```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
```in the same file...
Beware: Putting 0 as above in first part of my message might be a bad decision since You might mave problem once You need to choose another kernel or such...

---

### Post by Andre-D on 2013-04-08
Thank you - SSH'ed home, and discovered that "GRUB_HIDDEN_TIMEOUT=0" was commented out.
It's probaply the reason to why it waited for the default 10sec every time.
Will know for sure at next reboot.

Thanks.

---

