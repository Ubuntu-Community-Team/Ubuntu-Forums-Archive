---
title: "Configurar paneles de GNOME"
date: 2010-05-23
forum: Software
---

### Post by Hadso on 2010-05-23
Hola gente. Gracias por pasar a leer esta pregunta. 
Sucede que tengo instalado Ubuntu 10.04 y GNOME 2.30.0.
Ahora bien, quiero configurar los paneles, y no puedo. Cuando click con el botón derecho en el panel, aparecen las opciones de "Ayuda" y "Acerca de", pero nada más. Si lo hago sobre algún lanzador, sólo aparece la opción "Lanzar". 
He buscado información al respecto en internet, pero no he encontrado más que strings para borrar todos los paneles y "restaurar" la configuración originaria. Antes de llegar a ese extremos quería saber si alguien me podría dar una mano por este medio. También me gustaría saber de dónde surgió el problema, dado que no he metido mano. 
Muchas gracias. 
Saludos,

---

### Post by DrKenobi on 2010-05-23
Hola, fijate si te sirve "Sistema-->Preferencias-->Menu Principal"

---

### Post by Hadso on 2010-05-23
mmmm... no, eso no me ha dado solución. Gracias de todas maneras.

---

### Post by eliux on 2010-05-26
Hola, lo unico que se me ocurre es que restaures la configuracion por defecto de gnome y sus paneles, para ello ejecutate este comando en un Terminal

[COLOR=darkred]sudo gconftool-2  --recursive-unset /apps/panel[/COLOR]

Si no funciona con lo anterior podes probar esto: (ojo que podes perder info con los siguientes pasos)

La otra opcion es que te crees un segundo usuario y proba ahi a ver si anda bien, y la ultima opcion es borra todo el contenido del usuario "ATENCION BACKUPEATE TODA LA INFO MIRA QUE ESTO TE BORRA TODO EL CONTENIDO DE LA CARPETA DE TU USUARIO"(siempre tenete un usuario configurado opcional y backupeate toda la configuracion a otra carpeta que no sea dentro de tu usuario por borrar)

Ejemplo: cambia "TUUSUARIO" por el nombre de tu usuario

sudo rm -R /home/TUUSUARIO

al iniciar sesion nuevamente restaura todo, creo... =D

---

### Post by guillermolisi on 2010-05-26
> **eliux said:**
> Hola, lo unico que se me ocurre es que restaures la configuracion por defecto de gnome y sus paneles, para ello ejecutate este comando en un Terminal

[COLOR=darkred]sudo gconftool-2  --recursive-unset /apps/panel[/COLOR]

Si no funciona con lo anterior podes probar esto: (ojo que podes perder info con los siguientes pasos)

La otra opcion es que te crees un segundo usuario y proba ahi a ver si anda bien, y la ultima opcion es borra todo el contenido del usuario "ATENCION BACKUPEATE TODA LA INFO MIRA QUE ESTO TE BORRA TODO EL CONTENIDO DE LA CARPETA DE TU USUARIO"(siempre tenete un usuario configurado opcional y backupeate toda la configuracion a otra carpeta que no sea dentro de tu usuario por borrar)

Ejemplo: cambia "TUUSUARIO" por el nombre de tu usuario

sudo rm -R /home/TUUSUARIO

al iniciar sesion nuevamente restaura todo, creo... =D
Una forma menos violenta de probar esto es creando un usuario nuevo.

---

### Post by Hadso on 2010-06-13
> **eliux said:**
> Hola, lo unico que se me ocurre es que restaures la configuracion por defecto de gnome y sus paneles, para ello ejecutate este comando en un Terminal

[COLOR=darkred]sudo gconftool-2  --recursive-unset /apps/panel[/COLOR]

Si no funciona con lo anterior podes probar esto: (ojo que podes perder info con los siguientes pasos)

La otra opcion es que te crees un segundo usuario y proba ahi a ver si anda bien, y la ultima opcion es borra todo el contenido del usuario "ATENCION BACKUPEATE TODA LA INFO MIRA QUE ESTO TE BORRA TODO EL CONTENIDO DE LA CARPETA DE TU USUARIO"(siempre tenete un usuario configurado opcional y backupeate toda la configuracion a otra carpeta que no sea dentro de tu usuario por borrar)

Ejemplo: cambia "TUUSUARIO" por el nombre de tu usuario

sudo rm -R /home/TUUSUARIO

al iniciar sesion nuevamente restaura todo, creo... =D
Hice tal cual como me dijiste, pero no me ha dado resultado. 
Gracias de todas maneras. 
Saludos,

---

### Post by Hadso on 2010-06-13
> **Hadso said:**
> Hice tal cual como me dijiste, pero no me ha dado resultado. 
Gracias de todas maneras. 
Saludos,
Claro que llegué al extremo de borrar todo el /home. Me parece una medida excesiva, todo lo que quiero hacer, es poner en su lugar un par de paneles.

---

