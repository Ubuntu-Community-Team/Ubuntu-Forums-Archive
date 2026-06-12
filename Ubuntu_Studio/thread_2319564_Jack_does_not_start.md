---
title: "Jack does not start"
date: 2016-04-05
forum: Ubuntu Studio
---

### Post by ajotatxe on 2016-04-05
Hello, I have just installed **UbuntuStudio 14.04** in my [B]laptop ASUS X554L.

[/B]Sound works (youtube, for example), but jack does not. When I press Start button in QjackCtl I get this (I appologize, some messages are in Spanish, I can translate them if needed):

```
 19:34:30.775 Patchbay desactivada.

19:34:30.778 Reiniciar estadísticas.
19:34:30.783 Cambios en las conexiones ALSA.
19:34:30.796 D-BUS: Disponible (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started
19:34:30.804 Cambió el gráfico de conexiones ALSA.
(qjackctl:2500): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2500): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
19:34:47.682 D-BUS: El servidor JACK no puede iniciarse. Disculpa
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:2500): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2500): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
Tue Apr  5 19:34:47 2016: Starting jack server...
Tue Apr  5 19:34:47 2016: JACK server starting in realtime mode with priority 10
Tue Apr  5 19:34:47 2016: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Apr  5 19:34:47 2016: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Apr  5 19:34:47 2016: ERROR: Audio device hw:0 cannot be acquired...
Tue Apr  5 19:34:47 2016: ERROR: Cannot initialize driver
Tue Apr  5 19:34:47 2016: ERROR: JackServer::Open failed with -1
Tue Apr  5 19:34:47 2016: ERROR: Failed to open server
Tue Apr  5 19:34:49 2016: Saving settings to "/home/ajh/.config/jack/conf.xml" ...
19:34:53.720 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started
19:34:58.848 D-BUS: El servidor JACK no puede iniciarse. Disculpa
Tue Apr  5 19:34:58 2016: Starting jack server...
Tue Apr  5 19:34:58 2016: JACK server starting in realtime mode with priority 10
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started
Tue Apr  5 19:34:58 2016: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Apr  5 19:34:58 2016: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Tue Apr  5 19:34:58 2016: ERROR: Audio device hw:0 cannot be acquired...
Tue Apr  5 19:34:58 2016: ERROR: Cannot initialize driver

Tue Apr  5 19:34:58 2016: ERROR: JackServer::Open failed with -1
Tue Apr  5 19:34:58 2016: ERROR: Failed to open server
Tue Apr  5 19:35:00 2016: Saving settings to "/home/ajh/.config/jack/conf.xml" ...
19:35:08.870 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
Cannot connect to server socket err = No existe el archivo o el directorio
Cannot connect to server request channel
jack server is not running or cannot be started
```

---

