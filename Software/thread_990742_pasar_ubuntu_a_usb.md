---
title: "pasar ubuntu a usb"
date: 2008-11-23
forum: Software
---

### Post by tsueseres on 2008-11-23
hola, instale ubuntu en un disco duro extraible(usb) pero 

como le ago para clonar todos mis datos de ubuntu de lo que tengo en mi computadora de escritorio y pasarlos al disco duro externo para asi poder llevar siempre con migo todas mis cosas

---

### Post by c4d0rn4 on 2008-11-23
La carpeta /home/usuario tiene tus preferencias, si te fijas hay montones de .CarpetaDeProgramas (el punto adelante las hace hidden)

Creo que copiandolas y sobreescribiendo las que tienes estaría, pero tienes que darle permiso al usuario para que puede acceder y usar los archivos.

----------------

Si la pregunta era otra,
clonar textualmente todo, tengo entendido que con el comando dd podés hacerlo. Y te hubiera ahorrado instalar ubuntu en el disco externo.

jamás lo usé, así que mucho más no puedo decirte. Encontré rápido un link [http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/](http://www.mckeay.net/2004/10/18/using-dd-to-clone-a-hd/) espero sirva.

---

### Post by luks911 on 2008-11-23
Otra posibilidad, de acuerdo a mis limitados conocimientos, es generar una iso de tu sistema de la PC de escritorio con Remastersys, que es bastante sencillo y podés elegir qué datos incluir de tu home (la herramienta es para hacer backup). Y luego con esa iso instalar en el disco extraible, ya que la iso que vas a lograr es como el disco original de Ubuntu pero con toda las modificaciones que le hiciste y hasta con tu home. 

[Acá]("http://liberandotumente.com.ar/2008/08/13/remastersys-crear-live-cd-personalizado-de-ubuntu/")[0] hay una explicación de cómo usarlo. También incluye un pequeño menú gráfico.

[0] [http://liberandotumente.com.ar/2008/08/13/remastersys-crear-live-cd-personalizado-de-ubuntu/](http://liberandotumente.com.ar/2008/08/13/remastersys-crear-live-cd-personalizado-de-ubuntu/)

---

### Post by tsueseres on 2008-11-23
ya lo intente con las 2 pero no funciona estoy intentando con el acronis desde windows creando la imagen del SO y luego restaurandola en el disco duro extraible pero me sale el problema del grub error 17 

lo que ice fue pasar de nuevo el grub al  disco duro extraible con live cd pero cuando arranca carga dentro de el mismo el ubuntu del disco duro interno y nada del externo. creo que esto sucede por los enlaces ha los directorios

---

### Post by EnriqueK on 2008-11-24
Con cualquier clonador que uses vas a tener problemas del Grub y además vas a tener que modificar el fstab, siempre usando el Live Cd posteriormente de haber realizado la clonación . Algo que en este momento se me ocurre es hacer una instalación básica con el CD de instalación poniendo el grub en el disco extraíble y luego de terminar, usas EL Live Cd para copiar los archivos de configuración del Grub y además el archivo /etc/fstab , luego hacés la clonación con Acronis y nuevamente con el Live CD reemplazas los archivos que antes respaldaste, por las dudas antes de clonar con Acronis o el que sea, estimo que sería conveniente quitar el montaje automático de las particiones, esto también podría causar conflictos al no encontrar los puntos de montaje de la instalación original.
Si con esto no funciona, creo que lo mejor es usar Remastersys con la opción de respaldo distribuible y así lo podés instalar sin problemas, la carpeta de usuario aprovechá de ponerla en otra partición.
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by faktorqm on 2008-11-24
Esta herramienta va como piña, la usamos el otro dia en la tribu.

[http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)

Si te tira la bronca de que no arranca, tenes que hacer

```
sudo apt-get install python2.5-dbus
```

Salu2!!

---

### Post by luks911 on 2008-11-24
> **faktorqm said:**
> Esta herramienta va como piña, la usamos el otro dia en la tribu.

[http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)

Si te tira la bronca de que no arranca, tenes que hacer

```
sudo apt-get install python2.5-dbus
```

Salu2!!

Ya que estamos pregunto: ¿esa aplicación hace lo mismo que la opción que viene por defetco en Intrepid para crear un USB booteable? ¿Podría usarse Remastersys y la iso resultante usarse para generar el USB?

Saludos

---

### Post by faktorqm on 2008-11-24
> **luks911 said:**
> Ya que estamos pregunto: ¿esa aplicación hace lo mismo que la opción que viene por defetco en Intrepid para crear un USB booteable?

Si

> **luks911 said:**
> ¿Podría usarse Remastersys y la iso resultante usarse para generar el USB?

Saludos

En realidad no se, digamos, ustedes se quieren hacer un ubuntu live con sus datos del /home verdad? La cosa con eso es que primero el usb les va mucho menos que lo que iba a durar desde el principio. Segundo, lo que hay que hacer es crear un imagen del cd live con tu /home... no se nunca lo hice. Prestenme un pendrive de 2 gb y les hago un tuto xD

Salu2!

---

### Post by luks911 on 2008-11-24
> **faktorqm said:**
> En realidad no se, digamos, ustedes se quieren hacer un ubuntu live con sus datos del /home verdad? La cosa con eso es que primero el usb les va mucho menos que lo que iba a durar desde el principio. Segundo, lo que hay que hacer es crear un imagen del cd live con tu /home... no se nunca lo hice. Prestenme un pendrive de 2 gb y les hago un tuto xD
Salu2!

Jaja... preguntaba para saber nomás. Supongo que el Remastersys debe servir entonces. Pero, no, no voy a usar mi penoso mp3 para eso.

Gracias y saludos :lolflag:

---

### Post by EnriqueK on 2008-11-24
Me parece que se está refiriendo de pasar su instalación a un DD externo USB y no a una memoria Flash USB o también llamada Pendrive, son cosas distintas, aunque ambos sean USB.
Hace poco hice el siguiente experimento:
1.- Creo un Live DVD de toda mi instalación con Remastersys sin datos personales-
2.- copio mi carpeta de usuario a mi pendrive formateado en EXT3 mediante el comando cp -a
3.- Corro mi Live DVD y una vez arrancam creo un nuevo usuario con mi nombre y contraseña, como esta operación me genera una carpeta de usuario igual a la mia, lo que hago es borrarla y en ese lugar pongo un enlace simbólico a mi verdadera carpeta de usuario situada en el pendrive.
4.- Cambio de usuario y el sistema arranca con todas mis configuraciones y así puedo usar mi Ububtu con la ventaja de que todos los cambios en documentos y configuraciones serán persistentes por que se almacenarán en el pendrive.
Con los debidos ajustes, puedes aplicar este criterio para instalar mediante un DVD creado con Remastersys en una partición de tu DD externo y en otra partición hacer una copia de tu carpeta de usuario.

---

### Post by tsueseres on 2008-11-24
deecho si me refiero a pasar todos mis datos del disco duro al dico duro externo(extraible)

bueno tengo una pregunta con respecto a donde se guarda la informacion de los programas 

por ejemplo digamos que bajo un deb o un tar el caso es que se va a instalar un programa.

al momento de instalarlo se guarda todo incluidas las modificaciones y los ejecutables en la carpeta del usuario ?

o

las configuraciones a la carpeta usuario y lo demas a otras carpetas?

---

### Post by luks911 on 2008-11-24
> **tsueseres said:**
> deecho si me refiero a pasar todos mis datos del disco duro al dico duro externo(extraible)

bueno tengo una pregunta con respecto a donde se guarda la informacion de los programas 

por ejemplo digamos que bajo un deb o un tar el caso es que se va a instalar un programa.

al momento de instalarlo se guarda todo incluidas las modificaciones y los ejecutables en la carpeta del usuario ?

o

las configuraciones a la carpeta usuario y lo demas a otras carpetas?

Opción 2. Los ejecutables, los programas en sí, van a /, por lo general a /usr/bin (seguro alguien puede explicarlo con más detalle que yo).
Mientras que las configuraciones de esos programas sí van al home, a la carpeta del usuario. Hay carpetas ocultas en el /home con esos datos. Por ejemplo, en /home/nombre_de_usuario/.mozilla están las configuraciones de firefox, en realidad en /home/nombre_de_usuario/.mozilla/firefox porque en esa misma carpeta .mozilla se deben guardar datos de thunderbird en caso de que lo tengas. Como fuere, en esa carpeta firefox van a estar tus marcadores, extensiones, historial, etc, etc. Y así con otras aplicaciones.
De allí la recomendación de tener el home en partición aparte. Porque en caso de reinstalar hay que reinstalar los programas, pero se mantienen intactas sus configuraciones, o sea los datos que pudiste haber cambiado.

---

### Post by tsueseres on 2008-11-24
deecho si me refiero a pasar todos mis datos del disco duro al dico duro externo(extraible)

bueno tengo una pregunta con respecto a donde se guarda la informacion de los programas 

por ejemplo digamos que bajo un deb o un tar el caso es que se va a instalar un programa.

al momento de instalarlo se guarda todo incluidas las modificaciones y los ejecutables en la carpeta del usuario ?

o

las configuraciones a la carpeta usuario y lo demas a otras carpetas?

---

### Post by tsueseres on 2008-11-25
rayos me estoy frustrando.... pero tengo k lograr esto

bueno ya descarte lograrlo por acronis tmb descarte con el comando dd ya que dura demaciado y copea cada sector incluso donde esta vacio 

estoy ahorita volviendo  remastersys ya hice remastersys backup pero el iso solo pesa 1.9gb y checke mi datos y llegan asta 4.5

alguna idea de por k pasa esto?

bueno como restauro con remastersys?

---

### Post by EnriqueK on 2008-11-25
Simplemente graba la ISO usando por ejemplo Brasero, la forma mas simple es click secundario sobre la ISO -->Abrir con--> Brasero , lo que queda es usar  el Live DVD creado  para hacer una instalación tal como si fuera un Live CD normal.
En mi caso hice un Live DVD de mi instalación sin datos personales y la ISO pesa unos 2 gigas, mientras que mi instalación es de unos 7 Gigas, lo que pasa es que hace compresión de datos no esenciales para que funcione en modo Live .
Cuando hagas la instalación debes usar el msimo Login y Password .
Mas no te puedo ayudar por que no estás indicando que opción usaste, si con datos personales o sin ellos.

---

### Post by tsueseres on 2008-11-26
> **EnriqueK said:**
> Simplemente graba la ISO usando por ejemplo Brasero, la forma mas simple es click secundario sobre la ISO -->Abrir con--> Brasero , lo que queda es usar  el Live DVD creado  para hacer una instalación tal como si fuera un Live CD normal.
En mi caso hice un Live DVD de mi instalación sin datos personales y la ISO pesa unos 2 gigas, mientras que mi instalación es de unos 7 Gigas, lo que pasa es que hace compresión de datos no esenciales para que funcione en modo Live .
Cuando hagas la instalación debes usar el msimo Login y Password .
Mas no te puedo ayudar por que no estás indicando que opción usaste, si con datos personales o sin ellos.

lo que quiero es ponerlo en un disco duro estraible no en un dvd

como que si con datos personales

yo solo le puse sudo remastersys backup

---

### Post by EnriqueK on 2008-11-26
Entonces has hecho un backup completo o sea incluye datos personales, la ISO quedó ubicada en /home/Remastersys , lo que debes hacer es usar esa ISO (que una imágen de DVD) para grabarla en un DVD y seguidamente a ese DVD lo usás para instalarlo en tu disco extraíble, o sea de la misma manera que si fuera el CD original que distribuye Canonical para instalar Ubuntu. En resumidas cuentas, no estarías haciendo una clonación de una instalación, sino una instalación nueva pero con todos los programas que quieras, esta diferencia es fundamental, por que no vas a tener problemas con el fstab, ni con los puntos de montaje ni con el grub que debes instalarlo en el disco extraíble y no en MBR de DD del equipo.
Otra cosa, una vez grabada la ISO en un DVD, debes hacer una limpieza de los archivos temporales que genera el proceso, estos archivos pesan bastante y además va a interferir en caso de que quieras repetir el proceso de crear una nueva ISO.

---

### Post by faktorqm on 2008-11-26
Che tanto lio si es una pavada lo que tienen que hacer! Instalate un ubuntu normal comun y corriente en tu pendrive o disco extraible o lo que quieras, y despues copia el /home y listo. Despues instalas las aplicaciones y ya. Salu2!

---

### Post by EnriqueK on 2008-11-26
Puede que tengas razón, es mas, tal vez ni le convenga hacerlo por que pretender tener una instalación en un DD externo para poderlo llevar a cualquier parte, es algo utópico, por que no es para nada seguro que el dueño de un equipo te autorice a que bootees su PC, a menos que te tenga mucha confianza o que sea un ignorante total, yo al menos, jamas permitiría que alguien haga un booteo en mi equipo ya sea con un Live Cd ni con un DD externo.
Pero por otra parte, Remastersys es una herramienta de lo mejor que existe y vale muy bien la pena dedicarle algo de tiempo para saber manejarla.

---

### Post by tsueseres on 2008-11-30
ok porfin queme el disco creado de remastersys y veo que funciona muy bien ya lo instale en el discoduro externo y logre bootear en otras computadoras

tmb lo logre con acronis nomas que hay no estoy muy seguro si tuve que agregarle el grub 

ahora lo que estoy biendo es como detecta los drivers en otras computadoras

---

### Post by tsueseres on 2008-11-30
ok tengo un problema con los graficos como que si detecta la targeta de graficos cuando lo conecto a otra computadora pero no puedo activar los efectos extras ya he reconfigurado el xorg varias veces y nada 

alguien sabe como arreglar esto

---

### Post by EnriqueK on 2008-12-01
Si vas a estar booteando en diferentes PCs, no debes instalar los drives de la gráfica, ponete el caso que le cargas drivers Nvidia y si luego lo ponés a bootear en otra PC con gráfica ATI, con seguridad que el equipo arrancará sin entorno gráfico, obligádote a meter mano a configuraciones avanzadas , desinstalar drivers anteriores , etc, etc, por esta razón es que Remastersys al crear la ISO, no copia los drivers de la gráfica, justamanete para ser lo mas "universal" posible.

---

### Post by tsueseres on 2008-12-01
> **EnriqueK said:**
> Si vas a estar booteando en diferentes PCs, no debes instalar los drives de la gráfica, ponete el caso que le cargas drivers Nvidia y si luego lo ponés a bootear en otra PC con gráfica ATI, con seguridad que el equipo arrancará sin entorno gráfico, obligádote a meter mano a configuraciones avanzadas , desinstalar drivers anteriores , etc, etc, por esta razón es que Remastersys al crear la ISO, no copia los drivers de la gráfica, justamanete para ser lo mas "universal" posible.

ahorita nomas estoy booteando en una computadora, asi que si me puedes esplicar como hacer eso

---

