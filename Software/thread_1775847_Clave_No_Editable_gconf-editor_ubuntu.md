---
title: "Clave No Editable gconf-editor ubuntu"
date: 2011-06-05
forum: Software
---

### Post by zalva on 2011-06-05
Ola, tengo un problema, pasa que quise modificar la posición de los  botones de la barra de ventanas y al principio pude pero luego no. Me  explico, lo habia hecho y funcionaba y el problema creo que surgió al  instalar un script para la transparencia RGBA 
([http://www.webupd8.org/2010/05/script-to-fix-panel-for-all-themes-at.html](http://www.webupd8.org/2010/05/script-to-fix-panel-for-all-themes-at.html) e instale sudo python -u theme_bg_patcher2.py)
Creo que todo empezó desde ahí. Luego reinicié y tenía los botones a la  derecha (yo los había puesto a la izquierda). Intenté por gconf-editor,  pero la clave button_layout dice clave no editable; intente poniendo  gksu gconf-editor pero pasa lo mismo. Intente desde la terminal y con  programas y dice: "..No se puede sobreescribir un valor de sólo lectura:  No se puede sobreescribir un valor de sólo lectura: El valor de  «/apps/metacity/general/button_layout» es una fuente sólo de lectura en  la parte superior de su configuración.."

Ayuda porfa, soy nuevo en linux. Em como dato, tendrá que ver los  permisos? Onda como doy permiso de escrituras para estas claves??  Ayudaaa plzz!!
PD. busqué en 'search' y no encontré resultados . PD2. He buscado en más sitios sin encontrar respuesta. 
Saludos!

---

### Post by zalva on 2011-06-05
**Solucionado!** Disculpen las molestias. Les dejo la solución.
Bueno no pasó por cómo yo había pensado: antes había entrado en gconfig-editor y en apps->metacity->general->button_layout había cambiado los parametros (boton secundario) y puse **establecer obligatorio**. Me pidió la clave y yo se la había dado, y sin darme cuenta lo establecí obligatorio.
-Ahora, entré en modo root: **gksudo gconfig-editor** y en Archivo->Abrir nueva ventana 'obligatorios', **desestablecí** (boton secundario) las claves antes establecidas como obligatorio, en este caso button_layout.
Reinicié y listo! :D 

-linux for human beings- (h)

---

### Post by RafaelG on 2011-06-07
Zalva;

Otra Maquina Libre!

---

