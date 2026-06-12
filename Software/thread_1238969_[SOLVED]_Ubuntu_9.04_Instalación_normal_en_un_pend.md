---
title: "[SOLVED] Ubuntu 9.04 Instalación normal en un pendrive"
date: 2009-08-13
forum: Software
---

### Post by madbyte on 2009-08-13
Hola, soy nuevo en Ubuntu, y estoy tratando de instalar la version 9.04 en un pendrive, anteriormente probe instalando con el *uSubuntu Live Creator* y otras herramientas parecidas, pero tuve varios problemas y no andaba del todo bien, asi que en el foro en ingles me aconsejaron que haga una instalación normal sobre el pendrive. Arranco desde un cd, pero llego hasta el paso 4 y ahi no se bien que opcion seguir:

Si eligo *Utilizar todo el disco,* para el pendrive, se instala automaticamente el archivo de intercambio swap??? Cosa que no es deseable en una flash.

Y si entro a la opcion avanzada *Especificar particiones manualmente,* que debería elegir ahi?? No me queda claro lo de las particiones para  /home, root, si es necesario hacer eso, y si asi fuera, no se que tamaño es el adecuado para cada una. (Tengo un disco con Windows XP que no quiero tocar)

Si la primera opcion no instala el swap seria lo mejor para mi, pero como no estoy seguro espero que alguien me aclare el panorama.

Gracias

---

### Post by rubioo on 2009-08-13
madbyte quieres instalar Ubuntu en el pendrive para poder usarlo como live cd? o quieres hacer una instalación como si se tratase de un disco?

 Yo ahora mismo estoy haciendo lo primero, usando el *Creador de disco de arranque* que trae Ubuntu. Para hacerlo necesitas el CD o la imagen iso.

   Saludos

---

### Post by alfplayer on 2009-08-13
Instalarlo directamente en el pendrive es menos problemático porque el pendrive actúa en Ubuntu como un disco rígido, pero al crear el pendrive booteable con la aplicación de Ubuntu se usa el sistema casper, y esto implica una menor cantidad de escritura de datos en el pendrive, lo cual le da una ventaja en  el tiempo de vida útil del pendrive.

---

### Post by madbyte on 2009-08-13
Gracias por responder

> **rubioo said:**
> madbyte quieres instalar Ubuntu en el pendrive para poder usarlo como live cd? o quieres hacer una instalación como si se tratase de un disco?

Yo ahora mismo estoy haciendo lo primero, usando el Creador de disco de arranque que trae Ubuntu. Para hacerlo necesitas el CD o la imagen iso.

