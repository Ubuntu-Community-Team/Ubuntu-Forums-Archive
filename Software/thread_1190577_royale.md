---
title: "royale"
date: 2009-06-18
forum: Software
---

### Post by tsueseres on 2009-06-18
hola, alguien tiene de casualidad este tema o un link que tenga una descarga buena de este tema se llama royale creo de roy windows royale, este me gusto mucho ya que hay otro royale pero aparece la barra de start como la de xp y no quiero que tenga logos de windows, y ya que mi color favorito es el azul este tema me ha llamado mucho la atencion, pero no puedo bajarlo de ningun lado siempre me aparece que  no se encontro

este es como se ve 
[IMG]http://www.technama.com/wp-content/uploads/2009/05/royale.jpg[/IMG]

y este es un link que me dice que no se encontro

[http://gnome-look.org/content/show.php/Royale?content=76081](http://gnome-look.org/content/show.php/Royale?content=76081)

---

### Post by sartrejp on 2009-06-18
Con ubuntu tweak podés cambiarle la imagen al menú y ponerle la que quieras (para sacarle el starto logo)

Sino, para cambiar la imagen sin ubuntu tweak sería
- Alt+F2 y escribis:
gconf-editor

- en la ventana buscas la clave: apps-->panel-->objects-->objects_0

- Donde pone “object_type” lo cambiás por “menu_object“

- Donde pone “custom_icon“, poné el path (la ruta) donde este la imagen que querés poner.

Ahora en la terminal ponés

$ killall gnome-panel

Para recargar la informacion del panel.
Y si lo que querés es volver a la situacion original del panel habría que poner:

gnome-session-remove gnome-panel
gconftool-2 –recursive-unset /apps/panel
gnome-panel &

No es exactamente lo que pedís, pero por ahí te ayuda

---

