---
title: "No aparece la lista de OS"
date: 2009-03-28
forum: Software
---

### Post by elnetotaca on 2009-03-28
instaleen mi disco duro Ubunto 8.10 y hoy cree una particion para instalar el xp.
y no aparece ninguna lista de O.S, sino que inicia directamente con XP.
que hago?

---

### Post by z37a on 2009-03-28
> **elnetotaca said:**
> instaleen mi disco duro Ubunto 8.10 y hoy cree una particion para instalar el xp.
y no aparece ninguna lista de O.S, sino que inicia directamente con XP.
que hago?

El problema es que a Windows no le gustan otros SOs, lo que necesitas es reinstalar el grub.

[Fijate en esta guía](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by elnetotaca on 2009-03-28
> **z37a said:**
> El problema es que a Windows no le gustan otros SOs, lo que necesitas es reinstalar el grub.

[Fijate en esta guía](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Si muchisimas gracias, de corazón te lo agradezco, no puedo vivir sin ubuntu!

---

### Post by guillermolisi on 2009-03-28
> **elnetotaca said:**
> Si muchisimas gracias, de corazón te lo agradezco, no puedo vivir sin ubuntu!
Para proximas veces: Si vas a seguir con dual boot, primero instala Windows y despues Ubuntu.

Cuando Windows se instala borra la informacion de arranque correspondiente a la particion que contiene Ubuntu, en el MBR, por eso hay que proceder como te comente.

---

### Post by z37a on 2009-03-29
> **guillermolisi said:**
> Para proximas veces: Si vas a seguir con dual boot, primero instala Windows y despues Ubuntu.

Cuando Windows se instala borra la informacion de arranque correspondiente a la particion que contiene Ubuntu, en el MBR, por eso hay que proceder como te comente.

Por lo que tengo entendido no solo Windows te da problemas el bootloader, si no también opensolaris, así que escribo esto por si estas interesado en instalarlo que ya lo sepas!!!!

---

### Post by elnetotaca on 2011-11-08
Gracias a todos, esta solucionado.

My original post was;
I had Ubuntu, then created a partition that I was intending to use to install winXP

(at the time I was new and did not new about the hole Win/Linux thing worked)

so I did what people told me, reset grub;
starting up my pc with Super Grub2 Disk

-open the console then
# grub-install /dev/sda
$ sudo update-grub2

-and if that doesn't works, then try;

$ sudo aptitude install grub2 

-And it did worked!


thanks a lot.

---

