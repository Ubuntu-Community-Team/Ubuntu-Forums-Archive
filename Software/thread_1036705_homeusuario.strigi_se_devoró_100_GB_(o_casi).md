---
title: "/home/usuario/.strigi se devoró 100 GB (o casi)"
date: 2009-01-11
forum: Software
---

### Post by mecdem on 2009-01-11
Mi sistema es Kubuntu 8.04.

La partición / escenario del drama es la que indico en el título.&#8232;
Hasta antes de lo que expicaré, ocupada en bastante menos de la mitad de su capacidad total de 100 GB.&#8232;&#8232;

Primer síntoma extraño: un mensaje que anuncia&#8232; "Tiene poco espacio de disco en su partición personal (actualmente, 0 % libre): ¿desea ejecutar Konqueror para iberar algo de espacio de disco y corregir el problema?". Cliqueo en Cancelar.
&#8232;Creo que apareció por primera vez cuando intenté una actualización de paquetes. Después aparecía en cualquier momento.

&#8232;&#8232;Precisamente en esos días había aprendido a usar el aMule y como niño con juguete nuevo, estaba "bajando todo". "Todo" son cinco películas y algunos e-libros.
&#8232;Caramba: ¿lo que bajo ocupa tanto que ocupó toda la partición? No, no podía ser eso. No obstante me puse a pasar archivos y directorios grandes a un disco removible.

&#8232;Seleccionando todos los directorios "visibles" dentro de /home/usuario compruebo que ocupan poco menos de 2GB, pero /usuario ocupa 98 GB.
&#8232;El aviso de poco espacio no aparece ahora en cualquier momento, pero si intento conectar el aMule aparece de vuelta informando que actualmente tengo el 4 % libre.

&#8232;&#8232;Si los directorios "visibles" de /home/usuario ocupan menos de 2GB pero /usuario pesa 98 GB, el problema está en los ocultos. Busco y encuentro que el problema está en .strigi, con un peso de 82,9 GB, y -dentro de .strigi- clucene ocupa 82,6 GB.
&#8232;Dentro de clucene hay más de 150 archivos generados a partir del 04.05.2009, fecha en que en algún lugar del menú principal hice clic sobre Strigi y puso un ícono en la barra de sistema. Clic sobre ese ícono habilitaba una pequeña ventanita para ingresar algún dato. Me pareció que era un buscador de imágenes. No volví a usarlo y hoy eliminé el ícono de la barra de sistema.

&#8232;&#8232;Describo alguno de los archivos dentro de /home/usuario/.strigi/clucene:

&#8232;&#8232;_9sxl.tmp - 356 MB - Este archivo encabeza la lista ordenada por fecha.&#8232;&#8232;

_8r3mu.f* -  Hay 85 archivos con esta denominación - Todos son "documento simple de texto" y se han generado a la misma hora - El nombre finaliza con un número desde 0 hasta 85 - Todos son de 988,8 KB
&#8232;&#8232;_8r3mu.fdt - Descripción: desconocido - 2,0 GB&#8232;
_8r3mu.fdx - Descripción: desconocido - 7,7 MB&#8232;
_8r3mu.tmp - Descripción: doc.simple de texto - 555,8 MB&#8232;&#8232;

_6qrek.fdt - Descripción: desconocido - 16,1 GB&#8232;
_6qrek.fdx - Descripción: desconocido - 46,3 MB&#8232;&#8232;
_7es55.cfs - Descripción: desconocido - 2,5 GB

&#8232;&#8232;Hay 18 archivos que pesan entre 1,8 y 16,1 GB&#8232;&#8232;Se siguen generando archivos. El último es&#8232;_9fbz0.fdt  - Descripción: desconocido - 14,6 GB
&#8232;&#8232;Si hago una búsqueda en el gestor Synaptic, de 12 paquetes que aluden a strigi aparece instalado sólo libstrigiqtdbusclient0, con un tamaño de 152 kB.&#8232;
Búsqueda igual con gestor Adept, muestra 16 paquetes que aluden a strigi, apareciendo instalado el mismo libstrigiqtdbusclient0 más libstreamanalyzer y libstreams0.

&#8232;&#8232;Creo que están todos los datos para la consulta.
&#8232;No soy informática, así que he puesto todo lo que me ha parecido que puede orientar una respuesta. Disculpar si faltan o sobran datos.

