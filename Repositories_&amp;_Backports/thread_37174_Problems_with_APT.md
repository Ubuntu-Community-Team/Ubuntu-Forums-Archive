---
title: "Problems with APT"
date: 2005-05-26
forum: Repositories &amp; Backports
---

### Post by zaxer on 2005-05-26
Hi guys.

I got this problem whenever I try sudo apt-get install

```

xx@xx:~$ sudo apt-get install wine
Leyendo lista de paquetes... Hecho
// Reading packs list... Done
E: Error de lectura - read (21 Es un directorio)
// E: Reading Error - read (21 is a folder)

```

Can you help me? I cant update and/or install anything :(

Thanks guys.

---

### Post by stevenyu on 2005-05-26
Look like your apt source file might be corrupted, try remove them from /etc/apt/

and use **apt-get setup** to make a fresh one

---

### Post by jeremy on 2005-05-27
Post your /etc/apt/sources.list here and we can see if that is the problem.

---

