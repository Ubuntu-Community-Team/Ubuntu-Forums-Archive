---
title: "hp deskjet f2210 no show"
date: 2013-06-10
forum: Ubuntu Studio
---

### Post by Acepony on 2013-06-10
I use to be able to plug my printer (hp deskjet f2210) in and just see it on normal ubuntu 12.04. Do I have to do something different on ubuntu studio 13.04? I would like to to know how to fix this problem. Thanks

---

### Post by jejeman on 2013-06-10
Plug it in, and give
```
lsusb
```

---

### Post by Acepony on 2013-06-13
Sorry I took a while I was buisy. Here is the output. It shows up but in the print options of all the programs I use it does not show up as an option to print.
> octavian@octavian-Inspiron-1545:~$ lsusb
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 006 Device 002: ID 03f0:2404 Hewlett-Packard Deskjet F2280 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
octavian@octavian-Inspiron-1545:~$ 



---

### Post by jejeman on 2013-06-13
See on HPLIP list if printer is supported. [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Instal HPLIP, it will setup the printer.

---

### Post by Acepony on 2013-06-13
Thanks. Even the scanner works. That is a real pluss.

---

