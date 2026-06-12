---
title: "Instalación correcta de Ubuntu y Windows en dos particiones"
date: 2009-04-30
forum: Software
---

### Post by cor_stellae on 2009-04-30
¡Hola!

Ayer pasamos varias horas tratando de reparar el Grub de mi sistema y fue imposible (¡gracias, chicos!). Además, aunque se repare, ya detectamos problemas como un exceso de particiones en un disco duro en donde solo deberían haber 3 y lo que el Ubuntu necesite como espacio compartido.

Siendo así las cosas, quiero formatear todo el disco duro para tratar de lograr lo que quería desde el inicio: la partición principal para Ubuntu, una segunda partición para Windows y una tercera partición para datos. Pero puesto que he estado varios días intentando hacer esto, ahora tengo varias preguntas puntuales que no logro responder en ningún tutorial. Les agradezco mucho la ayuda.
[B]
Pregunta 1: tamaño de las particiones[/B]
El disco tiene 160 GB. He leído que las particiones de Ubuntu pueden tener máximo 10 GB, pero soy fan de instalar programas, así que me gusta dejar el disco de arranque con espacio suficiente para no tener falta de espacio para actualizaciones ni problemas de lentitud por no tener suficiente espacio físico para hacer sus operaciones. ¿Cuánto es aconsejable: 15-20-25?

