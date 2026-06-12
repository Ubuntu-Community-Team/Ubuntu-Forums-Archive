---
title: "Problemas con directorio borrado"
date: 2009-03-30
forum: Software
---

### Post by Andyvec on 2009-03-30
Hola a todos

Nuevamente estoy pidiendo ayuda a usuarios más experimentados. Estoy teniendo muchos problemas con paquetes que se rompen y/o que aparentan estar rotos cuando los bajo del las fuentes oficiales.

Instalando el antivirus Clam, un paquete parecía estar roto desde la fuente, no me fue posible repara este paquete con Synaptic, entonces decidí borrar el cache de las actualizaciones (/var/cache/apt/archives/) para que lo vuelva a bajar de 0.

Evidentemente, esto no se podía hacer, y ahora rompí el gestor de actualizaciones.

Desde ya muchas gracias por su ayuda

---

### Post by pablo.s on 2009-03-30
> **Andyvec said:**
>  entonces decidí borrar el cache de las actualizaciones (/var/cache/apt/archives/) para que lo vuelva a bajar de 0.

Evidentemente, esto no se podía hacer, y ahora rompí el gestor de actualizaciones.

Borraste el directorio? O borraste desde Synaptic la caché?
¿Que pasa si hacés **sudo mkdir /var/cache/apt/archives** ?

---

### Post by Andyvec on 2009-03-31
Borré el directorio entero, si intento hacer:
*"sudo mkdir /var/cache/apt/archives"*
el resultado es:
*"mkdir: no se puede crear el directorio «/var/cache/apt/archives»: No existe el fichero ó directorio*"

AL intentar abrir un gestor de paquetes el error que me da es similar este:
[I]"E: No se puede escribir en /var/cache/apt/
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report."[/I]

---

### Post by pablo.s on 2009-03-31
> **Andyvec said:**
> Borré el directorio entero, si intento hacer:
*"sudo mkdir /var/cache/apt/archives"*
el resultado es:
*"mkdir: no se puede crear el directorio «/var/cache/apt/archives»: No existe el fichero ó directorio*"

A ver, vamos por partes:
1)Fijate si tenés el directorio /var/cache/apt
2) Si lo tenes entonces te tiene que permitir crear el 
directorio /archives
3)Podés probar de forma gráfica con sudo Nautilus navegando
hasta /var/cache/apt y ahi crear el directorio

Saludos.

---

### Post by clasificado on 2009-04-02
> **Andyvec said:**
> Hola a todos

Nuevamente estoy pidiendo ayuda a usuarios más experimentados. Estoy teniendo muchos problemas con paquetes que se rompen y/o que aparentan estar rotos cuando los bajo del las fuentes oficiales.

Instalando el antivirus Clam, un paquete parecía estar roto desde la fuente, no me fue posible repara este paquete con Synaptic, entonces decidí borrar el cache de las actualizaciones (/var/cache/apt/archives/) para que lo vuelva a bajar de 0.

Evidentemente, esto no se podía hacer, y ahora rompí el gestor de actualizaciones.

Desde ya muchas gracias por su ayuda

¿No será que en lugar de borrar la carpeta archives, borraste toda la carpeta apt?

clasificado

---

### Post by Andyvec on 2009-04-02
Como el problema persitía terminé borrando toda la carpeta.

La verdad es que no se como solucionarlo, en princpio desde el navegador de archivos no puedo crear carpetas porque no tengo permisos, entonces lo hago mediante consola con SUDO, pero igualmente auqnue vuelva a crear las carpetas me sigue diciendo que no las encuentra.

---

### Post by pablo.s on 2009-04-02
1     Tenés la carpeta /var?                       SI      NO
2     Tenés la carpeta /cache?                  SI      NO
3     Tenés la carpeta /apt?                       SI      NO
4     Tenés la carpeta /archives?             SI      NO


Marcá las carpetas que tenés en un post.
Te voy ayudando. Porque hay otras carpetas que son
necesarias y hay que crear.

Dentro de /archives está una carpeta llamada partial
donde guarda los paquetes que no instala por una
razón u otra (puede ser porque los baja pero se
interrumpe la instalación). Esa carpeta puede estar
vacia. La creas y la dejas vacia. También en /archives
hay un archivo propiedad de root que se llama lock.

Una vez hayas creado esto, ya podés intentar hacer

sudo apt-get update.

Saludos.

---

### Post by EnriqueK on 2009-04-03
A ver, si lo que has borrado lo has hecho en forma gráfica, es muy posible que que realidad no se hayan borrado, sino que fueron enviadas a una papelera oculta dentro de /root , o sea probá si están poniendo en terminal
 ```
sudo nautilus /root/.local/share/Trash/files
```
Si definitivamente no se encuentran en la papelera oculta de /root, tenés la posibilidad de usar el Live CD de instalación y reponer de allí lo que has borrado.

---

### Post by infernus92 on 2009-04-03
si alguno de nosotros hace un paquete con nuestras carpetas de las que le faltan a el y lo sube a rapidshare/megaupload, serviria de algo?

---

