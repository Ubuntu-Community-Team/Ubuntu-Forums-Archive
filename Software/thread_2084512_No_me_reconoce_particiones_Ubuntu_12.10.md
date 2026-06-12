---
title: "No me reconoce particiones Ubuntu 12.10"
date: 2012-11-15
forum: Software
---

### Post by jagmig on 2012-11-15
Ayuda tengo un problema con las particiones, ya que tengo un DD de 600 Gb, pero ya tengo 2 particiones una para windows 8 y otra para archivos, deje una sola particion para el ubuntu, Peeeero al tratar de instalar ubuntu no me reconoce esa particion (por que el win crea otra particion de recuperacion), y me dice que ya son 4, pero la que dejo para ubuntu no me la reconoce por que?? Me sale una SDA1 de 1mb de tamaño y pues esa no se de donde sale y como me marca que ya son 4 no puedo ver la que deje para Ubuntu ya probe con gparted y sigue apareciendo esa de 1mb y kien sabe donde sale. Ayuda porfas.

---

### Post by gmunioz on 2012-11-16
En una sesión live, abre una terminal y ejecuta:
[HTML]sudo su
fdisk -l[/HTML]
copia y pega la salida en el post.

---

