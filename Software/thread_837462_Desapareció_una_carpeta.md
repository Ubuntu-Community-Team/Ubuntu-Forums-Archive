---
title: "Desapareció una carpeta"
date: 2008-06-22
forum: Software
---

### Post by guisheca on 2008-06-22
Que tal comunidad, vengo un poco afligido a hacerles una consulta. Resulta que sin razón alguna, de manera inesperada ha desaparecido una carpeta de mi sistema de archivos, esta carpeta no contiene información vital, pero me preocupa que esto pueda pasar con alguna carpeta que si lo contenga.
La carpeta en cuestión se encuentra en mi /home, y lo que me parece raro es que nautilus aún detecta que el espacio que ocupa esta carpeta está en uso.
Soy consciente de que es difícil que me puedan ayudar con la información que proporciono, lo que quisiera es saber como puedo hacer alguna comprobación de disco a ver si está todo bien con él, la verdad que nunca tuve problemas de este tipo en ubuntu, de modo que no se bien como proceder. Se que puedo utilizar fdisk, pero no encuentro buena info al respecto.
Espero alguien me tire alguna idea, me siento desconcertado y preocupado, no quiero que me ocurra esto con otra carpeta.
Saludos.

---

### Post by Mauro22 on 2008-06-22
no esta oculta o algo asi??


Desde consola, en donde estaria tu carpeta hace un:

```
ls -la
```


Para correr un chkdisk lo tenes que hacer sin estar montado el disco. Es decir desde un live cd o cualquier medio, que no monte el disco.

---

### Post by guisheca on 2008-06-22
Mauro22 gracias por comentar, mirá, inicié desde el live-cd de hardy y ejecuté este comando:
> ubuntu@ubuntu:~$ sudo fsck /dev/sda5 -f -p -v
fsck 1.40.8 (13-Mar-2008)

   99398 inodes used (0.64%)
    3646 non-contiguous inodes (3.7%)
         # of inodes with ind/dind/tind blocks: 12037/744/5
22278918 blocks used (72.12%)
       0 bad blocks
       7 large files

   75236 regular files
    9778 directories
       0 character device files
       0 block device files
       0 fifos
      21 links
   14373 symbolic links (14366 fast symbolic links)
       2 sockets
--------
   99410 files
ubuntu@ubuntu:~$ 


Me parece que está todo bien, pero igual lo pongo para ver que opinan de esa devolución y del comando que ejecuté.
Saludos.

---

