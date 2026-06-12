---
title: "Shareaza para linux"
date: 2008-12-08
forum: Software
---

### Post by andy_91 on 2008-12-08
bueno para empezar no se si postiar esto en software o en comunidad, por que en fin es algo para pedir a los desarrolladores.

me preguntaba si shareaza esta licenciado bajo la licencia GNU 2, por que no pedir a los desarrolladores que den una opción para Linux???
por lo menos al estilo del picasa (que utiliza librerías de wine hasta donde yo se)

mi idea es que tal vez si los usuarios de ubuntu plantean esto a los desarrolladores halla una versión de shareaza en los repositorios de la próxima LTS

Pagina del proyecto

[http://shareaza.sourceforge.net/](http://shareaza.sourceforge.net/)

---

### Post by Hei Ku on 2008-12-08
Un inconveniente es que usa la MFC, ese es el toolkit para Windows, que no es libre ni mucho menos. O sea que tecnicamente es bastante dificil portarlo a Linux.

---

### Post by andy_91 on 2008-12-08
a ahi me esta quedando mas claro, osea que mientras se use esa cosa el programa no es muy migrable, que lastima por que es muy buen programa

---

### Post by Hei Ku on 2008-12-09
Probablemente sea mas facil agregar las cosas que les faltan a los programas que ya estan en linux, como ktorrent, o alguno similar.

Que funciones tiene fuera de lo común?

---

### Post by luks911 on 2008-12-09
> **Hei Ku said:**
> Probablemente sea mas facil agregar las cosas que les faltan a los programas que ya estan en linux, como ktorrent, o alguno similar.

Que funciones tiene fuera de lo común?

Yo solía usarlo en win, y si mal no recuerdo la principal diferencia con aMule es que usa la red Gnutella, algo que también se puede hacer con MLDonkey, Frostwire o Apollon.

---

### Post by andy_91 on 2008-12-09
primero que no esta escrito en java (lo que lo hace mas ligro que limewire)

segundo tiene tres redes Gnutella 1, Gnutella 2 y una red llamada eDonkey que en windows nunca me conecto y en ubuntu si (pero esta red mucho no me gusta)

es fácil de usar como limewire (distinto de emule que nunca supe como usarlo) y tiene una interfase con skin muy sencilla.

bueno eso es en general lo que yo veo que lo diferencia, tambien les dejo lo que dice wikipedia

[QUOTE=Wikipedia]Shareaza tiene las siguientes características que lo hacen único (algunas características que tienen en común los clientes P2P no están listadas):

    * Soporte de múltiples redes: Shareaza puede descargar y buscar archivos en cuatro redes, para dar una mayor cantidad de resultados y mejor velocidad de descarga.
    * Interfaces: Elección entre una interface básica o una más avanzada, dejando a usuarios con experiencia monitorear las conexiones con las redes y configurar opciones avanzadas; para así no confundir a los usuarios no avanzados.
    * Reproductor multimedia: A diferencia de ciertos reproductores multimedia de algunos P2P, el de Shareaza remueve las partes del audio/video que aún no se descargan, para formar un archivo reproducible con las partes ya descargadas. Sin embargo, esta funcionalidad no siempre puede proveer el sonido en ciertos formatos de video.
    * Detección de errores: Shareaza utiliza hasta tres algoritmos (SHA1, ED2K Hash y TTH) para detectar errores en archivos. De esta manera es casi imposible que los archivos descargados estén corruptos. Además de que Shareaza realiza esta verificación conforme descarga los pedazos y al final de la descarga, reduciendo la cantidad de datos a descargar para corregir un error.
    * Comentarios y Calificaciones: Shareaza permite a los usuarios dar un comentario y una calificación sobre un archivo.
    * Colecciones: una funcionalidad que permite agrupar varios archivos en un archivo para así poder descargar ese conjunto de archivos con tan solo tener el archivo de la colección. Esta funcionalidad es parecida a los torrents de BitTorrent.
    * Acceso remoto: Permite acceder a ciertas funciones de Shareaza desde un navegador web, pudiendo así controlar Shareaza desde una computadora remota.
    * Multilingüe: Shareaza incluye traducciones del programa en diferentes idiomas, incluyendo el español. Además de que tiene soporte Unicode, dándole la posibilidad de ser traducido a idiomas de escritura de derecha a izquierda, entre otros.
    * Filtro: Shareaza cuenta con un filtro, que a diferencia de otros clientes, permite bloquear tanto el acceso a ciertas direcciones IP como ciertos resultados en las búsquedas. El filtro es generalmente usado para evitar conectarse a direcciones que envían tanto datos corruptos como archivos incorrectos (fakes) y para filtrar algunos virus de los resultados de las búsquedas.
    * UPnP: Shareaza cuenta soporte de la tecnología UPnP para facilitar su uso inclusive en redes que cuentan con un router (routeador), entre otros beneficios.
    * Programador: Permite configurar Shareaza para que en ciertos días/horas descargue con ciertos límites, así como poder seleccionar si se debe de conectar a las redes a ciertas horas del día, o solo descargar.
    * Pieles: La habilidad para cambiar la piel de la interface (skin) permitiendo a los usuarios cambiar la apariencia.
[/QUOTE]

desde ya gracias por su atención

---

### Post by luks911 on 2008-12-09
Sí, es probable que no haya algo idéntico. 
Lo que decía es que hay con qué reemplazarlo, o casi. La verdad es que nunca lo usé, pero por lo que poco que leí el MLDonkey se le parece bastante: usa las tres redes y hasta puede bajar torrents y  no usa java. Lo que no tiene son skins (aunque hay un par de GUIs para probar además de la que viene por defecto) ni un reproductor integrado.

Saludos :lolflag:

---

### Post by andy_91 on 2008-12-09
el MLDonkey segun wikipedia dejo de soportar le red G1 y G2  :confused:

---

### Post by luks911 on 2008-12-09
> **andy_91 said:**
> el MLDonkey segun wikipedia dejo de soportar le red G1 y G2  :confused:

Sí, tenés razón, estaba desactualizado. Pero mirando la página/wiki de MLDonkey veo que aunque el soporte no viene por defecto, aparentemente se puede activar.
[Acá]("http://mldonkey.sourceforge.net/MLdonkeyOptionsExplained#p2p_Protocols")[0] hay un listado de opciones con respecto a protocolos aceptados que pueden modificarse en el archivo .ini del programa.
Y en el peor de los casos se puede compilar la aplicación y en el proceso activarle el soporte para Gnutella pasándole un parámetro. Eso está [acá]("http://mldonkey.sourceforge.net/CompilationProblems")[1]. Fijate en el apartado "configure options" y más abajo están las instrucciones para compilarlo en Ubuntu. Si lo hacés, leelo con paciencia  porque si no entiendo mal la explicación comete errores adrede y los va solucionando, como olvidarse paquetes necesarios... :confused: medio raro, pero sería cuestión de leerlo todo para instalar todo de una y ya. Y después de eso abría que instalar la GUI de los repositorios, se me ocurre.

Pero, sí, sería mucho más sencillo tener una versión Linux de Shareaza :lolflag:

PD: otra opción, mas solo para Gnutella gtk-gnutella en repositorios.

[0] [http://mldonkey.sourceforge.net/MLdonkeyOptionsExplained#p2p_Protocols](http://mldonkey.sourceforge.net/MLdonkeyOptionsExplained#p2p_Protocols)
[1] [http://mldonkey.sourceforge.net/CompilationProblems](http://mldonkey.sourceforge.net/CompilationProblems)

---

### Post by andy_91 on 2008-12-11
> **luks911 said:**
> 

Pero, sí, sería mucho más sencillo tener una versión Linux de Shareaza :lolflag:

PD: otra opción, mas solo para Gnutella gtk-gnutella en repositorios



si seria mas posible para mi si hubiera una versión de shareaza para Linux :lolflag:

ya probé gtk-gnutella y nunca supe como usarlo :confused:

bueno las opciones para reemplazarlo no son muy alentadoras

pero debido a la imposibilidad de migrarlo supongo que la única solución es Wine

---

