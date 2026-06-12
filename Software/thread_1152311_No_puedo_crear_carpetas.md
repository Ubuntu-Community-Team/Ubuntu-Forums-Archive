---
title: "No puedo crear carpetas"
date: 2009-05-07
forum: Software
---

### Post by cor_stellae on 2009-05-07
Hola:

Luego de mucho batallar para tener privilegios de copia de archivos en mi disco duro, ahora que ya logré darle privilegios con nautilus, no me deja crear carpetas. ¿Alguien sabe cómo solucionar esto?

---

### Post by cor_stellae on 2009-05-07
Ya se resolvió. Parece que el disco padeció de locura temporal, pero reinicié y todo volvió a la calma...

---

### Post by infernus92 on 2009-05-07
un consejo antes de postear... y si te pasa algo parecido de nuevo...
reinicia... si bien normalmente no hace falta... hay casos en los que si...
y si necesitas hacer algo con privilegios de root de forma grafica (muchos lo saben porque es algo muy facil y comun), tocas alt+F2 (ejecutar aplicacion) pone "gksu" (sin las comillas) y te aparece una ventana de ejecutar programas, pero esta vez te deja elegir con que usuario queres iniciar esa aplicacion (por defecto root), escribis el nombre de la aplicacion (por ejemplo nautilus) y te va a apedir la constraseña. La escribis y te inicia el programa con TODOS los permisos...
algunas veces me sirvio bastante... y espero que te sirva si pasa algo asi de nuevo...

Saludos

PD: esto no es hardware... es software...
como dice Hei Ku, hardware es todo lo que se puede patear

---

### Post by staar on 2009-05-07
> **cor_stellae said:**
> Ya se resolvió. Parece que el disco padeció de locura temporal, pero reinicié y todo volvió a la calma...

jajaja, no fue locura temporal, pasa que estuviste modificando el fstab, y para aplicar los cambios a ese archivo, hay que volver a montar todo, o reiniciar (que vendría siendo lo mismo :-P ya que al reiniciar montas todo de nuevo)

saludos

---

### Post by cor_stellae on 2009-05-08
Je je je je... Bueno, ya logré hacerlo con esa partición, y quedan dos en camino. He pasado toda la noche con la segunda partición que pasé a ext3 y le ha pasado de todo, incluyendo que en fstab aparece como ntsf...!!!! La logro montar, tras muchos esfuerzos y cuando reinicio... no me deja abrirla con cualquier excusa... (ni tan cualquiera: o indica que no tiene soporte ntfs o que la línea 18 del fstab es incorrecta). El pysdm no la logra ver bien y el montaje tengo que hacerlo por medio de Terminal...

Lo único que puedo decir es que estoy cerquita de aprenderme los comandos, pero en fin... en esas seguiré. Ya logré que la segunda partición esté montada y con privilegios de copia, pero todavía no estoy plenamente segura de si la cargará cuando se reinicie. Si no lo hace... me verán de nuevo pidiendo gritos de socorro. Por ahora, buenas noches y gracias por otro día más de apoyo moral y técnico en mis primeros pasos de Ubuntu.

---

