---
title: "Cerrar tapa de laptop - no hacer nada"
date: 2009-11-11
forum: Software
---

### Post by cidro on 2009-11-11
Buenas, tengo una pequeña duda con ubuntu, especificamente con el gestor de energia.
Alguien sabe si existe la posibilidad de agregar una opcion para "no hacer nada" (o "hacer nada") cuando se cierra la pantalla del portatil. Lo que sucede es que tengo un monitor adicional conectado a mi laptop, y cuando no estoy trabajando (viendo peliculas, jugando o navegando) no necesito usar la pantalla de mi laptop, pero si la cierro, se apagan los 2 monitores, tanto el del laptop como el adicional.

Si alguien sabe como arreglar esto y me puede dar una mano, se agradece muchisimo.

Pablo Canales.

---

### Post by cidro on 2009-11-11
Cuec!
Como siempre era cosas de buscar un poco dentro del "gconf-editor" (casi todas las configuraciones se encuentran ahí).
Por si alguien llega a tener el mismo problema, aca les dejo la solucion.
Con "Alt+F2" entramos "gconf-editor".
Dentro del editor, navegamos hasta "gnome-power-manager" -> "buttons"
Ahí cambiamos el valor que tenga la opcion "lid_ac" (adaptador de corriente) o "lid_battery" (con bateria) dejándolo en "nothing" (sin las comillas)... y LISTO!

Espero ha alguien le sirva.

---

### Post by Carlos C on 2009-11-11
Movido a "Software". Por favor recuerda leer [esto]("http://ubuntuforums.org/showthread.php?t=1319475") antes de publicar nuevamente.


Saludos.

---

### Post by donmatas on 2010-03-31
genial compa!
muchas gracias

salud
M

---

### Post by danielelias22 on 2011-05-15
Gracias!

---