&#8232;&#8232;Las preguntas son:
&#8232;&#8232;La primera: ¿puedo desinstalar esos paquetes?
&#8232;La segunda: ¿puedo eliminar los directorios y archivos de .strigi?
&#8232;&#8232;La tercera sería ¿por qué ocurrió esto? pero quizás esa sea una de esas preguntas que  [-X  no deben hacerse...

&#8232;&#8232;Gracias por la paciencia para leer esto y gracias anticipadas por la respuesta.
&#8232;Saludos.&#8232;

---

### Post by pol666 on 2009-01-11
mmm strigi es algo Tracker de gnome? para indexar no cierto? parece que se lleno de datos irracionalmente, No te fies en mi palabra, pero si fuera vos hago un purge de strigi asi se borra todo eso,

---

### Post by joe74 on 2009-01-11
Simplemente borra la carpeta .strigi

Por lo general lo que tienes en carpetas escondidas son configuraciones y esas cosas. En caso que se necesite, la carpeta .strigi volvera a ser creada por la aplicacion que la usa. Como te dijo pol666 antes, puede ser informacion irracional ocupando tu espacio libre o solo marcandolo como usado.

Suerte!

---

### Post by Hei Ku on 2009-01-11
Strigi es un indexador. Algun error o problema de configuracion hizo que se vaya de mambo. Borra esa carpeta nomas.

---

### Post by mecdem on 2009-01-11
Estimados pol666, joe74 y HeiKu:
[CENTER]¡¡.STRIGI BORRADO!![/CENTER]
___________________

Les cuento: ¡¡al fin la consola me sirvió para algo!! :D

Bueno, bueno, no pongan esas caras... 
Yo digo: si existe el entorno gráfico, tan bonito, tan clic-clic-clic... ¿hay necesidad de andar todo el tiempo escribiendo palabras cabalísticas sobre tableros mágicos? ¿eh?
'Tá bien, parece que un poco de falta hace.

Por supuesto que como buena usuaria "rasa" intenté resolver todo con el GUI. ¡Jua! Jamás iba a borrar así archivos de 16 GB.
Me resigné. Entré despacito a la consola, me loguié como root, me aseguré de estar parada en el lugar adecuado, y tragando saliva me mandé con el rm -rv .strigi ¡enter!
Para mí fue algo así como atención-apunten-fuego.
Y se puso a borrar nomás.

Como le puse la "-v" mis angustias se iban calmando a medida que veía confirmado  que estaba borrando strigi y no formateando la partición. Tardó bastante, se detenía por momentos, seguramente cuando estaba aplicando el golpe de furca a algún gordo grandote.

Les cuento esto para transmitir a los gurúes informáticos los padeceres a que está expuesta una pooooooobre usuaria no informática en estas aventuras linuxeras. Seguro que ya lo saben, pero bueno es una visión más.

No hay duda: con Win era todo más fácil. Siguiente-siguiente-siguiente, y si no va, a formatear y a otra cosa, qué embromar... 
:tongue:

Software libre es como esos amigos por los que uno siente mucho cariño, pero cada tanto se pregunta por qué diablos los quiere ¿no?
___________________

UNA ÚLTIMA PREGUNTA: 

En otro equipo tengo el mismo sistema operativo y entre los ocultos en /home/usuario no hay ningún .strigi, por lo que conjeturo que no es necesario.

En la consulta dije que había un paquete según Synaptic y tres según Adept vinculados a strigi.

[CENTER]¿Los puedo desinstalar?[/CENTER]

No quisiera dejar la puerta abierta para que este díscolo se ponga otra vez a hacer de las suyas.
___________________

Gente, muchísimas gracias por la ayuda.
Ya pinché para cada uno de ustedes el iconito de decir

[CENTER]¡GRACIAS![/CENTER]

---

### Post by Hei Ku on 2009-01-11
Desinstalalo nomas, sin culpas. 

No es algo esencial del sistema operativo, y la verdad es que todavía le falta un golpe de horno, y ademas va a ser reemplazado por otro sistema. :D

---

### Post by mecdem on 2009-01-11
> **Hei Ku said:**
> Desinstalalo nomas, sin culpas. 

No es algo esencial del sistema operativo, y la verdad es que todavía le falta un golpe de horno, y ademas va a ser reemplazado por otro sistema. :D

Gracias, HeiKu.
Expulsaré a ese insolente que se mete a hacer cosas sin consultar al usuario.
Va contra los principios del softlibre...

):P

Consulta concluida, problema resuelto.
Saludos.

---

