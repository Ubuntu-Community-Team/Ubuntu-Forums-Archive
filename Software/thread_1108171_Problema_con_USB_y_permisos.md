---
title: "Problema con USB y permisos"
date: 2009-03-27
forum: Software
---

### Post by infiter789 on 2009-03-27
En primer lugar, guarde carpetas de un DVD y se almacenaron con un candado arriba.
No recuerdo cual era el comando de permisos para hacerlas libre para todos los usuarios :S.

Y por segundo, quiero formatear mi pendrive y hacerlo booteable con Debian (la mini imagen).

*tenganme paciencia que estoy aprendiendo y rapido :P*

P.D: Use el comando dmesg para ver donde el pendrive esta... pero no lo encontre, veia muchos usb is in (y un numero). Pero ningun /dev/sda ni nada similar.

Saludos.

---

### Post by euzkoarima on 2009-03-27
A la primer pregunta, en gnome al menos, botón derecho->propiedades->solapa permisos
Sino el comando para consola es chmod
La segunda, no se.

Saludos,
Eduardo

---

### Post by infiter789 on 2009-03-27
Si, es chmod gracias.
Y el tema del pendrive... es para instalar Debian en una mini notebook.

---

### Post by exegeses on 2009-03-28
> **infiter789 said:**
> En primer lugar, guarde carpetas de un DVD y se almacenaron con un candado arriba.
No recuerdo cual era el comando de permisos para hacerlas libre para todos los usuarios :S.

Y por segundo, quiero formatear mi pendrive y hacerlo booteable con Debian (la mini imagen).

*tenganme paciencia que estoy aprendiendo y rapido :P*

P.D: Use el comando dmesg para ver donde el pendrive esta... pero no lo encontre, veia muchos usb is in (y un numero). Pero ningun /dev/sda ni nada similar.

Saludos.

[COLOR="DarkSlateGray"]**respecto de los permisos:**[/COLOR]
el comando es:     

     ```
chmod -Rf 777 /PATH
```

debes hacerlo bajo sudo

o sea 

     ```
sudo chmod -Rf 777  /PATH
```

siendo PATH la ruta que necesites, por ejemplo /media/sdb2/TuDirectorio

esa es la manera viaja de hecerlo, pero es sencillo

7 es dar todos los permisos, o sea rwx


la manera nueva es:

     ```
chmod -rwxrwxrwx /PATH 
```

siendo PATH la ruta que necesites, por ejemplo /media/sdb2/TuDirectorio

espero haberte ayudado.
si no ha sido claro, me repreguntas y haré lo mejor para dar una mejor explicación.


```

no he mencionado 

0  =  ---  =  sin acceso
1  =  --x  =  ejecución
2  =  -w-  =  escritura
3  =  -wx  =  escritura y ejecución
4  =  r--  =  lectura
5  =  r-x  =  lectura y ejecución
6  =  rw-  =  lectura y escritura
7  =  rwx  =  lectura, escritura y ejecución

ni stick bits a fin de facilitar la explicación. espero la explicación haya sido simple y clara.

```

saludos
exegeses

---

### Post by infernus92 on 2009-03-28
chmod no es para cambiar los atributos a un archivo??
a mi me parece mas como chown para cambiar el grupo de usuarios que tiene acceso a el...

---

### Post by exegeses on 2009-03-28
> **infernus92 said:**
> chmod no es para cambiar los atributos a un archivo??
a mi me parece mas como chown para cambiar el grupo de usuarios que tiene acceso a el...

```
chmod
``` cambia los permisos de un archivo. y tiene en cuenta la jerarquía Owner, Group, World (Usuario, Grupo, Otros).

por otro lado ```
chown
``` cambia sólo el OWNER/GROUP del archivo, o sea que 

cambia el user y group que lo creó.


ejemplo:

    ```
chown nuevousuario archivo1 [archivo2 archivo3...]
```

        cambia el propietario de archivo1 [archivo2, etc]. que pasará a ser de nuevousuario

    ```
chown -R nuevousuario directorio
```

        cambia el propietario para que pase a ser DE nuevousuario EL directorio de manera recursiva, 
o sea: a todos los archivos y subdirectorios contenidos en él, 
de este modo cambiándolos también de forma recursiva en todos los archivos de sus subdirectorios.


de la misma manera, usando USUARIO.GRUPO, se pordrá cambiar el OWNER y el GROUP del archivo seleccionado.

```
chown -R nuevousuario.nuevogrupo directorio
```


espero haber sido de ayuda.
si no es así, repregunten, la idea de esta comunidad es ayudarnos todos y aprender  compartiendo.

saludos
exegeses

---

### Post by Nikolopulus on 2009-04-13
Hola, acabo de crear un usuario en mi máquina (compratida con quienes vivo) y no quiero hacerlo sudoer, pero necesito darle permiso para que monte otras particiones a parte de en la que está Ubuntu ¿como lo hago?
Gracias

---

### Post by staar on 2009-04-13
Sistema -> Administración -> Usuarios y grupos -> *usuario* -> Propiedades -> Privilegios del usuario

saludos

---

### Post by Nikolopulus on 2009-04-14
ya lo hice, tiene todas las opciones habilitadas pero igual no puede montar el segundo disco que tengo en la máquina ni ninguna partición del primero (formateadas en ntfs y fat32)

---

### Post by staar on 2009-04-14
fijate en Sistema -> Administración -> Autorizaciones -> org -> freedesktop -> hal -> storage -> Mount filesystems from internal drives -> Autorizaciones explícitas -> Conceder

saludos

---

