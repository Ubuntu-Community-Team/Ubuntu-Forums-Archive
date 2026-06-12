---
title: "force unmount /opt"
date: 2005-10-24
forum: Tutorials
---

### Post by blueberrycheesecake on 2005-10-24
i need to unmount /opt but i keep getting this:

poobah@ds9:~$ sudo umount /opt
umount: /opt: device is busy
umount: /opt: device is busy

so i closed all applications except for the terminal and i still got the same result.

how do i force unmount?

---

### Post by Kyral on 2005-10-24
1) Reccommend that this be moved to one of the Support Forums

2) Is /opt on the same partition as the rest of the / file system? If so then you won't be able to unmount it

---

### Post by blueberrycheesecake on 2005-10-24
thanks kyral!

it's not in the same partition.

i tried to force unmount it again

sudo umount -f /opt

again, it gave me a service is busy reply or something like that :mad: 
i then rebooted it. 
and ... voila! ... /opt is already unmounted after booting.:D 

i don't get it. :confused:

---

### Post by denkedran on 2005-11-07
you could have umount withount rebooting with the following

```
umount -l /opt
man umount (search for lazy)
```

perhaps with a sudo

---

### Post by ajoliveira on 2011-04-21
that -l option was useful for me, thanks!

---

### Post by dodo_ur on 2013-03-13
"umount -l /opt" it works for me

---

