---
title: "Problemas con cuentas de usuario."
date: 2009-08-23
forum: Software
---

### Post by morefeo on 2009-08-23
Buenas, verán: en la cuenta que creé mientras se instalaba ubuntu va todo bien, me reconoce la gráfica, tengo aceleación etc, pero si creo un usuario y me voy a sistema > preferencias > apariencia e intento activar los efectos, me aparece el cuadro de que busca los drivers, pero acaba diciéndome que no se han podido activar los efectos.

No sé por que pasa, si en mi cuenta va perfectamente, ¿porqué si creo otro usuario no?

Uso Ubuntu 9.04.

---

### Post by ceramicm on 2009-08-23
¿Has obtenido drivers grafícos restringidos? Pienso que es necesario que tengas drivers grafícos restringidos antés que pueda usar los efectos grafícos. También, ¿sabes si tu computadora puede apoyar efectos grafícos? ¿Cual tipo de sistema de grafícos usas (como NVIDIA o ATI o Intel...)?

Lo siento, español no es mi lengua primera.

---

### Post by morefeo on 2009-08-23
Mi computadora usa los drivers graficos open source (ATI radeon 9250), y soporta bien los efectos gráficos, incluso compizfusion. En mi cuenta principal todo funciona bien, es en otros usuarios donde encuentro el problema.

---

### Post by ceramicm on 2009-08-23
Ah, comprendo ahora. Desafortunadamente, no conozco este momento a ninguna solución. Una busqueda de Google no me dio nada tampoco. ¿Has tratado de empezar compizfusion por «compiz --replace» en terminal en lugar de sistema > preferencias > apariencia? ¿Recibes algunos errores cuando usas el command en el terminal? ¿Puedes darme el texto exacto del mensaje de error que recibes cuando usas sistema > preferencias > apariencia? Muchas gracias y, también, lo siento por mi español.

Una cosa más: ¿Estás usando los paquetes oficiales o paquetes de un PPA?

---

### Post by pablo.s on 2009-08-23
En el menú Sistema ->
Administración -> Usuarios
y Grupos se manejan los
permisos de los usuarios.
Desbloquealo, fijate en el 
usuario que hayas creado y
constata la solapa "Privilegios
de Usuario" que tenga el
permiso para utilizar la aceleración
3D. Si no es así, autorizalo.

---

### Post by morefeo on 2009-08-24
> **ceramicm said:**
> Ah, comprendo ahora. Desafortunadamente, no conozco este momento a ninguna solución. Una busqueda de Google no me dio nada tampoco. ¿Has tratado de empezar compizfusion por «compiz --replace» en terminal en lugar de sistema > preferencias > apariencia? ¿Recibes algunos errores cuando usas el command en el terminal? ¿Puedes darme el texto exacto del mensaje de error que recibes cuando usas sistema > preferencias > apariencia? Muchas gracias y, también, lo siento por mi español.

Una cosa más: ¿Estás usando los paquetes oficiales o paquetes de un PPA?

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 


> **pablo.s said:**
> En el menú Sistema ->
Administración -> Usuarios
y Grupos se manejan los
permisos de los usuarios.
Desbloquealo, fijate en el 
usuario que hayas creado y
constata la solapa "Privilegios
de Usuario" que tenga el
permiso para utilizar la aceleración
3D. Si no es así, autorizalo.

Si que tiene el permiso.

Ahora nisiquiera la cuenta principal puede activar los efectos =S es muy raro ya que aceleración 3d sé que tengo (gran resolución, glxinfo devolviéndome "Direct Rendering: Yes".

---

### Post by morefeo on 2009-08-27
Bump! Tuve que formatear dado que por tocar los drivers las texturas no estaban siendo renderizadas bien, así que mi usuario vuelve a tener aceleracion 3d, sin embargo sigo sin poder activar los efectos de escritorio con otro usuario.

---

### Post by morefeo on 2009-08-31
Hola?

---

