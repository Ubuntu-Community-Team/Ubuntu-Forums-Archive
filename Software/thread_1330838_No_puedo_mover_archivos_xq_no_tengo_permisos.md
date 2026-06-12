---
title: "No puedo mover archivos xq no tengo permisos"
date: 2009-11-18
forum: Software
---

### Post by WooS on 2009-11-18
Gentes estaba queriendo personalizar mi Conky y los iconos pero no me deja mover los archivos a la carpeta .fonts ni a la carpeta themes ya que me sale un error diciendo q no tengo permiso. Como saco eso?

---

### Post by Sleeping Beauty on 2009-11-18
Tenés que hacerlo como superusuario.
Yo abro un terminal y pongo: gksu nautilus (te va a pedir tu contraseña)
Así se abre el navegador de archivos para root de manera tal que ya tenés los pemisos suficientes para hacer lo que necesites. En el árbol de directorios buscas la carpeta y moves lo que quieras ;)
Fijate que los iconos cuando estas como root son diferentes al tema que usas habitualmente (grises si mal no recuerdo)
Saludos

---

### Post by dirty fingers on 2009-11-18
yo cuando es así abro con sudo en vez de gksu. ¿es lo mismo?

---

### Post by pablo.s on 2009-11-18
> **dirty fingers said:**
> yo cuando es así abro con sudo en vez de gksu. ¿es lo mismo?

gksudo es un sudo gráfico en GTK.

---

### Post by granjero on 2009-11-18
el problema que encontré yo con esa metodología es que después los archivos me quedaron con los permisos de root. y se los tuve que cambiar...

salud!

---

