---
title: "Permisos de archivos rebeldes"
date: 2009-02-16
forum: Software
---

### Post by Peter Smile on 2009-02-16
Muchachos, tengo un problema y no sé qué estoy haciendo mal.

Les cuento:

Se me ocurrió la idea de compartir una carpeta en la red, con samba sobre todo y también a través del SimpleHTTPServer de python, pero mi problema tiene que ver con la seguridad.

Para poder hacerlo de manera más o menos segura se me ocurrió que lo mejor era crear un usuario nuevo sin privilegios y a él darle la propiedad de la carpeta y sus archivos; para ello lo creé con el siguiente comando ```
useradd -g compartida -d /dev/null -s /bin/false compartidor
```
Creé la carpeta en /home/ y le dí la propiedad de la misma al usuario "compartidor". Con la idea de que pudieran escribir en la carpeta solamente los usuarios que estuvieran autorizados (o sea que formaran parte del grupo "compartida").

Hasta ahí todo muy bien, el problema es que puedo darle todos los permisos que yo quiera a los "otros" pero tanto el propietario como el grupo en cuestión no obtienen los permisos de lectura y escritura de archivos.

Lo estoy haciendo de modo gráfico: cuando le doy los permisos (usando un nautilus ejecutado como root) al cerrar la ventana se me resetea a como estaba antes (es decir, permisos para ver y escribir la carpeta pero ningún permiso con respecto a los archivos dentro).

Intenté también con la consola, pero el resultado es muy similar, obtienen permiso con respecto a la carpeta pero ninguno para poder escribir los archivos que ésta contendrá (actualmente está vacía).

Estoy seguro que le estoy pifiando en algo. ¿En qué?

---

### Post by Hei Ku on 2009-02-16
que pasa si lo haces desde la terminal?

Por ej:

```

sudo chown -R compartidor:compartidor /home/compartidor

```

---

### Post by Peter Smile on 2009-02-16
¡Anduvo bárbaro!

¡Muchas gracias!

---

