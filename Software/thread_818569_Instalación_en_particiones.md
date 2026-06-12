---
title: "Instalación en particiones"
date: 2008-06-04
forum: Software
---

### Post by fgl82 on 2008-06-04
Hola, una duda de principiante:

cuando usaba Windows e instalaba programas, les decia "che vo' fiera, andate al D:\" o "no, no, a ver que hacemo' papá, qué te pensá', vo' te va' al C:\!!!"

Al pasar a Linux, me surgió la duda de si la instalación de los programas en distintas particiones es posible dado que, en general, o los instalo automáticamente desde el "add/remove" o con el apt-get install, no existiendo en ninguno de los dos casos (al menos aparentemente, no investigué demasiado) la opción de indicarle a la aplicación dónde quiero que se instale.

Desde ya, muchas gracias.

¡Saludos!

---

### Post by faktorqm on 2008-06-04
Todos se instalan en /usr. La cosa es que para hacer eso por ejemplo, tendrias que agregar el path nuevo a la variable que use el sistema (que no se cual es) para que si haces desde cualquier posicion en el arbol de directorios "nombre_programa" no te diga que no lo encuentra, y si o si tengas que ir al directorio donde lo instalaste y hagas "./nombre_programa". Si te gusta digamos o tenes la necesidad de instalar programas que oupen mucho espacio, capaz te convendria mas hacerte una particion aparte, montar el / en una de 2gb, el /home en la que tenes ahora y el /usr en una particion de 30gb por ejemplo. (no te olvides del swap xD). Salu2!

---

### Post by fgl82 on 2008-06-04
ok gracias, creo que entiendo, o sea que los únicos directorios del sistema que deberían crecer serían el usr y el home, ¿es así?

---

### Post by Mister X on 2008-06-04
Es un poco mas complejo que eso, hay un estandar (FHS) que define la estructura de directorios en los sistemas linux, pegale una leida y te va a aclarar todo el panorama.

[http://es.wikipedia.org/wiki/Jerarqu%C3%ADa_de_directorios_sistemas_tipo_UNIX](http://es.wikipedia.org/wiki/Jerarqu%C3%ADa_de_directorios_sistemas_tipo_UNIX)

---

### Post by fgl82 on 2008-06-04
ok me fijo...

---

