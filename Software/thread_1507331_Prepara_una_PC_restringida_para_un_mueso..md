---
title: "Prepara una PC restringida para un mueso."
date: 2010-06-11
forum: Software
---

### Post by daggaz on 2010-06-11
Hola.
Estoy trabajando en una exposicón en un museo y queremos poner una computadora para que las personas navegen por un sitio de intenet de proyecto. El cual es un CMS (como un blog) con información y algo de contenido multimedia que se actualiza cada semana.

La cosa es que queríamos que de preferencia no se metieran a ningún otro sitio más que la del proyecto y de preferencia que no pudieran hacer nada más en la PC. Y desde luego todo lo queremos hacer en Ubuntu. Un inconveniente es que los trabajadores del museo serán los que se encarguen de iniciar la PC todos los días y no podemos pedirles que hagan mucho. Nisiquiera que memoricen una contraseña así que la entrada al sistema debe ser automática.

Se me ocurría que podía programar la inciaición del navegador (Google Chrome en este caso, pero si es necesario podemos usar Firefox) en las aplicaciónes que se arrancan al inicio, y agregarle algo al comando para que el navegador se hiciera en pantalla completa al iniciar (como cuando uno presiona F11) Pero no sé cómo hacer eso.
Igual podría buscar en las preferencias algo para bloquear la navegación a otras páginas (nunca lo he hecho). Luego borrar los paneles y solo dejar un pequeño Dock con el menú de apagado y el lanzador del navegador en pantalla completa.
Otra opción era quizás hacer un usuario con permisos restringidos...
En fin, lo que necesito son algunos consejos y un poco de orientación.


Gracias

---

### Post by alfplayer on 2010-06-11
Se puede hacer con Pessulus, y si es necesario se puede usar con un proxy como Squid para permitir solo el dominio del CMS.

---

### Post by juancarlospaco on 2010-06-11
**echo /usr/share/gdm/guest-session/guest-session-launch >> $HOME/.profile**

Ponele el login automatico en el GDM de gnome, 
con eso la PC queda freezada, todo cambio se borra al reiniciar.


si unicamente queres el dominio del sitio, podes usar directamente el **/etc/hosts**

---

### Post by alfplayer on 2010-06-12
> **juancarlospaco said:**
> si unicamente queres el dominio del sitio, podes usar directamente el **/etc/hosts**

Esto solo no bloquea direcciones IP, que puede ser un problema.

Usar solo bloqueo por dirección IP puede ser insuficiente también porque no se bloquean virtual hosts.

---

### Post by daggaz on 2010-06-13
No me queda muy claro. ¿Debo hacer el archivo *.profile*? ¿Se genera a partir de lo que tengo ahora?
Probaré con Pessulus y lo de la Proxi. Nunca he manejado una, pero siempre hay una primera vez...

---

