---
title: "Firefox falla y se reinicia la seción gnome"
date: 2010-08-10
forum: Software
---

### Post by Andyvec on 2010-08-10
Escribo a la comunidad de Ubuntu para ver si alguien tiene idea que puede estar pasando, la verdad que este es un problema que me molesta bastante.

La cuestión es que cuando estay usando Firefox, teniendo tres o cuatro pestañas abiertas, algún programa liviano como Gedit o la terminal también abiertos e ingreso ingreso algo en un cuadro de texto de Firefox y presiono ENTER, de repente ce cierra la sesión Gnome y me aparece la ventana para elegir usuario de GDM.

Es algo al azar, no siempre pasa, pero siempre que pasó fue al apretar ENTER luego de haber escrito algo en un cuadro de texto en Internet. Me pasa por ejemplo al ingresar mi contraseña para entrar en Gmail o por ejemplo cuando busco algo Google, incluso si lo hago mediante el buscador que se encuentro a la derecha de la barra de direcciones.

La verdad es que es algo que me molesta bastante, última vez (hace unos minutos) perdí un mail importante que estaba redactando en Gmail en otra pestaña y parte de un trabajo que estaba haciendo en Gedit mientras buscaba algo en Google (Además se tampoco se guardó en borradores de Gmail :confused:, mala suerte....).

Es algo raro, si alguien tiene alguna idea de que puede ser esto por favor chifle.

Saludos y gracias

EDITO:
Estoy usando 10.04 actualizado al día
Tengo activado los repositorios estables de X updates y uso los drivers Nvidia

---

### Post by Andyvec on 2010-08-13
Disculpen si soy molesto. Pero el tema es que reinstale Lucid y nuevamente me encuentro con el mismo problema.

Nuevamente hay reinicios cuando presiono ENTER luego de escribir algo en algún formulario de Firefox.

No estoy seguro de que siempre sea así, pero las últimas veces que me pasó esto siempre estaba usando conexiones encriptadas con SSL mediante HTTPS

Esta ver la único que intalé de Lucid fue DockbarX, el plugin Flash, MPlayer, WINE, los extras restringidos, Dropbox y el paquete de iconos Faenza, todo desde los repositorios respectivos.

Por lo que me indican los sensores las temperaturas están bien, y el uso de CPU y memoria es muy bajo (lo normal), además intenté reabrir Windows 7 y usar un buen rato Firefox y todo funcionó bien.

¿Alguien tiene alguna idea? :confused:

---

### Post by pablo.s on 2010-08-13
Hola: Te sugiero hacer un procedimiento para
descartar factores que puedan estar provocando
el cierre de sesion.

1) _Para descartar a Firefox:_ Sugiero bajar
la [beta 3 del sitio oficial]("http://www.mozilla.com/es-ES/firefox/all-beta.html") y descomprimirla.
Luego abres una terminal, y vas hasta el 
directorio donde esta descomprimido el archivo
y ejecutarlo con ```
./firefox
```
Al estar siendo ejecutado desde terminal Firefox
va a dar mensajes de error, aunque si reinicia la
sesion se perderan.

2) Asimismo para descartar a GNOME se puede probar
el mismo procedimiento con las dos versiones de
Firefox aunque desde otro DM (por ejemplo desde OpenBox
o LXDE).
Saludos

---

### Post by guillermolisi on 2010-08-13
> **pablo.s said:**
> 
1) _Para descartar a Firefox:_ Sugiero bajar
la [beta 3 del sitio oficial]("http://www.mozilla.com/es-ES/firefox/all-beta.html") ......
Beta 4 en realidad ?

---

