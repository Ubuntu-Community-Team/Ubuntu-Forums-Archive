---
title: "Kamoso y espacio en disco"
date: 2009-12-14
forum: Software
---

### Post by lexer98 on 2009-12-14
Hola chicos tengo un problema rarisimo instale el ''kamoso'' para mi web cam pero lo desinstale por que no me funcionaba me fui a la casa de un amigo y veo que cada vez tengo menos espacio en disco ahora hasta que llego al tener 0 bytes copie unos archivos a otro disco y veo que esta el proceso ''KAMOSO'' consumiéndome 100% del procesador pero no puedo localizar los archivos que me creo este proceso toy mas que seguro que es ese me faltan como 2+ gb en el disco

---

### Post by guillermolisi on 2009-12-15
Cambie el title para que sea mas representativo con el problema

---

### Post by Mister X on 2009-12-15
pueden ser logs tal vez... fijate en /var/log

o sino ejecuta el proceso y fijate los archivos que abre:
```
lsof|grep kamoso

```

---

### Post by lexer98 on 2009-12-15
me fije en var/log pesa solamente 13 mb  ... y al poner ese comando me arroja esto

[php]david@david-desktop:~$ lsof|grep kamoso
david@david-desktop:~$ sudo lsof|grep kamoso
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/david/.gvfs
      Output information may be incomplete.[/php]me fije en esa carpeta .gvfs no hay nada :S

---

### Post by alfplayer on 2009-12-15
Pudo suceder que el programa haya dejado grabando archivos de video aunque haya parecido que no estaba funcionando. Si sucedió esto habría que borrar esos archivos para recuperar el espacio.

---

