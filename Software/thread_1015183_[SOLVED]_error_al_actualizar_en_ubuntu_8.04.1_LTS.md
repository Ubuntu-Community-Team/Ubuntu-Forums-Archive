---
title: "[SOLVED] error al actualizar en ubuntu 8.04.1 LTS"
date: 2008-12-18
forum: Software
---

### Post by lucasfava on 2008-12-18
Esto me esta pasando desde hace dos días, parece que es algo del linux-image

cuando actualizo me pone esto

[COLOR="Red"](Leyendo la base de datos ...
115735 ficheros y directorios instalados actualmente.)
Preparando para reemplazar limux-image-2.6.24-19-generic 2.624-19.34 (usando .../linux-image-2.6.24-19.41_i386.deb) ...
Done.
Desempaquetando el reemplazo de linux-image-2.6.24-19-generic ...
dpkg: error al procesar /var/cache/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb ( --unpack):
 no se puede crear un enlace de seguridad de './boot/vmlinuz-2.6.24-19-generic' antes de instalar
la nueva versiòn: Operaciòn no permitida
dpkg-deb: el subproceso paste fue terminado por la señal (Tuberia rota)
Running postrm hook script /sbin/update-grub.
searching for GRUB installation directory ... found: /
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found Kernel: /boot/vmlinuz-2.6.24-22-generic
Found Kernel: /boot/vmlinuz-2.6.24-19-generic
Found Kernel: /boot/memtest86+bin
Updating /boot/grub/menu.lst ... done

Se encontraron errores al procesar:
 /var/cache/apt/archives/linux-image-2.6.24-19.41_i386.deb
E: Sub-proces /usr/bin/dpkg returned an error code (1)
No se ha podido instalar un paquete. Intentando recuperarse:
[/COLOR]

Después salta esta, ventana de error

[COLOR="Red"]E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: no se puede crear un enlace de seguridad de `./boot/vmlinuz-2.6.24-19-generic' antes de instalar [/COLOR]

alguien sabe que tengo que hacer,:confused: soy novato novato,

---

### Post by guillermolisi on 2008-12-18
Cuando llevas a cabo la actualizacion, que usas, linea de comandos - apt-get, Synaptic, etc. ?

Cuando inicas el proceso de actualizacion, te solicita que ingreses la password del usuario que estas usando ?

Si te solicita que ingreses una password, le pones la del usuario u otra ?

---

### Post by lucasfava on 2008-12-18
Actualizo desde el gestor de actualizaciones, porque todavía no se usar la terminal, cuando pide el password pongo el de usuario.
E leído por hay que tengo que eliminar ese archivo y reinstalarlo de nuevo, puede ser o no es muy buena opción :confused:

---

### Post by guillermolisi on 2008-12-21
> **lucasfava said:**
> Actualizo desde el gestor de actualizaciones, porque todavía no se usar la terminal, cuando pide el password pongo el de usuario.
E leído por hay que tengo que eliminar ese archivo y reinstalarlo de nuevo, puede ser o no es muy buena opción :confused:
Si aun no lo hiciste, si, puede ser una buena opcion pero antes de actualizar vas a tener que revisar que esten marcados todos los repositorios que tenias antes de borrar el archivo (tal vez te convenga mas renombrarlo, por las dudas, ya que para borrarlo siempre hay tiempo (una vez que puedas actualziar correctamente.

Con los repos que utilizas, inicias Synaptic/gestor de actualizaciones y regenera el sources.list

---

### Post by lucasfava on 2008-12-21
[COLOR="Red"]**Guille**[/COLOR] como no quiero joder el S.O, me vas a tener que guiar, como renombro el paquete.
En synaptyc el paquete con problema es la versión 2.6.24-19.34 y hay una versión mas nueva para actualizar la .41.
Una pregunta que significa x86/x86_64, mi viejo dijo que era de pentium 4 y la maquina donde está andando es pentium 3

---

### Post by guillermolisi on 2008-12-22
> **lucasfava said:**
> [COLOR=Red]**Guille**[/COLOR] como no quiero joder el S.O, me vas a tener que guiar, como renombro el paquete.
En synaptyc el paquete con problema es la versión 2.6.24-19.34 y hay una versión mas nueva para actualizar la .41.
Una pregunta que significa x86/x86_64, mi viejo dijo que era de pentium 4 y la maquina donde está andando es pentium 3
El tema no es renombrar el paquete sino el archivo /etc/apt/sources.list, que es donde figuran todos los repositorios que tenes incluidos para actualizar/bajar paquetes.

Renombrar este archivo es solo una cuestion de mejores practicas, por si la solucion no resulta como se espera, asegurandote el camino de vuelta al punto inicial.

Para renombrar el archivo tenes que abrir una consola e ingresar```

