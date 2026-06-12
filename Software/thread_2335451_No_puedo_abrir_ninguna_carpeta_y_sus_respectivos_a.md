---
title: "No puedo abrir ninguna carpeta y sus respectivos archivos"
date: 2016-08-28
forum: Software
---

### Post by lluvia on 2016-08-28
Buenas noches a todos los foristas, apelo a su ayuda ya que yo soy novata en este SO.
Versiòn de Ubuntu 16.04 LTS

No puedo abrir las carpetas que estàn en el escritorio ni tampoco se abre desde el ícono de archivo (aparece la ruedita y nada) o desde "buscar en el equipo", esto sucede a partir de que pasé las fotos y documentos de estudio de la facultad del cel a la pc (no se si eso tendrá algo que ver). Intenté con el nautilus y pasó lo siguiente:

[FONT=courier new]
[I]~$ nautilus --no-desktop

(nautilus:12997): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:12997): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
No se pudo registrar la aplicación: Se alcanzó el tiempo de expiración

(nautilus:12997): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:12997): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:12997): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed[/I][/FONT]

Instalé "Tree" para ver si aparecían los archivos dentro de los directorios y si aparecen, pero en diferentes colores por ejemplo un pdf en blanco y otros pdf en verde... Y aquí me quedé.

Por favor si alguien me puede dar una ayuda, las fotos son de viajes, eventos de mis hijos y no quiero perderlas :( . 

Desde ya muchas gracias a toda la comunidad. Saludos :)

---

### Post by lluvia on 2016-09-04
Muchas gracias, ya fue solucionado!!! :D

---

