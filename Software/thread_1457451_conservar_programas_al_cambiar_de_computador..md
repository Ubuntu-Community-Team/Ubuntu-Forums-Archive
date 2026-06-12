---
title: "conservar programas al cambiar de computador."
date: 2010-04-18
forum: Software
---

### Post by panchoponcho on 2010-04-18
Hola a todos, bueno, mi problema es el siguiente:

tenia la carpeta home con muchos programas (como por ejemplo mathematica) en un compudador y instale ubuntu en otro computador pero necesitaba tener todos los programas que siempre tube sin instalar uno por uno. y leyendo en internet me entere que si copiaba todo lo de la carpeta home antigua en mi nuevo computador todo seguiria como antes. la copie y el fondo de pantalla y esas cosas se cambiaron, pero los programas que antes tenia no. como vlc y mathematica. aparecen en la carpeta home, pero al escribir "mathematica" o "vlc" en consola me dice que el programa no esta.

¿que estoy haciendo mal?

agradesco mucho las respuestas.

saludos,

Francisco.

---

### Post by bichopro on 2010-04-18
Cuando copias el home copias las configuraciones de los programas pero no el programa, por eso cuando borras una carpeta y ejecutas el programa parte de cero, como recién instalado.

Te recomiendo que ocupes este comando: > sudo dpkg --get-selections > installed-software
Eso creara un archivo con todas las aplicaciones instaladas separas por un espacio.

Luego te queda en el pc nuevo agregar los repositorios que tienes el en ubuntu anterior, por que si no no podra bajar todos los paquetes ya para terminar abrir una consola y colocar: > sudo apt-get install seguido de las lista de programas. Asi instalara todo lo que tenias en el pc viejo, y como ya tendrás copiado las carpetas de configuración volverá a estar como antes.

---

