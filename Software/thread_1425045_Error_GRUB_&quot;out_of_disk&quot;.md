---
title: "Error GRUB &quot;out of disk&quot;"
date: 2010-03-08
forum: Software
---

### Post by lucasX on 2010-03-08
Hola a todos.
Acabo de instalar Ubuntu 9.10 en mi pc, en la cual ya tenia instalado WindowsXP.
Al terminar la instalación de Ubuntu, reinició la maquina y al momento de bootear me muestra lo siguiente:
[I]GRUB loading.
error: out of disk
grub rescue>[/I]

No se como solucionarlo. Pensé que tal vez tenía que recuperar el GRUB pero no, hice la recuperación y sigo con el mismo problema.

Espero que alguien pueda darme una mano.

Saludos!!

---

### Post by oldfred on 2010-03-08
Sorry, High school French 40 years ago is my only other language and the way I am butchering english in my posts I may not know English.

Wubi??

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by guillermolisi on 2010-03-08
> **lucasX said:**
> Hola a todos.
Acabo de instalar Ubuntu 9.10 en mi pc, en la cual ya tenia instalado WindowsXP.
Al terminar la instalación de Ubuntu, reinició la maquina y al momento de bootear me muestra lo siguiente:
[I]GRUB loading.
error: out of disk
grub rescue>[/I]

No se como solucionarlo. Pensé que tal vez tenía que recuperar el GRUB pero no, hice la recuperación y sigo con el mismo problema.

Espero que alguien pueda darme una mano.

Saludos!!
La instalacion es Dual Boot o via Wubi ?
Si es Dual Boot (Windows en una particion del disco y Ubuntu en otra diferente), podrias pasarnos la informacion que te brinda fdisk sobre las particiones y sus tamaños ?

Cuando reiniciaste la maquina, elegiste con que sistema operativo o inicio directamente en Ubuntu ?

Estas con poco lugar libre en el disco por eso el mensaje *error: out of disk.*

---

