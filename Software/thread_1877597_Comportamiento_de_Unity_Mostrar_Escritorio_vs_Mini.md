---
title: "Comportamiento de Unity Mostrar Escritorio vs Minimizar"
date: 2011-11-08
forum: Software
---

### Post by granjero on 2011-11-08
Hola ubunteros, instalé 11.10 y probé gnome3 para compararlo con unity y me quedé con unity. 
Ahora tengo una instalación limpia de 11.10 en mi dell inspiron 1440.

La consulta. Cuando muestro el escritorio, ya sea con crtl+atl+d o con el gesto de monitor que asigné en compiz (me gusta la esquina superior izquierda),y luego hago click en el icono de unity de una aplicación cualquiera para levantarla me levanta todo el resto de las aplicaciones. 

Esto no sucede si las he minimizado una por una con el botón correspondiente de la ventana o con el atajo que le asigné en compiz (super + flecha abajo) y llamo una aplicación sólo esa se restaura.

Antes en 10.04 esto no sucedía. Minimizaba con el atajo de teclado o el de monitor y cuando llamaba una aplicación desde el dock de gnome-do venía una sola.

Alguna idea de como lograr que al mostrar el escritorio y llamar una aplicación sólo venga la deseada y no todas.

Muchas gracias por su tiempo.

salud!

---

### Post by granjero on 2011-11-15
otro comportamiento que cambió en unity es el plugin "scale" ahora cuando se lo activa, ya sea con ctrl+w (configuración por defecto) o con el atajo de pantalla muestra en la salida todas las ventanas de todos los programas que se están ejecutando. Antes sólo mostraba las ventanas que no estaban minimizadas.

por ejemplo, tengo abiertas 3 terminales, pidgin, evolution y gwibber. 
pidgin y gwibber minimizadas y apreto ctrl+W en me muestra las 6 ventanas en lugar de las 4 no están minimizadas.

¿Hay forma de volver al comportamiento anterior?

salud!

---

### Post by granjero on 2011-11-22
Al final encontré la solución a pura metida de mano.
En el Compiz Settings Manager > Unity Plugin > Switcher hay que destildar la opción "Show minimized windows on switcher"

Adjunto Imgaen.

Ahora el comportamiento es como antes. Lo minimizado no se "eleva" al iniciar scale o al llamar una aplicación minimizada desde el launcher sólo llama a esa.

Salud.

---

