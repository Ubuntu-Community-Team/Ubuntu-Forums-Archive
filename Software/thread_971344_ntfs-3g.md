---
title: "ntfs-3g"
date: 2008-11-04
forum: Software
---

### Post by tsueseres on 2008-11-04
tengo un problema al querer montar una particion ntfs antes funcionaba bien y derepente me sale esto


ntfs-3g mount failed to acces mountpoin/media/user

como puedo mntar mi unidad (posd: en windows si puedo abrirla)

---

### Post by tvtech on 2008-11-04
te hablas engles?  y que versión ubuntu?

en windows te necesitas uno conductor especial por montar una particion de ubuntu/ ext2, ext3, riserjfs......

lo siento para mi espanol yo hablar engles

---

### Post by tsueseres on 2008-11-04
> **tvtech said:**
> te hablas engles?  y que versión ubuntu?

a littel bit:

 ntfs-3g
i have a problem when i try to open my ntfs partition,
it used to work fine but suddenly this happens when i try to open it


ntfs-3g mount failed to acces mountpoin/media/user

how can i mount mi drive (in windows it works fine)
ubuntu

---

### Post by tvtech on 2008-11-04
eche una mirada a su archivo de fstab  

uso ```
sudo gedit /etc/fstab
```

usted quizás necesite para agregar manualmente el camino si no aparece en el archivo

Espero que esto ayude. o le señala en la dirección correcta

arrepentido utilicé un programa de traducción para escribir a máquina a usted

yo hablo un pequito de espanol, pero te queres aprender como hablar espanol!

---

### Post by c4d0rn4 on 2008-11-04
**tsueseres**, antes de meter mano, reiniciá la Pc en windows y asegurate de que se apague correctamente.

por si las dudas no sea eso, la proxima pegá el resultado de
```
sudo fdisk -l

```
para saber cual es la partición en caso de tocar el fstab

tengo idea que hay un comando mejor, por que da más info, pero ahora no me acuerdo cual era.

-------------
@ tvtech OFF-TOPIC
I'm amazed of how many people try to learn Spanish in this forum. =D

a tip:
I - yo
you - tu (it isn't te)
he /she - el / ella
we - nosotros
you - vosotros or ustedes
they - ellos

-------------------
examples:
*you* love _me_ -> *tu* _me_ amas
*I* love _you_ -> *yo* _te_ amo


sé que no es un foro para enseñar castellano, pero me enterneció su intento de escribir ajaj xD

---

### Post by faktorqm on 2008-11-05
> **tsueseres said:**
> a littel bit:

 ntfs-3g
i have a problem when i try to open my ntfs partition,
it used to work fine but suddenly this happens when i try to open it


ntfs-3g mount failed to acces mountpoin/media/user

how can i mount mi drive (in windows it works fine)
ubuntu

vieja en este foro se habla español. si queres hablar en ingles pedi ayuda en el general y listo. y fijate que exista el directorio /media/user.

---

### Post by tsueseres on 2008-11-05
gracias por la ayuda lo que hice al final fue quitar una linea de
Entry for /dev/ !! UNKNOW DEVICE !! :
la de mi unidad y listo ya la detecto

thanks for the help, at the end i removed a line from 
Entry for /dev/ !! UNKNOW DEVICE !! :
the one with my drive

---

### Post by undiaperfecto on 2008-11-05
probá instalando DISK-MANAGER esta en synaptic

---