**Pregunta 2: preparación de las particiones**
Mi problema comenzó porque preparé las particiones desde el instalador de Windows. Como resultado, este dejó 8-9 GB sin asignar y cuando el instalador de Ubuntu vio este espacio suelto, hizo fiesta: lo partió en fragmentos más pequeños, se instaló a sí mismo en una partición creada ahí y dejó el resto como espacio para intercambio. Claro, a la primera actualización que traté de hacer me dijo que no tenía espacio físico. Y mientras, la partición de 25 GB que yo había hecho para él estaba vacía, triste y solitaria. :(

Por eso me pregunto si lo más adecuado será iniciar desde el Live CD y, desde ahí, preparar y formatear las particiones antes de correr el programa de instalación. 

MI principal problema con el menú de instalación de Ubuntu para las particiones, es que no logro entender con exactitud qué va a hacer: si escojo "opción 1", elige a su gusto en dónde va a instalar, sin que yo pueda asignarle una partición. 

Si escojo "opción 2", supuestamente borra todo, pero no sé si desde ahí puedo ir creando las particiones en el disco duro íntegro. Y si ya para este paso he instalado el Windows, definitivamente no me interesaría borrar todo. 

Si selecciono "opción 3", que es avanzada, yo misma debo crear todo manualmente y es así como acabé con un disco de más de 7 particiones (es decir, no lo sé utilizar correctamente).

**Pregunta 3: instalar primero Windows o Ubuntu**
Cuando uno instala primero Ubuntu, el Windows luego destruye el Grub original y es necesario instalarlo otra vez. Pero, cuando uno instala primero Ubuntu, pareciera que esto no ocurre. ¿Me recomendarían utilizar este procedimiento, instalar Windows primero y Ubuntu después? O bien, ¿piensan que es mejor instalar primero Ubuntu y después Windows y reinstalar el Grub? 

Si instalo primero el Windows, regreso al problema original: ¿cuál de las tres opciones de instalación del Ubuntu debo seleccionar: 1, 2 ó 3?

Bueno, por ahora esas son las preguntas que tengo.

Muchas gracias por su ayuda.

---

### Post by pablo.s on 2009-04-30
Has redactado el mejor post que vi en 
ningún foro en toda mi vida.

**Respuesta 1: Tamaño de las particiones**

Las particiones pueden ser del tamaño
que uno quiera (hay limitaciones de 16 TB
para Ext3, cuidado)
Si querés instalar Linux en una partición
grande, sugiero:
-Hacer una partición base de 8 GB para
el / que es donde se instalan los programas
-Una partición de 100 GB para /home, que
ahi guarda los datos de los usuarios
-Una partición swap de digamos 2 GB
-Lo que quede (50 GB) al principio del
disco para Windows (buuuuuu)

**Respuesta 2: Preparación de las particiones**

Particionar desde el Live CD.
Una vez realizado esto, instalar el sistema
privativo defectuoso e inseguro.
Terminada la instalación del sistema privativo
defectuoso e inseguro, volver a lanzar
el Live CD e instalar Linux, preferentemente
Ubuntu.

Espero que sirva.

---

### Post by cor_stellae on 2009-04-30
¡Hola Pablo!

Muchas gracias, me queda clarísimo. Gracias también por el piropo, pero creo que hago trampa porque redactar bien es mi profesión... je je je... queda claro que informática no soy :lolflag:.

Bien, una pregunta más, aprovechando tu amabilidad. En este proceso que estoy de hacer respaldo de los discos duros, el disco duro que estaba usando como respaldo es perfectamente legible desde Ubuntu (puedo copiar y pegar sin problemas), pero el Windows no logró ver sus contenidos nunca (siempre indicaba que era necesario formatearlo). 

Para evitar el problema, decidí formatearlo nuevamente desde el LiveCD, como NTFS. El asunto es que ahora cuando abro el programa GParted, en Ubuntu (desde el HD, no desde el LiveCD), me incluye un signo de advertencia. La leyenda dice más o menos así: "Imposible leer de este sistema de archivos. Debido a esto, algunas operaciones pueden no estar disponibles."

Acabo de notar que el mismo aviso lo incluye la partición NTFS en la que está actualmente instalado el Windows.

Me pregunto si es necesario que haga caso de esta advertencia o puedo seguir adelante, sin preocuparme demasiado. También pregunto si el NTFS es mejor formatearlo siempre desde Windows, ya que veo que no es el formato preferido de Ubuntu.

---

### Post by pablo.s on 2009-04-30
> **cor_stellae said:**
>  El asunto es que ahora cuando abro el programa GParted, en Ubuntu (desde el HD, no desde el LiveCD), me incluye un signo de advertencia. La leyenda dice más o menos así: "Imposible leer de este sistema de archivos. Debido a esto, algunas operaciones pueden no estar disponibles."

Acabo de notar que el mismo aviso lo incluye la partición NTFS en la que está actualmente instalado el Windows.

Me pregunto si es necesario que haga caso de esta advertencia o puedo seguir adelante, sin preocuparme demasiado. También pregunto si el NTFS es mejor formatearlo siempre desde Windows, ya que veo que no es el formato preferido de Ubuntu.

Mmm... Veamos, desde Gparted se puede
formatear NTFS. Supongo que debe formatear
igual que desde Windows, nunca lo hice
afortunadamente. NTFS es un sistema de
archivos avanzado de Windows, pero a mi y
a muchos nos parece una basura, como todo
lo que hace Microsoft. Lease que estoy
criticando con conocimiento de lo sencillo
que es corromper una partición formateada
en NTFS. Pero igualmente no hay mucho para
elegir: eso o FAT32, otro engendro.

Si formateas el disco de respaldo, pierdes lo
que contiene, todos los datos.

---

### Post by cor_stellae on 2009-04-30
Je je je je.... Me acabo de encontrar este tutorial que está perfecto para particionar antes de la instalación. Lo dejo aquí por si alguna otra persona tiene las mismas inquietudes existenciales en el futuro.

[http://chamangt.wordpress.com/2008/05/13/instalar-ubuntu-804-con-windows-preinstalado-y-home-independiente/](http://chamangt.wordpress.com/2008/05/13/instalar-ubuntu-804-con-windows-preinstalado-y-home-independiente/)

---

### Post by cor_stellae on 2009-04-30
Hola Pablo:

Gracias por la respuesta. Sí, pierdo los datos porque los voy a copiar otra vez... todo está "fríamente calculado". En cuanto a Fat32, pues por lo que he leído es mejor NTSF, así que ni modo. Bien, proseguiré entonces. En unas horas te cuento.

---

### Post by cor_stellae on 2009-04-30
Hola de nuevo:

Esta vez sí vengo a cantar victoria. Logré instalar ambos sistemas exitosamente, y ahora solamente tengo 4 particiones. :lolflag:

Seguiré entonces personalizando y descubriendo mi nuevo Ubuntu que me hace sentir como si tuviera una computadora nueva... :guitar:

Un abrazo y mil gracias!!!!!!!!!!!!!!!!!! :KS

---

### Post by josecuervo86 on 2009-04-30
Bueno, entonces ahora si corresponden las felicidades no?? 

Felicitaciones!!

---

### Post by ADICTOALMAXIMO on 2009-05-01
jaja

hapy hapy hapy
foooooo

llouuuuuuuu

---

### Post by cor_stellae on 2009-05-01
Weee!!!!! Sí, ahora ya por fin me estoy dando gusto instalando y explorando aplicaciones en Ubuntu!!! Ya localicé una de Astrología y brinco de contento. Todavía el A-Mule no me responde como quisiera (no se mueve, no localiza fuentes, tengo una ID baja y, cuando ve fuentes, no son ni una décima parte de las que veía desde E-Mule... pero ahí vamos).

:popcorn: Por ahora, ¡a celebrar!

---

### Post by josecuervo86 on 2009-05-01
De Astrologia o Astronomia?? Por si es de la segunda, Stellarium esta muy, pero muy bueno.

```
sudo apt-get install stellarium
```

---

### Post by cor_stellae on 2009-05-01
Sí... es Astrología y no Astronomía... son diferentes. Claro que probaré el Stellarium, porque también me interesa la observación de estrellas y utilizaba un software para eso en Windows. Pero el software de Astrología calcula los mapas natales, progresados, etc., a partir de las efemérides estelares. Nos da como resultado un diagrama o dibujo con la posición de los planetas, objetos y signos que es el que se utiliza para hacer el estudio psicológico de cada persona. Afortunadamente, alguien ya había pensado en eso y así es que diseñaron el OpenAstro para Linux.

---

