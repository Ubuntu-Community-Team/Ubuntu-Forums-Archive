---
title: "Comatibilidad EXT4"
date: 2009-02-17
forum: Software
---

### Post by h9005 on 2009-02-17
Alguien sabe si puede instalarse uii 8.10 con ext4 y si reconoce el grub a este tipo de sistema de archivos?

---

### Post by fmsismo on 2009-02-18
Creo que el soporte en instalación esta recién a partir de la 9.04 (que esta como nuevas características).

Igual no te recomiendo que pongas ext4 en un sistema de producción por ahora o donde tengas datos que consideres de algún valor.

Si bien evolucionó y se considera estable como para dejar de ser expirimental no se cuanta información sobre ex4 o herramientas para solucionar problemas vas a encontrar en caso de que te topes con alguno (problemas).

---

### Post by sdennie on 2009-02-18
Notas de ext4 con Hardy:

- Para usar ext4 con Hardy o Intrepid, tenes que usar el kernel 2.6.28 (que tiene ext4 estable y no ext4dev).  

- El grub de 8.04 y 8.10 no entiende ext4 asi que necesitas una partition /boot ext2 u ext3.

- Hay que compilar y instalar el nuevo e2fsprogs: [ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/e2fsprogs-1.41.4.tar.bz2](ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/e2fsprogs-1.41.4.tar.bz2)

- Hay que poner "ext4" en /etc/initramfs-tools/modules y hacer un "update-initramfs -u" despues de iniciar con el kernel 2.6.28.  

- Hay un bug en Hardy (no se con Intrepid) y no te va a funcionar si no haces el workaround aca: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/309762](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/309762)

- Tenes que cambiar "ext3" a "ext4" y usar la opcion "extents" en /etc/fstab

Y despues de hacer todo eso, lo mas probable es que:

1) La maquina no va a iniciar y no tenes ningun LiveCD que sabe leer ext4 (Y te va a pasar.  Te lo juro.)

o

2) La maquina inicia pero no hay ningun diferencia entre ext3 y ext4.  Para usar ext4 ext4 hay que reformatear las particiones con mke2fs.ext4 y despues copiar la informacion al particion nuevo.  Si no, estas mas o menos usando ext3 pero con el driver de ext4.

Si no te molesta a hacer todo eso... la maquina va a andar barbero...

;)

---

### Post by h9005 on 2009-02-18
Jaja menos mal que no lo instalé entonces...

---

### Post by sdennie on 2009-02-19
> **h9005 said:**
> Jaja menos mal que no lo instalé entonces...

En realidad me encanta ext4 pero hasta Jaunty, es un poco dificil a armar el sistema asi.  Si tenes partitiones / y /home, con el kernel 2.6.28 podes cambiar /home a ext4 y no vas a tener ningun problema.  Esta complicadismo solo si tratas de usar ext4 por el root.

---

### Post by guillermolisi on 2009-02-19
Shaun

Me permitis reproducir literalmente lo que acabas de comentar en la seccion de Tutoriales en nuestro website y en la lista de e-mail para que este bien al alcance de quienes no participan del foro (logicamente con todas las referncias del caso) ?

---

### Post by sdennie on 2009-02-19
> **guillermolisi said:**
> Shaun

Me permitis reproducir literalmente lo que acabas de comentar en la seccion de Tutoriales en nuestro website y en la lista de e-mail para que este bien al alcance de quienes no participan del foro (logicamente con todas las referncias del caso) ?

Si incluidas un grande, "Don't try this at home!" no hay ningun problema.  No es un "HOWTO" exacto pero cambie dos maquinas con Hardy a ext4 y asi se hace.

---

### Post by clasificado on 2009-02-21
es re importante lo del mke2fs.ext4

sino, realmente no hiciste nada ^^

---

### Post by h9005 on 2009-02-21
Ah ok gracias... muy buena data!

---

