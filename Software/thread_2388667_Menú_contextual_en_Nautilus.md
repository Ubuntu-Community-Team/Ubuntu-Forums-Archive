---
title: "Menú contextual en Nautilus"
date: 2018-04-05
forum: Software
---

### Post by EGKaltenmeier on 2018-04-05
Hola a todos, saludos.
  Recientemente actualicé mi distribución de  16.04 LTS a 17.10, y ahora no funciona el menú contextual cuando oprimo  la tecla "Menú" del teclado, teniendo seleccionado un elemento en  Nautilus (en otras aplicaciones funciona correctamente).
  Intenté  buscando personalizar algún atajo de teclado, pero no lo he logrado.  Aclaro que probé usando (Ctrl + F10), (Shift + F10) y (Super + F10),  pero ninguna me dió resultado.
  Sólo puedo ver las opciones del  archivo si navego con el cursor hasta seleccionar el elemento (no  funciona tampoco cuando lo selecciono navegando con las flechas del  teclado) y abriendo recién allí el menú contextual, pero con el botón  derecho del touchpad.
  Si Nautilus ha perdido esa opción, igualmente  me interesa establecer algún atajo de teclado para poder seguir usando  la tecla "Menú". Esto no sé cómo personalizarlo: me ayudaría si me  dijeran cómo debo configurar el comando de desplegar el menú contextual  de un elemento seleccionado.
  Información técnica: SO Ubuntu 17.10  64bits, versión de GNOME 3.26.2, versión de Nautilus (creo) 3.26.0.  Equipo: Lenovo G470 (del año 2012 pero a la que le quedan varias  batallas por delante...)
  Desde ya, muchas gracias! Saludos!

---

### Post by xwizard2 on 2018-04-06
Has probado iniciar nautilus de símbolo de sistema? Si no, prueba lo y ve si hay algunos errores.

---

### Post by EGKaltenmeier on 2018-04-06
user@laptop:~$ sudo nautilus
[sudo] password for user: 
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: No se pudo conectar: Conexión rehusada

(nautilus:2893): Gtk-WARNING **: cannot open display: :0

---

### Post by xwizard2 on 2018-04-07
Porqué usas "sudo"? Pensaba que tienes problema con utilizar nautilus en tu cuenta. Unfortunadamente mi portatil no tiene "menú" y no lo puedo probar aquí.

---

### Post by EGKaltenmeier on 2018-04-07
Tal vez no he entendido por qué debía abrirlo con símbolo de sistema.

---

