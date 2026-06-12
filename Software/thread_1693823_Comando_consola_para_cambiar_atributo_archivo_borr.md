---
title: "Comando consola para cambiar atributo archivo borrado"
date: 2011-02-23
forum: Software
---

### Post by pabloatilio on 2011-02-23
Amigos

Estoy buscando algún comando (o secuencia de ellos) que me permita que un archivo que está marcado como (deleted) deje de serlo y sea visible por los métodos habituales. Aclaro que no estoy buscando un programa que haga eso para archivos borrados, sino un comando por terminal. Gracias por sus respuestas y por su tiempo. Saludos !!

Pablo A.

---

### Post by gmunioz on 2011-02-24
¿ archivo marcado como deleted?
hasta donde sé, eso en Gnu/Linux no existe.

En los sistemas de archivo ExtX, usados en Gnu/Linux, el borrar un archivo exige una serie de pasos que modifican estructuras claves como los i-nodos, para mantener consistente la integridad del sistema. 
Si bien cuando se borra un archivo en sistemas Ext2, los valores de los i-nodos no desaparecen, luego los apuntadores a los bloques de los datos existen, en el caso de Ext3, los apuntadores no permanecen.

El mecanismo de borrado de archivos en sistemas de archivos ExtX es más o menos el siguiente:

Se lee el superbloque.
Se lee tabla de descriptores de grupo de bloques.
Se localiza el archivo a eliminar en el directorio raíz y se procesa el i-nodo 2.
Se ubica en el grupo de bloques, la tabla de I-nodos, para identificar dentro de la estructura de directorios, el bloque que le corresponde al archivo a eliminar.
Se lee el contenido del directorio raíz para el número de bloque identificado e identifica el valor del I-nodo del archivo.
Se calcula donde esta ubicado el inodo del archivo, dentro del grupo de bloques.
Ubicado el archivo dentro del grupo de bloque, se procede a desasignar y cambiar el estado del I-nodo, lo cual lleva a la actualización del MAC time del archivo, registrándose estos cambios en el sistema de journaling del sistema.
Se desasignan los bloques ocupados por el archivo, actualizando el bit en el bloque que indica su uso a 0 y el apuntador al bloque en el I-nodo es reiniciado.

---

### Post by pabloatilio on 2011-02-24
> **gmunioz said:**
> ¿ archivo marcado como deleted?
hasta donde sé, eso en Gnu/Linux no existe.

En los sistemas de archivo ExtX, usados en Gnu/Linux, el borrar un archivo exige .......

Hola, gracias por tu respuesta, te cuento que los archivos marcados como "deleted" a mi entender , si existen o están en algúna especie de "limbo" y son visibles/recuperables hasta que se disparan algunos eventos (por ej. el cierre del programa que los generó) que los borran definitivamente. 

Te explico porqué pienso esto:

