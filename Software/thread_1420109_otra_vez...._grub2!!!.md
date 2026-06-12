---
title: "otra vez.... grub2!!!"
date: 2010-03-02
forum: Software
---

### Post by infernus92 on 2010-03-02
hola gente... tanto tiempo sin darme una vuelta por aca...
vengo con un pequeño problemita, otra vez con grub2

La cosa es asi... hace un tiempo instale karmic en una computadora de la que nop soy el administrador principal. Todo bien, todo joya \\:D/ hasta que uno de los administradores principales decidio reinstalar ventanas y, por tanto, pisar el grub :frown:

hoy trate de reinstalarlo desde un LiveCd como lo hice siempre con grub legacy pensando que iba a ser de la misma manera... y para mi sorpresa no fue asi :S
busque un poco (la verdad no demasiado) sobre como reinstalar grub 2 y lei un poco los manuales de las funciones de grub que encontre... pero todo sin resultado.

Si alguno me pudiera explicar o pasar un link de como reinstalar grub2 lo mas expreso posible se lo agradeceria muchisimo!!!

Saludos

---

### Post by biale on 2010-03-03
En el foro hay al menos un thread que trata del tema. De todas maneras desde un Live CD la secuencia sería:

```


mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda


``` 

Yo lo hice desde el mismo Ubuntu y por lo tanto no necesite hacer el chroot.

Saludos.

---

