---
title: "Ayuda para Ubuntu 10.10 con Raid 0"
date: 2010-10-28
forum: Software
---

### Post by Tenar on 2010-10-28
Hola a Todos 

Tengo configurado un RAID0 donde instale XP en un parte y W7 en otra. Quiero ademas instalar ubuntu 10.10 para tener los tres sistemas operativos

Cuando intente instalarlo desde el LiveCD detecta los discos individualmente, no reconoce el RAID0, ni las particiones, ni los SO instalados

Toda la informacion que voy leyendo hasta ahora en el foro, solo enseña a crear desde el princio el RAID con ubuntu, y hacer las particiones. No encontre informacion de como instalarlo cuando el raid ya esta creado y con windows instalado.

Alguien que pueda ayudarme plis.

Pd: mi mather es Asus Rampage EE II
dos HD WD Serialata II 64gb en RAID0

Saludos

---

### Post by guillermolisi on 2010-10-28
Si bien en Windows creaste el arreglo de discos, Linux no lo vera si no usas dmraid (habilita RAID por software ya que no tenes una controladora inteligente para implementar RAID por hardware)

[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by Tenar on 2010-10-29
Gracias guillermo


conoces algun paso a paso del dmraid? 
esta compleja para mi nivel de linux la data del wiki

---

### Post by gmunioz on 2010-10-29
Lee aqui:

[http://doc.ubuntu-es.org/Instalar_servidor_Ubuntu_8.04_con_RAID_por_software](http://doc.ubuntu-es.org/Instalar_servidor_Ubuntu_8.04_con_RAID_por_software)

---

### Post by Tenar on 2010-10-30
Gracias gabriel

ya habia visto esa pagina, pero me muestra como crear las particiones desde cero. Yo ya las tengo listas y funcionando, pero las cree con windows 7. Deje una particion de las 3 sin formato para instalar linux
Ubuntu no me las detecta. y no quiero borrar todo para crear desde Cero.

salu2

---

### Post by guillermolisi on 2010-10-30
> **Tenar said:**
> Gracias gabriel

ya habia visto esa pagina, pero me muestra como crear las particiones desde cero. Yo ya las tengo listas y funcionando, pero las cree con windows 7. Deje una particion de las 3 sin formato para instalar linux
Ubuntu no me las detecta. y no quiero borrar todo para crear desde Cero.

salu2
El RAID que tenes configurado lo ve solamente Windows. Ubuntu no lo ve sencillamente porque no tiene cargado DMRAID, asi que lo que te paso Gabriel es aplicable porque para Ubuntu ES una instalacion nueva y no afectara, siempre que tengas especial cuidado en la asignacion de las particiones en el RAID para Linux, al RAID de Windows.

---

