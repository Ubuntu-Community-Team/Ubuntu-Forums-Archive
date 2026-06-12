---
title: "inetd?"
date: 2012-08-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-23
Quick question: 

Do you guys also have inetd installed? Or did I forget this thing installed while testing some other stuff?

whereis inetd (/usr/sbin/inetd) and ls -lah /etc/inetd.conf to test.

Thanks,
Effenberg

---

### Post by arpanaut on 2012-08-23
```
john@qq-two:~$ whereis inetd
inetd:
john@qq-two:~$ ls -lah /etc/inetd.conf
ls: cannot access /etc/inetd.conf: No such file or directory
john@qq-two:~$ 
```Apparently not?
i386 install.

---

### Post by effenberg0x0 on 2012-08-23
> **arpanaut said:**
> ```
john@qq-two:~$ whereis inetd
inetd:
john@qq-two:~$ ls -lah /etc/inetd.conf
ls: cannot access /etc/inetd.conf: No such file or directory
john@qq-two:~$ 
```Apparently not?
i386 install.

Thanks Arpanaut, I probably got it as a dep of something else.

Regards,
Effenberg

---