El caso que estoy tratando es el de nuestros queridos amigos de adobe, que antes guardaban los archivos que reproducías con el navegador (por ej. de youtube) en el directorio "temp" y uno podía copiarlos y guardarlos en donde quisiera; y que como todos saben, con la última actualización (gracias adobe :(  -creo que es por eso-), los sigue guardando en el directorio "temp" pero los marca como "deleted" por eso no se los puede ver ni manipular fácilmente, me consta que esto es así, porque por vía de otros mecanismos pude recuperar todos los archivos descargados y moverlos a un archivo "normal" y verlos offline, pero busco algún comando linux o secuencia que me permita hacer algo como un script o complemento que me automatice dicha operación. 

Hasta que termina la carga del archivo flash, los guarda en el directorio de la caché del navegador "por ej : .mozilla ... etc" pero 
-aparentemente- cuando la descarga se completa los mueve a temp y los marca como "deleted" sin embargo ahí están, y como dije antes, los puedo recuperar pero con comandos que no me son del todo útiles para lo que quiero hacer, porque tengo que apuntar a la id del proceso del reproductor flash, luego ver el archivo que usa (que efectivamente sale marcado como deleted) y no directamente al archivo en cuestión. Por eso digo, por lo menos para mi entender, sí existen, porque sino no los podría recuperar. Eso sí, en el momento que cerrás la ventana del navegador, efectivamente el archivo desaparece (por eso decía "lo de algún evento..."). 

Además me interesa ver ese tema de si hay archivos marcados como "deleted" que puedan ser recuperados porque pienso que me puede ser útil para algunas cuestiones de tipo un poco más profesional. 

 Bueno, si estoy equivocado y alguien me puede desaznar, soy todo oídos ! 
Saludos

Pablo A

---

### Post by guillermolisi on 2011-02-24
Coincido con Gmunioz salvo por el hecho real de que el archivo (o su contenido) sigue fisicamente en el disco y a partir de esto con herramientas de recuperacion/administracion de filesystems (o informatica forense) podes recuperarlo, total o parcialmente. Pero no creo que sea lo que pabloatilio esta buscando.

---

### Post by biale on 2011-02-24
No lo probe con Youtube, pero el efecto existe y luce como "si existiera" una especie de marca.

Pensandolo un poco lo atribuyo (o sea: no lo se) a un bloqueo de archivo y a la comunicación entre procesos. Hasta que no se termina realmente de usar no se borra. Y descartaría al buffer cache, también al retardo de escritura de ext4

¿No te sirve el download helper bajo FFox? Hace una bajada y la guarda. Y recuerdo que existen varios instalables que si les das la URL permiten bajar y guardar. Pero son bajadas independientes, si querés ver y guardar a la vez el ancho de banda se duplica.

---

### Post by pabloatilio on 2011-02-25
> **biale said:**
> No lo probe con Youtube, pero el efecto existe y luce como "si existiera" una especie de marca.

Pensandolo un poco lo atribuyo (o sea: no lo se) a un bloqueo de archivo y a la comunicación entre procesos. Hasta que no se termina realmente de usar no se borra. Y descartaría al buffer cache, también al retardo de escritura de ext4

¿No te sirve el download helper bajo FFox? Hace una bajada y la guarda. Y recuerdo que existen varios instalables que si les das la URL permiten bajar y guardar. Pero son bajadas independientes, si querés ver y guardar a la vez el ancho de banda se duplica.


Muchachos, gracias a todos por sus respuestas y por el enriquecedor diálogo que podemos construir. 

Con respecto a los gestores de descargas que andan dando vueltas, en efecto, me sirven y los uso, pero tenía curiosidad de ver como era eso de un archivo que está, -pero no está-, pensando que tal vez existiesen algunos comandos linux que me permitiesen hacer como dicen "ingeniería forense" en ámbitos profesionales y de paso guardar los archivos flash muy pesados que quisiera volver a ver en algún momento, haciendo algún tipo de script, complemento o lo que sea para automatizar el proceso.

Por si les interesa, el procedimiento que uso cuando no tengo el gestor de descargas de archivos flash es el siguiente : **[COLOR="DeepSkyBlue"](2 pasos)[/COLOR]**

**[COLOR="DeepSkyBlue"]1)[/COLOR]** pabloatilio@notebook:~$** [COLOR="DeepSkyBlue"]lsof |grep Flash[/COLOR]** ; la salida de la terminal:
  
  npviewer. 5274 pabloatilio 11u REG 8,2 2348776 1819038 /tmp/[COLOR="Red"]Flash[/COLOR]CDeWjUdQ (deleted)

**[COLOR="DeepSkyBlue"]2)[/COLOR]** Esperamos a que el archivo flash se descargue completamente y NO cerramos la pestaña del explorador en donde está del reproductor flash,
nos fijamos en la salida del paso 1, en el primer número (5274 para el ej) y el segundo (11), luego:
   
  pabloatilio@notebook:~$ ** [COLOR="DeepSkyBlue"]cp /proc/5274/fd/11 capítulo1.flv [/COLOR]** (el nombre de archivo que se les ocurra)

listo !, archivo flash recuperado , como verán, aparece marcado como "deleted", de ahí el orígen de éste post.

Saludos !

---

### Post by guillermolisi on 2011-02-25
el comando "lsof" busca y expone los archivos abiertos que encuentre en el sistema, para decirlo muy resumidamente.

Logicamente, si el archivo esta abierto no esta ni borrado ni marcado como borrado, esta abierto, vivito y coleando hasta que el proceso que lo ocupa lo cierre.

Estuve leyendo rapidamente el man de "lsof" y me sorprendio por lo completo y lo complejo que es este comando. Interesantisimo.

Ademas, copiando de esa forma aprovechas links y pipes del proceso para tomar su contenido, algo que programas como los mencionados seguramente hacen por uno sin tanta vuelta.

---

