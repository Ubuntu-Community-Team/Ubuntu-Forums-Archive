---
title: "*buntu 64 bit = gimp 64 bit ?"
date: 2011-05-07
forum: Ubuntu Studio
---

### Post by iahim on 2011-05-07
Hello,

Just a silly question :
If I install 64 bit version of Ubuntu Studio (or other 64 bit *buntu like edubuntu) does it mean I'll have the 64 bit verion of gimp installed ?
How can one tell if an installed gimp is 32 bit or 64 bit ? 

Have a nice day.

---

### Post by squaregoldfish on 2011-05-07
Yes, the Gimp will be a 64-bit version.

You can check any executable with the file command:

```
> file /usr/bin/gimp-2.6
/usr/bin/gimp-2.6: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

---

### Post by iahim on 2011-05-08
Thanks !

---