Lo que quiero hacer es tener Ubuntu en un pendrive al cual pueda modificar, agregar usuarios, cargar drivers, etc y que quede todo guardado y que ademas funcione bien (Tuve problemas con algunas utilidades que vienen para Windows para hacer una instalacion persistente de Ubuntu en un pendrive: [http://ubuntuforums.org/showthread.php?t=1233704](http://ubuntuforums.org/showthread.php?t=1233704)), si, seria como si fuera en un disco duro pero sin el archivo de intercambio swap. Tambien probe lo que me comentas, creando un disco de arranque desde Ubuntu (iniciado desde el CD) con espacio para almacenar datos, pero cuando arranca desde el pendrive, me sale las mismas opciones que desde el CD y no se si hice algo mal, pero a modo de prueba, hice un archivo en la carpeta Documents, y al siguiente reinicio ya no estaba ahi. Cual es la opcion que debo elegir?? *Probar ubuntu sin alterar su equipo*???

> **alfplayer said:**
> Instalarlo directamente en el pendrive es menos problemático porque el pendrive actúa en Ubuntu como un disco rígido, pero al crear el pendrive booteable con la aplicación de Ubuntu se usa el sistema casper, y esto implica una menor cantidad de escritura de datos en el pendrive, lo cual le da una ventaja en el tiempo de vida útil del pendrive.

Bien, ahora... que debo hacer en el paso 4 para realizar la instalacion sobre el pendrive sin un swap??

Disculpen mis preguntas, y sean pacientes... je... pero es un mundo totalmente nuevo para alguien que no salio del Windows.

Gracias

---

### Post by alfplayer on 2009-08-13
Disculpame, qué paso 4?

Con la aplicación de Ubuntu no queda una partición swap, solo queda una partición FAT32.

Este es mi minitutorial para hacerlo con Jaunty. No queda perfecto, durante unos segundos aparece el menú para elegir idioma en el inicio (el menú del cd de instalación), pero después Ubuntu queda funcionando.

Con el cd de instalación de Jaunty en la lectora de cd: 
Sistema --> Administración --> Creador de discos de arranque USB 
En ese programa lo único que hice es mover la barra para que quede un "espacio reservado", que es un espacio para leer y escribir archivos en el pendrive (leí que puede haber problemas si se elige un espacio mayor a 4 GB).

Cuando termina ese proceso, con un editor de texto modificar el archivo syslinux.cfg en el directorio syslinux del pendrive (no tiene sentido cambiar el archivo con el mismo nombre que está en el directorio raíz del pendrive), cambiar el valor de timeout de 300 a 30 (reemplazar 300 por 30). Esto es para hacer más rápido el inicio.

Iniciar el pendrive, seleccionar Español en el menú de idioma (el idioma que se elige ahora es el que queda definitivamente), después apretar Enter para seleccionar Probar Ubuntu sin alterar el equipo, esperar un poco, y listo! ya estamos adentro.

Después hay que hacer algo raro: cuando se inicia el pendrive las veces siguientes lo que hay que hacer es dejarlo que cuente los 3 segundos, que es el valor 30 que quedó en el archivo que modificamos (no importa que quede seleccionado English porque el idioma ya lo elegimos la primera vez que iniciamos el pendrive).

Otro problema que tuve es que la seguna vez que inicio el pendrive me aparecieron unos errores: no se pueden cargar unos applet del panel. Se pueden agregar manualmente al panel, pero pueden desaparecer de nuevo las siguientes veces que se inicia el pendrive.

Espero que sirva, aunque obviamente es un hack.

Si alguien sabe cómo eliminar el menú de idioma para que quede mejor visualmente que haga el aporte por favor.

---

### Post by staar on 2009-08-13
aviso que nunca lo hice, pero me parece que tendrías que elegir el particionado manual, crear una partición en el pendrive (suponiendo que no tengas una creada ya), con el sistema de archivos que te guste (el por defecto, ext3, está bien, ext2, en teoría, no afectaría tanto la vida útil del pendrive, a costa de algunas cosas) y ponerle como punto de montaje "/", y listo, le das instalar...

saludos

---

### Post by madbyte on 2009-08-13
Hola

> **alfplayer said:**
> Disculpame, qué paso 4?

El paso 4 siguiendo una instalacion normal, donde llegas al particionado. (son 7 pasos)

> **alfplayer said:**
> Espero que sirva, aunque obviamente es un hack.

No me fue bien con esas versiones... :(


> **staar said:**
> aviso que nunca lo hice, pero me parece que tendrías que elegir el particionado manual, crear una partición en el pendrive (suponiendo que no tengas una creada ya), con el sistema de archivos que te guste (el por defecto, ext3, está bien, ext2, en teoría, no afectaría tanto la vida útil del pendrive, a costa de algunas cosas) y ponerle como punto de montaje "/", y listo, le das instalar... 

ok... voy a probar eso a ver q pasa... y x las dudas voy a desconectar my disco...

---

### Post by pablo.s on 2009-08-13
> **madbyte said:**
> 
ok... voy a probar eso a ver q pasa... y x las dudas voy a desconectar my disco...

No hace falta desconectar
ningún disco, en el particionado
manual trabajá sobre el pendrive
e ignorá a los demás discos.
Yo ya he instalado Ubuntu en un
pendrive y no hay ningún riesgo,
siempre y cuando te limites a
instalar dentro del pendrive incluyendo
a GRUB dentro del pendrive.

---

### Post by madbyte on 2009-08-13
> **pablo.s said:**
> No hace falta desconectar
ningún disco, en el particionado
manual trabajá sobre el pendrive
e ignorá a los demás discos.
Yo ya he instalado Ubuntu en un
pendrive y no hay ningún riesgo,
siempre y cuando te limites a
instalar dentro del pendrive incluyendo
a GRUB dentro del pendrive.

ok, gracias... si no t j**e... me podrias indicar q hacer en el paso 4?? asi somos los newbies... molestos y cargosos... vio??? :P

---

### Post by pablo.s on 2009-08-13
> **madbyte said:**
> me podrias indicar q hacer en el paso 4??

Describime cual es el paso 4,
si sos tan amable.

---

### Post by guillermolisi on 2009-08-13
> **pablo.s said:**
> Describime cual es el paso 4,
si sos tan amable.
Este > Arranco desde un cd, pero llego hasta el paso 4 y ahi no se bien que opcion seguir:

---

### Post by pablo.s on 2009-08-13
> **guillermolisi said:**
> Este

No question about it. Be more descriptive
about what implies in the LiveCD installation
on step 4. No way I'm going to do an install
just for orientation's sake, you know what I mean?

PS: My apologies if I sound rude or demeaning, Will.

---

### Post by josecuervo86 on 2009-08-13
No (nou :P)

Me parece que se refiere a la parte donde creas la tabla de particiones

---

### Post by madbyte on 2009-08-13
> **pablo.s said:**
> Describime cual es el paso 4,
si sos tan amable.

ok... Paso 4:

[IMG]http://www.compumundo-hipermegared.com/images/Pantallazo-1.png[/IMG]

Llego hasta ahi y no se bien que opcion seguir... 

Si eligo *Ultizar todo el disco* (seleccionando el pendrive) seria la mas facil pero no se si tambien incluye el swap en esta opcion automaticamente. (cosa q no quiero)

Y si eligo *Especificar particiones manualmente (avanzado)*... entro en la sala de patines... :confused:

---

### Post by pablo.s on 2009-08-13
Supongamos:

Particionamiento manual, haciendo
una partición para / en ext2 (Vamos a
hacerle caso a staar) más una partición
de /home, también en ext2, y por 
supuesto una swap de 1 GB.
Después de eso instala normalmente.

EDIT: por lo que veo estás eligiendo
un disco duro, no el pendrive.

---

### Post by josecuervo86 on 2009-08-13
Si seleccionas usar todo el disco y dejas que lo haga automaticamente, entonces te va a incluir la swap, cosa que por lo que lei vos no queres. Entonces pone especificar manualmente

---

### Post by pablo.s on 2009-08-13
Alguna razón para no
crear una partición swap?
Se va a arrastrar...

---

### Post by josecuervo86 on 2009-08-13
> **pablo.s said:**
> 
Se va a arrastrar...

El cliente siempre tiene **alguna** razon

---

### Post by madbyte on 2009-08-13
me olvide de aclarar que la imagen no es un screenshot mio, la encontre x ahi (no se si hice bien en postearla...) pero hacia referencia al paso 4...

> **josecuervo86 said:**
> Si seleccionas usar todo el disco y dejas que lo haga 
automaticamente, entonces te va a incluir la swap, cosa que por lo que lei vos no queres. Entonces pone especificar manualmente

BIEN!!! LO QUE QUERIA SABER!!!   no quiero usar un swap en una flash....

entonces me queda seguir lo q me indico pablo.s menos lo del swap... y por ultimo... (espero... je... )  es necesario poner el tamaño en cada particion?? y si asi fuera... q es lo recomendado para cada una?? Mi pendrive de 8Gb. 

Gracias por la paciencia... :P

---

### Post by guillermolisi on 2009-08-13
> **pablo.s said:**
> No question about it. Be more descriptive
about what implies in the LiveCD installation
on step 4. No way I'm going to do an install
just for orientation's sake, you know what I mean?

PS: My apologies if I sound rude or demeaning, Will.
I posted that message just for reference.

I don't know what is step 4 at all, even reading all the thread along.

Take it easy. Your message sounds very funny for me :), the last paragraph in particular.

PS: Disculpen los demas pero me gusta respetar el protocolo propuesto por el remitente como una buena forma de facilitar la comunicacion.

---

### Post by pablo.s on 2009-08-13
Era un post recursivo el
tuyo y mis transistores 
entraron en un loop.

---

### Post by EnriqueK on 2009-08-13
Otra alternativa es crear con Remastersys un LiveDVD de toda tu instalación con la opción ·"distribuible" , o sea sin configuraciones. Luego usas el pendrive para tener allí tu carpeta de usuario (y las que quieras o puedas) y el resultado  es que vas a tener tu sistema en el Live DVD y tus configuraciones y datos en el pendrive y estos si serán persistentes , obviamente no vas apoder agregar nuevos programas al menos en forma persistente, pero te puedo asegurar que en el Live DVD creado con Remastersys entran muchísimos programas, en mi caso por ejemplo que creo tener todo lo que habitualnebte se tiene y mas, mucho mas, el LiveDVD ocupa un 50% de su capacidad.
Si te inmterese esta alternativa, te puedo dar detalles.

---

### Post by madbyte on 2009-08-13
> **EnriqueK said:**
> Otra alternativa es crear con Remastersys un LiveDVD de toda tu instalación con la opción ·"distribuible" , o sea sin configuraciones. Luego usas el pendrive para tener allí tu carpeta de usuario (y las que quieras o puedas) y el resultado  es que vas a tener tu sistema en el Live DVD y tus configuraciones y datos en el pendrive y estos si serán persistentes , obviamente no vas apoder agregar nuevos programas al menos en forma persistente, pero te puedo asegurar que en el Live DVD creado con Remastersys entran muchísimos programas, en mi caso por ejemplo que creo tener todo lo que habitualnebte se tiene y mas, mucho mas, el LiveDVD ocupa un 50% de su capacidad.
Si te inmterese esta alternativa, te puedo dar detalles.

Gracias por la sugerencia... pero... no quiero seguir causando un endless loop y que se quede con todos los recursos...

---

### Post by pablo.s on 2009-08-13
> **madbyte said:**
> Gracias por la sugerencia... pero... no quiero seguir causando un endless loop y que se quede con todos los recursos...

de 8 GB podés hacer
3 para / y 5 para /home.

Peor me fué con el efecto
Y2K, que estuve una semana
tildado.

---

### Post by madbyte on 2009-08-13
> **pablo.s said:**
> 3 para / y 5 para /home.

*Finally.... I got* it!!!  ehhh... si no fue para tanto!!! :P


RETFIE
....

> MAIN_

---

### Post by madbyte on 2009-08-15
*yeah!!! I did it and just I love it!!!* welcome to Ubuntu!!! :guitar:
[IMG]http://img268.imageshack.us/img268/457/pantallazo1n.png[/IMG]

---

### Post by josecuervo86 on 2009-08-15
Felicitaciones!!

---

