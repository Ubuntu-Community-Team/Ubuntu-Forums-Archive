---
title: "¿Dar permisos a /var/www?"
date: 2009-08-07
forum: Software
---

### Post by rebecabur on 2009-08-07
Acabo de instalar eclipse y apache2. Necesito guardar mi proyecto php en el directorio /var/www pero desde el propio eclipse me es imposible. Tampoco puedo hacer un copia/pega porque no tengo los permisos. 

He intentado darle los permisos mediante la consola pero sigo sin conseguirlo.
Alguna idea?

Gracias!

---

### Post by pablo.s on 2009-08-07
Has probado copiarlo
como superusuario?

---

### Post by josecuervo86 on 2009-08-07
No te aconsejaria que le des permisos a esas carpetas. En vez de eso podrías abrir una terminal y poner 
```
sudo nautilus
```
Eso te abre nautilus como superusuario y ahora si podes copiar/pegar en esa carpeta

---

### Post by guillermolisi on 2009-08-07
Algo que en general se recomienda como Best Practice es que los contenidos que seran gestionados por Apache (/var/www/ ......) sean www-data:www-data (owner:group) o el nombre de user:group que Apache reconozca como propios en la instalacion.

Los permisos se asignan a esta combinacion como rw-rw-r--, en general (siempre puede haber casos de excepcion), particularmente si el site esta en produccion.

Aclaro que (por ahora) no uso Eclipse, asi que no conozco si requiere algo en particular al respecto.

Edit: +1 sudo nautilus

---

