---
title: "Ícono dropbox en Xubuntu 16.04"
date: 2016-06-02
forum: Software
---

### Post by donmatas on 2016-06-02
Instalé el Xubuntu 16.04. Todo muy bien, salvo que el icono del dropbox en el panel de notificaciones no funciona (solo aparece un circunferencia roja y no da opciones, aunque la aplicación sigue sincronizando).

Esto es un problema recurrente, según se constata en diversos foros. Como todos están en inglés, les comparto esta solución, provista por [Ads20000]("https://launchpad.net/~ads20000") en los r[eportes de bugs oficiales]("https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/1546176/comments/27"), a la que agregué más detalles para principiantes (funcionó para mi).

Ejecuta en el terminal el siguiente comando:

```
dropbox stop && dbus-launch dropbox start
```

Si no te aparece el ícono correctamente, prueba con:

```
dropbox stop && DBUS_SESSION_BUS_ADDRESS="" dropbox start

```

Luego anda a "preferencias" del dropbox (en el ícono) y deselecciona "iniciar Drobox al arrancar el sistema". De esta manera.

Hecho lo anterior, vas al menu, y ahí escribes "Sesión e inicio" y lo pinchas. En la ventana selecciona la pestaña "Autoarranque de aplicaciones", y pincha "Añadir.

Nombre: Dropbox
Descripción: solución para el icono
Orden: dbus-launch dropbox start

Luego clickeas aceptar y reinicia la sesión

salud!

---

### Post by donmatas on 2016-08-07
Hola,
tuve que reinstalar el xubuntu y ahora no me funcionar el drobox. Si aplico mi propia solución, me aparece esto:

```
(dropbox:6506): GLib-GObject-WARNING **: cannot register existing type 'GdkDisplayManager'

(dropbox:6506): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(dropbox:6506): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
```

---

### Post by vlad-tepes89 on 2017-05-27
Muchas gracias! Llevaba meses con el icono inservible. Ahora al hacer una instalación limpia de Xubuntu 17.04 me he animado a solucionarlo siguiente estas instrucciones. Perfecto todo!

---

