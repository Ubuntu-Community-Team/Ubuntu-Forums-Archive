---
title: "en gnome como"
date: 2009-01-27
forum: Software
---

### Post by tsueseres on 2009-01-27
cuando se le da boton derecha y sale agregar nuevo no hay una manera de agregar mas documentos como en windows boton derecha nuevo y que aparecen word paint etc

---

### Post by sartrejp on 2009-01-29
Fijate los nautilus scripts, que aparecen al dar click derecho y cumplen otras funciones, pero no debe ser difícil (tomando como base los que hay) hacer algunos que solo lanzen una aplicación.

---

### Post by tsueseres on 2009-01-29
> **sartrejp said:**
> Fijate los nautilus scripts, que aparecen al dar click derecho y cumplen otras funciones, pero no debe ser difícil (tomando como base los que hay) hacer algunos que solo lanzen una aplicación.

como llego a esos scrips?

---

### Post by Air23 on 2009-01-29
> **tsueseres said:**
> cuando se le da boton derecha y sale agregar nuevo no hay una manera de agregar mas documentos como en windows boton derecha nuevo y que aparecen word paint etc

En tu home fíjate si tenes una carpeta de nombre "Templates" o "Plantillas". También chequea si existe una carpeta oculta con alguno de esos nombres (para ver las ocultas es ctrl+H).

Si no existe dicha carpeta la tenes que crear, llamándola "Templates", "Plantillas" o como quieras (queda mejor si la creas oculta, pero es cuestion de gustos)

Después vas a los distintos programas cuyos documentos queres tener a mano en el menú contextual, creas sus correspondientes documentos vacios y los guardas en la carpeta que acabas de crear. Por ejemplo abrir OpenOffice Writer y guardas el documento en blanco en la carpeta en cuestión. Haces eso con todos los programas que quieras.
Luego abris un archivo:
```
gedit ~/.config/user-dirs.dirs
```
Vas a la linea que dice: XDG_TEMPLATES_DIR, que debería estar así:
```
XDG_TEMPLATES_DIR="$HOME/"
```
Y la editas para que quede de alguna de estas maneras (segun como nombraste a la carpeta):
```
XDG_TEMPLATES_DIR="$HOME/.Templates"
XDG_TEMPLATES_DIR="$HOME/.Plantillas"
```
Hecho esto deberías tener los nuevos tipos de archivo disponibles en el menu contextual

PD: El nombre que le des a los archivos es el mismo con el que van a figurar en el menu

Fuente:[http://www.yakiboo.net/?p=332](http://www.yakiboo.net/?p=332)

---

