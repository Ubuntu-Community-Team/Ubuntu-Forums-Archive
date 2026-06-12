---
title: "sudo aqui , sudo alla"
date: 2009-11-04
forum: Software
---

### Post by fachamix on 2009-11-04
hola a todos.

me gustaria saber si existe alguna manera para que Ubuntu 9.04 deje de pedirme la contraseña de admnistrador cada ves que tenga que hacer algo (cambiar hora, montar particiones , etc...)

estoy desarrollando un sistema, para usuarios muy "especiales", acostumbrados a una vida de windows , y no puedo lograr algo automatizado porque siempre tienen que escribir la contraseña

saludos.

---

### Post by guillermolisi on 2009-11-04
Siempre hay alguna forma de enmascarar ese tipo de cosas solo que tendras que trabajar mas para que tus usuarios no lo hagan. La idea de pedir la contraseña para arrogarse privilegios de root es una de las carcteristicas mas importantes que hacen a la seguridad de los sistemas Linux.

Habria que conocer algo mas de detalle para saber que metodo aplicar en cada caso.

---

### Post by anarko on 2009-11-04
> **fachamix said:**
> hola a todos.

me gustaria saber si existe alguna manera para que Ubuntu 9.04 deje de pedirme la contraseña de admnistrador cada ves que tenga que hacer algo (cambiar hora, montar particiones , etc...)

estoy desarrollando un sistema, para usuarios muy "especiales", acostumbrados a una vida de windows , y no puedo lograr algo automatizado porque siempre tienen que escribir la contraseña

saludos.

Si hay una forma, tenes que editar con el comando "visudo" el archivo /etc/sudoers ( si lo editas con otra cosa no anda, o porlomenos no supe hacerlo andar )

En la linea que tiene %admin tenes que dejarla masomenos asi
```
# Members of the admin group may gain root privileges
%admin ALL=NOPASSWD: ALL

```

Esto quiere decir que los usuarios del grupo "admin" no se le requiere pedir contraseña cuando ejecutan un comando que requiera autentificacion, esto no quiere decir que eliminas el sudo, sino que ya no les pide la clave cuando ejecutas un comando como "sudo mkfs.ext4 /dev/sda"
Nota: El ejemplo es MUY perjudicial para la salud de cualquier sistema linux semi normal.

El tema de la seguridad es uno de los temas mas importantes en cualquier linux, pero si vos ya definiste que esos usuarios tengan acceso mediante sudo a los comandos que solo estan permitidos a un administrador del sistma ( root ) poner o no poner la contraseña es algo anecdotico y mas tratandose de usuarios acostumbrados a Windows que estan tan automatizados que no leen nada solo hacen caso del boton "next"

---

### Post by fachamix on 2009-11-04
gracias por las respuestas, voy a probar el metodo y despues les cuento.

la verdad que si, este es unsistema que fue diseñado para windows, y ahora lo estamos haciendo funcionar bajo linux con WINE, a pesar de que anda un poquitito mas lento, ando perfecto, ... perfecto en serio.

lo unico es que cuando hay que usar un recurso remoto por ejemplo, salta el popular SUDO, entonces bueno, ya vere si funciona tu metodo 


saludos

---

### Post by juancarlospaco on 2009-11-04
Depende el nivel de Hacketa que le quieras meter, 
podrias montar el $HOME/.wine en un tmpfs (cargarlo en RAM),
para que ande mas rapido, tambien es recomendable usar EXT4.

---

