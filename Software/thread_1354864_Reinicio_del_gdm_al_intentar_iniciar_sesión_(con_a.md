---
title: "Reinicio del gdm al intentar iniciar sesión (con algunos usuarios)"
date: 2009-12-14
forum: Software
---

### Post by electronpositivo on 2009-12-14
Me sucede algo curioso con algunos usuarios al intentar iniciar sesión por gdm. Se trata de equipos clonados a los que les he cambiado el hostname y la configuración de red que acceden por ldap a un servidor de usuarios.

El caso es que a veces no inicia sesión en algunos usuarios, sin dar ningún error aparentemente. Simplemente se vuelve a cargar el gdm y se queda otra vez con la pantalla del login. Lo soluciono borrando su home y cuando intentan acceder nuevamente no hay problema ninguno (hasta que inicia sesión unos días después).

He mirado el fichero .xsession-errors de los usuarios a los que les pasa esto y este es su contenido:

```


    /etc/gdm/Xsession: Beginning session setup…
    Setting IM through im-switch for locale=es_ES.
    Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
    GNOME_KEYRING_SOCKET=/tmp/keyring-XvamQ6/socket
    SSH_AUTH_SOCK=/tmp/keyring-XvamQ6/socket.ssh
    GNOME_KEYRING_PID=1690

    (gnome-settings-daemon:1688): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL’ failed
    Unable to find a synaptics device.
    Checking for Xgl: not present.
    xset q doesn’t reveal the location of the log file. Using fallback /var/log/Xorg.0.log
    No whitelisted driver found
    aborting and using fallback: /usr/bin/metacity
    Advertencia del gestor de ventanas: Ocurrió un error al leer el archivo de sesión guardado /home/alumnos/4ESO/hovik/.config/metacity/sessions/1044222046c0e7bca7125985454573561100000016230025.ms: Ha ocurrido un error al abrir el archivo «/home/alumnos/4ESO/hovik/.config/metacity/sessions/1044222046c0e7bca7125985454573561100000016230025.ms»:·No existe el fichero ó directorio
    No se puede abrir el visor:
    Ejecute «gnome-panel –help» para ver una lista completa de las opciones de línea de órdenes.
    gnome-session: Fatal IO error 11 (Recurso temporalmente no disponible) on X server :0.0.
    gnome-settings-daemon: Fatal IO error 104 (Conexión reiniciada por el par) on X server :0.0.
    Advertencia del gestor de ventanas: Error fatal de E/S 11 (Recurso temporalmente no disponible) en la pantalla «:0.0».


```

¿Alguna idea?

---

### Post by electronpositivo on 2010-02-15
Rescato este thread para comunicaros que después de mucho tiempo investigando, he dado con el origen del problema.

Se trata del fichero /home/usuarioactual/.config/monitor.xml

De momento, simplemente eliminando dicho fichero los usuarios que tenían problemas están pudiendo acceder perfectamente.

Lo que no termino de entender es el motivo por el que hace que se reinicie el gdm dependiendo de las resoluciones que tenga.

Con este contenido, funciona bien:
```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1280</width>
          <height>960</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
</monitors>
```

Pero si el width y el height cambian a otros valores (tras cambiar la resolución en Sistema->Preferencias->Pantalla), al cerrar la sesión e intentar acceder de nuevo, se reinicia el gdm.

Se os ocurre alguna forma de solucionarlo sin tener que borrar cada vez el fichero .monitor.xml

Gracias

---

