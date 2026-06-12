---
title: "[SOLVED] COmo accedo a Ubuntu en Win WUBI"
date: 2008-09-25
forum: Software
---

### Post by zeroadrenaline on 2008-09-25
Che termine todo el proceso de instalacion de Ubuntu, via WUBI, pero ahora no se como hacer para poder tenerlo en una ventanita de win, al menos yo pense que esa era la idea.
Si me pueden decir bien como es el easunto, como se utiliza, me vendria muy bien!.
PAZ!

---

### Post by sajnox on 2008-09-25
Wubi lo que hace es crear una carpeta en la que instala Ubuntu, en esa carpeta crea un disco virtual.

Tampoco usa Grub sino que usa el gestor de arranque de windows.

En resumen te permite tener un dual boot sin tener que usar Grub y sin particionar el disco, pero no es una maquina virtual. Para lo que vos queres tenes que usar programas de maquinas virtuales (Vmware, VirtualBox, etc)

---

