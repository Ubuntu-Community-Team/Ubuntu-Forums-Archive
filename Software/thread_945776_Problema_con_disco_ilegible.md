---
title: "Problema con disco ilegible"
date: 2008-10-12
forum: Software
---

### Post by chulelinux on 2008-10-12
Hola nuevamente, hoy estoy con mi ubuntu y tratando de solucionar los problemas que tengo... Comento: tengo dos discos de 250g... Uno con Win (en particion separada) y una particion NTFS. En el otro tengo Ubuntu 8.04.. con sus debidas particiones (Sistema, Swap, Home) y una partición de 200 gb en fat 32. El problema que tengo es que tuve que reinstalar nuevamente Win, recuperé la grub sin problemas pero ahora, a diferencia de antes, no puedo acceder al disco donde tengo ubuntu. Es decir que desde mi sesion de usuario no puedo acceder a las carpetas o particiones por no tener permisos. Entro como root y si puedo ver las carpetas, pero no me deja cambiar los permisos de acceso para que en mi modo de usuario normal pueda acceder al contenido del disco. 
En propiedades de soporte (parado en la ventana de lugares y marcando el soporte) me dice: Tipo: Carpeta, Contenido: ilegible, Lugar: /media, Volumen:233gb, Modificado: desconocido, tipo del sistema de archivos: msdos. 
Si alguien me puede ayudar....

---

### Post by sebastianabate on 2008-10-13
No quedó muy claro cuáles son los directorios/particiones donde no podés entrar y qué querés decir con
 
> no puedo acceder al disco donde tengo ubuntu. Es decir que desde mi sesion de usuario no puedo acceder a las carpetas o particiones por no tener permisos
 
porque ¿si no podés acceder al disco con ubuntu cómo hacés para iniciar sesión? 
 
Podés postear los errores que te tira cuando tratás de entrar a los directorios desde consola? También posteá el contenido de /etc/fstab y los permisos de los direcotios con problemas, podés hacer un "ls -l directorio-padre-del-problematico" para esto, por ejemplo si no podés entrar a /media/Torrents hacé
 
```
ls -l /media
total 12
lrwxrwxrwx 1 root      999    6 2008-10-09 18:20 cdrom -> cdrom0
drwxr-xr-x 2 root      999 4096 2008-10-09 18:20 cdrom0
drwxrwxrwx 9 root   root   4096 2008-10-12 21:28 Torrents
drwxrwxrwx 4 abates abates 4096 2008-10-12 00:33 VMs
```

---

### Post by chulelinux on 2008-10-14
Perdón Je je, la no claridad es resultado de que todavía le estoy cazando la onda a ubuntu. A ver si lo dejo más claro: Puedo entrar a mi sesión de ubuntu sin problemas y trabajar con las carpetas de home sin dramas, lo que no puedo hacer es leer (no aparece) o trabajar con la partición Fat32 que está en el mismo disco físico en que tengo Ubuntu y su home. Por ej: voy al menu lugares, me posiciono en el disco en cuestión y no me aparecen las carpetas ni nada (y posicionado allí, al ver las propiedades del disco la info me marca que es ilegible)... por ende no puedo acceder a los documentos alojados en esa partición FAT32. La cosa es que si entro como root si puedo acceder.a todo sin problemas... Intenté cambiar los permisos de acceso desde allí (bajo seción root) para que en mi sesión de usuario pueda también ver y trabajar con las carpetas pero no me deja hacerlo... Esto me ocurre desde que reinstalé win (en otro disco físico). Esppero que se haya entendido mejor... y voy a ver lo que me señalaste sebastian...

---

### Post by chulelinux on 2008-10-14
realmente no se que ha pasado, pero lo pude corregir moviendo los archivos desde win y formateando la partición Fat32 y ahora sí la puedo ver nuevamente desde ubuntu...

Saludos

---

