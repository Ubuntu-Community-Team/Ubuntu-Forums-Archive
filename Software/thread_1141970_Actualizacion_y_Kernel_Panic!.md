---
title: "Actualizacion y Kernel Panic!"
date: 2009-04-28
forum: Software
---

### Post by z37a on 2009-04-28
Gente acabo de actualizar mi Jaunty, por alguna razon reinicie la PC y esta nunca mas arranco, me esta tirando un Kernel panic como que no me reconoce mi EXT4, "...not syncing: VFS: unable to mount...", el tema es que ya intente de todo, reinicie con el failsafe y lo mismo.

Comento lo que ya hize:

- Intente entrar en failsafe(no funco)
- Reformatie la particion a ext3 con previo backup de los archivos y posterior restauracion(nada)
- Desde el LiveCD arranca(descarto hard)
- La verificacion del fsck dio que estaba todo OK(pero igual kernel panic)
- Copie los archivos del liveCD del /boot al /boot del HDD(y no funciono)

Empeze a bajarme el CD de la version Final para reinstalar(Total el /home lo tengo separado solo perderia los programas instalados) pero me gustaria saber si no tengo algun otra alternativa o si le paso a otro????

---

### Post by clasificado on 2009-04-28
¿y si inicias con el kernel viejo?

fijate que te tiene que aparecer como opción en el grub

clasificado

---

### Post by z37a on 2009-04-28
> **clasificado said:**
> ¿y si inicias con el kernel viejo?

fijate que te tiene que aparecer como opción en el grub

clasificado

Tengo solo un kernel, la ultima vez que instale jaunty fue con la RC, asi que solo tengo un kernel

PD: Tambien probe en copiar los archivos del kernel del live CD pero paso lo mismo!!!!

---

### Post by infernus92 on 2009-04-28
y con el mismo kernel a prueba de fallos?? o es eso de failsafe que decias antes??

---

### Post by josecuervo86 on 2009-04-28
> **infernus92 said:**
> y con el mismo kernel a prueba de fallos?? o es eso de failsafe que decias antes??

Ese es el modo a prueba de fallos

---

### Post by z37a on 2009-04-29
Ya lo solucione gente, gracias por sus respuestas, aproveche que tenia el /home separado, baje en otra pc la iso y la grabe del 9.04 final(solo tenia CD del Beta ensima!!!) y quedo, de paso no instale los libs de 32 bits, puse flash y java de 64 jeje.

Gracias por las respuestas tan rápidas!!!!

---

