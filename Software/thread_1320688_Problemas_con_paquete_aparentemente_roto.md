---
title: "Problemas con paquete aparentemente roto"
date: 2009-11-09
forum: Software
---

### Post by xulin on 2009-11-09
Cada vez que instalo algo mas me sale este error. He tratado de solucionarlo con lo de los paquetes rotos arrancando en modo de recuperacion inclusive pero nada sigue sin desinstalarme el paquete.

 > _*language-pack-kde-en-base: el subproceso script post-removal instalado devolvió el código de salida de error 2*_

Alguien puede darme una sugerencia.

Tengo Karmic sobre una Presario c700 (laptop)

---

### Post by josecuervo86 on 2009-11-09
Con "lo de los paquetes rotos" te referis a la opción de synaptic que esta en **Editar** > **Reparar paquetes rotos**?

---

### Post by xulin on 2009-11-10
Puedes hacerlo desde la opción de snaptycs, arrancando en fail safe y eligiendo la opcion, o con apt-get autoremove. El problema es que  no puedo desinstalar con nada ese paquete de KDE que dice tener el error.

---

### Post by xulin on 2009-11-10
Copio y Pego solucion hallada en un blog

[B]2ª Solución: funciona:
[/B]
 1- abro nautilus con privilegios de root: alt+f2   …y:  gksu nautilus.
2- voy al directorio  /var/lib/dpkg/info,
3- alli borro todos los archivos que hacen refencia a “nombre-del-paquete”.
4- cierro el nautilus y abro synaptic.
5- ahora busco “nombre-del-paquete”,  lo pongo marcado para eliminar  y le doy a aplicar.
6- ahora si que se borra el “nombre-del-paquete”.
7- ya funciona correctamente el synaptic, deja instalar, desinstalar, borrar, etc.


El blog es:
[http://hatteras.wordpress.com/category/errores/](http://hatteras.wordpress.com/category/errores/)

---

