---
title: "Instalar 2 distros en un mismo HDD (Ubuntu y openSUSE)"
date: 2009-07-05
forum: Software
---

### Post by Bonyo on 2009-07-05
Como les va compatriotas linuxeros, mis dudas se basan en que tengo Ubuntu Intrepid y quiero instalar openSUSE 11.1. No tengo espacio sin particionar en el disco, por lo tanto, no sé qué hacer, porque estuve con el Live CD del openSUSE para instalarlo y me decía de borrar la partición donde tengo el Ubuntu.

Si alguien me puede ayudar, desde ya se lo agradezco.

---

### Post by staar on 2009-07-05
podrías achicar alguna partición existente para dejar espacio libre suficiente, para eso podés usar gparted ```
sudo aptitude install gparted
```lo encontrás en Sistema > Administración > Editor de particiones, acordate que no podés tener más de 4 particiones primarias por disco y que entre los dos linux podés compartir la partición de swap...

si no sabés que partición achicar o tenés algún problema, posteate la salida de ```
sudo fdisk -l
```para que sepamos como tenés el disco...

saludos

---

### Post by Bonyo on 2009-07-06
> **staar said:**
> podrías achicar alguna partición existente para dejar espacio libre suficiente, para eso podés usar gparted ```
sudo aptitude install gparted
```lo encontrás en Sistema > Administración > Editor de particiones, acordate que no podés tener más de 4 particiones primarias por disco y que entre los dos linux podés compartir la partición de swap...

si no sabés que partición achicar o tenés algún problema, posteate la salida de ```
sudo fdisk -l
```para que sepamos como tenés el disco...

saludos

Bueno, muchas gracias. Lo pruebo y te digo qué tal me fue. :)

---

### Post by biale on 2009-07-07
Hay un pequeño problema con eso...

Bajo ubuntu operativo gparted solo va funcionar con particiones que se puedan desmontar. No sería el caso de "/home" y "/". O sea que si sirve para ver que puedo achicar pero (en principio) no sirve para hacer el trabajo en cuestion.

Tener a mano un CD de arranque live reciente: Ubuntu, SystemRescueCd, etc. Y por supuesto un backup de todo por las dudas. También tendría a mano una copia del supergrub disk.

Saludos

---

