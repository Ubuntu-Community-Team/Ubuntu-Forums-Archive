---
title: "No mostrar iconos de particiones montadas en el escritorio"
date: 2009-12-14
forum: Software
---

### Post by thegreeneyes on 2009-12-14
Perdonen que no tenga ningun escritorio para mostrar, pero quizás me puedan ayudar con algo que tiene que ver con lo que hacen, me parece.

En Ubnutu 9.10 incluí dos particiones que tengo del disco en fstab para que se monten automaticamente al bootear, pero los íconos de estas particiones se muestran en el escritorio. Saben cómo puedo hacer para que no estén en el escritorio?. Estuve buscando y encontré algunas recetas yendo al "gconf-editor" pero esas recetas eran para Ubuntu 7.xx creo y no encuentro los items que se citan allí. Si alguien puede sugerirme algo se lo agradezco.

Muy interesantes algunos escritorios!!

Saludos

---

### Post by matias_tati on 2009-12-15
[http://infomatica.wordpress.com/2007/04/20/verquitar-iconos-del-escritorio-en-ubuntu/](http://infomatica.wordpress.com/2007/04/20/verquitar-iconos-del-escritorio-en-ubuntu/)

Saludos!!

---

### Post by granjero on 2009-12-15
thegreeneyes:  hacé así:

alt+F2 > escribi **gconf-editor** > APPS > NAUTILUS > DESKTOP > destildá "volumes_visible"

salud!

---

### Post by thegreeneyes on 2009-12-15
El que sabe, sabe..., pero yo ni sé ni soy jefe!!! ;-)

muchas gracias a ambos, funcionó bien la solución.

---

### Post by FB91 on 2009-12-15
hace bastante escribí sobre eso en mi blog...

[http://fb91.com.ar/blog/2009/08/18/eliminar-icono-de-volumenes-en-el-escritorio-de-gnome/](http://fb91.com.ar/blog/2009/08/18/eliminar-icono-de-volumenes-en-el-escritorio-de-gnome/)

salu2!

---