sudo mv /etc/apt/sources.list /etc/apt/sources_original.list (por ejemplo)
```Luego abris el administrador de actualizaciones y revisa que paquetes podes marcar, cuales no queres y cuales tenes que agregar (si pusiste alguno que no venga por defecto en la distribucion original de Ubuntu).

Con esto le das que actualice, lo que en consola seria
```
sudo apt-get update
```Y despues intentas actualizar lo que no te funciono hasta ahora.

Para volver todo atras (si el intento falla), copias el archivo sources_original.list sobre el que se genero con el update de repositorios volviendo a abrir una consola y poniendo:
```
sudo cp /etc/apt/sources_original.list /etc/apt/sources.list
```

La nomenclatura x86 se utiliza pra indicar que es arquitectura Intel (valida para procesadores CICS Intel/AMD).

x86/x86_64 pareceria indicar que es tanto para 32 como para 64 bits por lo que incluiria Pentium III (32 bits arquitectura Intel x86).

---

### Post by lucasfava on 2008-12-22
Hola [COLOR="Red"]**Guille**[/COLOR]
Ayer a la noche, buscando, encontré esta pagina 
[http://ubuntulife.wordpress.com/2008/04/27/cosas-a-hacer-despues-de-instalar-ubuntu-84-hardy-heron/]("http://ubuntulife.wordpress.com/2008/04/27/cosas-a-hacer-despues-de-instalar-ubuntu-84-hardy-heron/")
 hay dice como verificar el kernel (el que sale no lo debo tocar, y los otros puedo borrarlos si quiero)

aplicando 

uname -r (en terminal) me salio el siguiente [COLOR="Red"]2.6.24-22-generic[/COLOR], en synaptic versión instalada [COLOR="Red"]22.45[/COLOR]

Al verificar por synaptyc me sale ese y el otro [COLOR="Red"]-19-generic[/COLOR] (pero este tiene una estrellita en el recuadro verde ¿que significa? :confused:), ese es el que jode cuando actualizo. La versión en synapic [COLOR="Red"]19.34[/COLOR].

P.D: ayer empezó otro problema, tengo XP y ubuntu en dos particiones en el mismo disco, pero cuando quiero entrar a la particion del XP se reinicia, hoy se reinicio tres veces que pasa :confused:

---

### Post by guillermolisi on 2008-12-22
> **lucasfava said:**
> Hola [COLOR="Red"]**Guille**[/COLOR]
Ayer a la noche, buscando, encontré esta pagina 
[http://ubuntulife.wordpress.com/2008/04/27/cosas-a-hacer-despues-de-instalar-ubuntu-84-hardy-heron/]("http://ubuntulife.wordpress.com/2008/04/27/cosas-a-hacer-despues-de-instalar-ubuntu-84-hardy-heron/")
 hay dice como verificar el kernel (el que sale no lo debo tocar, y los otros puedo borrarlos si quiero)

aplicando 

uname -r (en terminal) me salio el siguiente [COLOR="Red"]2.6.24-22-generic[/COLOR], en synaptic versión instalada [COLOR="Red"]22.45[/COLOR]

Al verificar por synaptyc me sale ese y el otro [COLOR="Red"]-19-generic[/COLOR] (pero este tiene una estrellita en el recuadro verde ¿que significa? :confused:), ese es el que jode cuando actualizo. La versión en synapic [COLOR="Red"]19.34[/COLOR].

P.D: ayer empezó otro problema, tengo XP y ubuntu en dos particiones en el mismo disco, pero cuando quiero entrar a la particion del XP se reinicia, hoy se reinicio tres veces que pasa :confused:

Vos inicias Ubuntu con un kernel que se supone es la ultima version de los posibles que puedas tener instalados en tu maquina.
Ese kernel es el que se informa a traves del comando uname y es el que debe importarte a la hora de actualizar.

Para usar una maquina como desktop, la variante generic es la recomendada (las variantes tienen que ver con la latencia del kernel para atender los procesos que demanden asignacion de recursos de maquina).

Si el que te da error *no* es el que estas usando, forget it or delete it.

Por la salida del uname que mencionaste, estas usando la ultima version de kernel para HH (8.04), asi que por ahora no habria mas actualizaciones hasta nuevo aviso.

La estrellita amarilla sobre fondo verde significa que hay una actualizacion a realizar para ese paquete (pero podes decirle que no queres actualizarlo, si es que no te interesa porque no lo usas).

Sobre el tema XP no voy a decir mas que esto ya que este foro no trata sobre esa plataforma operativa (despues de Ubuntu/Linux es uno de los temas con mas contenido en la web :) ) pero por lo que decis no me parece estar vinculado con el dual boot.

No se si logro interpretar adecuadamente tu situacion actual (estoy como confundido a esta altura del intercambio).

---

### Post by lucasfava on 2008-12-22
Hola [COLOR="Red"]**guille**[/COLOR]
El asunto era, por entrar rápido al XP, es que yo uso linux por los programas de bioinformatica que tiene :)
Bueno al final lo suprimí, y reinicio para ver si no hay problemas :)

---

### Post by lucasfava on 2008-12-22
Solucionado :lolflag:

Gracias [COLOR="Red"]**Guille**[/COLOR]

Sabes alguna pagina o archivo, que explique el manejo del terminal, quiero entender bien como usarlo, desde principiante a avanzado :)
Lo que no puedo solucionar todabia es, lo de hacer que el sistema apague automaticamente la maquina, o hacerlo hibernar(aparece solo al principio, pero no al apagar la maquina):(, o es que tengo que cliquear hay y aprece cuando termino la seciòn :confused:

---

### Post by guillermolisi on 2008-12-22
> **lucasfava said:**
> Solucionado :lolflag:

Gracias [COLOR="Red"]**Guille**[/COLOR]

Sabes alguna pagina o archivo, que explique el manejo del terminal, quiero entender bien como usarlo, desde principiante a avanzado :)
Lo que no puedo solucionar todabia es, lo de hacer que el sistema apague automaticamente la maquina, o hacerlo hibernar(aparece solo al principio, pero no al apagar la maquina):(, o es que tengo que cliquear hay y aprece cuando termino la seciòn :confused:

En realidad todos los programas que corres en el escritorio grafico pueden iniciarse en una consola y, en general y salvo algunas excepciones, todos cuentan con su manual on line.

Por ejemplo, abris una consola e ingresas
```
man apt-get
```
y te explica con cierto nivel de detalle como usar el comando.

Algunos tienen traduccion completa al Español, otros en forma parcial y otros estan solo en Ingles.

Hace muy poco tiempo Hei Ku puso un sticky message en el foro donde menciona una gran cantidad de enlaces utiles y por lo menos uno de ellos hace referencia a documentacion en general sobre Ubuntu/Linux.

Documentacion especifica sobre uso de consola nunca tuve que buscar, por lo tanto no se si existe tal cosa (probablemente si, pero deberia googlear si es que en este mismo foro no hubo ya algun thread sobre ese particular).

Sobre el resto de los temas, lo mejor seria que habras un nuevo hilo para cada uno. De esta forma a cualquier otro que tenga la misma duda le servira si esta separado, adecuadamente titulado en su asunto, y con las respuestas especificas al tema. Sobre todo si utiliza la funcion de buscar dentro del foro.

Luego, te pido que marques como resuelto/solucionado este tema (hay una funcion en la barra de menues/opciones al principio de la lista de mensajes sobre este asunto) que le pone una etiqueta de SOLVED al asunto, asi quien incurra en un problema similar sabra que en este hilo se resolvio y como.

Si no lo encontras, avisa que los administradores o cualquier otro que participe del foro te damos una mano.

Por ultimo, vas a ver abajo a la derecha de cada mensaje un icono que cuando pasas el puntero del mouse aparece un tip que dice "thanks" o parecido. Te agradeceria que lo uses si mi ayuda te sirvio.

---

