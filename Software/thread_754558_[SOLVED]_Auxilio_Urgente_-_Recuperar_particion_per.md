---
title: "[SOLVED] Auxilio Urgente - Recuperar particion perdida"
date: 2008-04-13
forum: Software
---

### Post by Elrengo on 2008-04-13
Les comento mi situacion, y espero q puedan ayudarme, como otras veces lo han hecho ya que los datos que perdi (espero que no) son de gran importancia para mi, soy bastante nuevo en esto de ubuntu, y investigando un poco hoy encontre ua forma de tener instalado mi UBUNTU en mi pen drive, estaba siguiendo los pasos del tutorial q eran bastante sencillos, y q llegue a comprender bastante.
Cuando termine de particionar mi PEN DRIVE q mi live cd de UBUNTU lo reconocia como **/dev/sdb**  el tutorial me pedia q formatee las 2 particiones antes creadas, las /dev/sdb1 y la /dev/sdb2, pero al intentar formatear la segunda particion, me equivoque, (asumo total responsabilidiad en esto) y formatee la particion **/dev/sda2** q eran los datos de mi disco rigido en formato NTFS, ya q todavia estoy en periodo de migracion (no completa).

El comando q inserte erroneamente es:

**[COLOR="Red"]mkfs.ext2 -b 4096 -L casper-rw /dev/sda2[/COLOR]**

el link del tutorial es este: 
 
[COLOR="Blue"][http://www.rodolinux.com.ar/node/43]("http://www.rodolinux.com.ar/node/43")[/COLOR]

ESPERO Q ME PUEDAN AYUDAR; muchas gracias matias

---

### Post by alejandro.mc on 2008-04-14
Antes del "Antes que nada" otro antes que nada: En mi opinion deberias de dejar de agarrarte la cabeza, tomarlo con calma y empezar a entender que lo que hiciste es dificilmente reversible.

Antes que nada te aclaro que soy amateur y mi opinion deberia ser reevaluada por alguien mas. Dado que vi que muchas personas leyeron tu post y no contestaron, pense "bueno vamos a tirarle un salvavidas pobre muchacho".

Cuento con que sepas hacer algunas cosas como manejar espacios de disco con el CD Ubuntu LiveCD e instalar programas con Synaptic.

Bueno a ver. Como yo lo veo tenes dos opciones (una de las opciones requiere que sepas ingles o que un buen samaritano traduzca la pagina para vos). Y esto es si de verdad es necesario recuperar esos documentos (de lo contrario es un flor de enchastre y tiempo en vano)

Opcion A. 

1. Hacer un espacio EN TU PARTICION ACTUAL DE UBUNTU con el Ubuntu LiveCD (es decir liberar un espacio), pero NO simplemente liberarlo para que quede adherido a tu particion NTFS, sino que LIBERAR EL ESPACIO Y CREAR UNA PARTICION CON ESE ESPACIO, pues alli vas a instalar una copia de Windows.
2. Instalar en esa particion nueva Windows. 
3. Instalar en ese Windows esto: [http://www.diskinternals.com/](http://www.diskinternals.com/) o un programa similar de esos que hay de sobra en internet. Yo hace mucho que no uso windows pero te recomiendo que bajes el programa ese o uno similar (googlea un poquito) Voy a ponerlo de tal forma que no parezco que estoy a favor de algo de lo que no estoy: para conseguir ese u otro programa similar vas a tener que hacer uso de vias "alternativas". Lo recomendable es que te bajes el programa usando torrentes (GUIÑO GUIÑO)
4. Usar el programa para recuperar aquello que se pueda recuperar si llegara a ser posible.

Opcion B. 

ESTE PROGRA NO LO USE Y DE HECHO NO LO HE VISTO NI FUNCIONAR NI LO HE VISTO. NO SE COMO ES SU INTERFASE NI COMO OPERA.

1. En tu Ubuntu (del cual asumo escribiste este post obviamente) instala el programa "testdisk" a través de Synaptic.
2. No se en que versión esta funcionando, ni si tiene GUI (es decir que funcione graficamente en Gnome). La ultima vez que oí de eso funcionaba desde consola. Es decir que una vez instalado lo vas a tener que abrir desde la terminal (consola) y probablemente correr completamente desde la terminal.
3. Hay un How-To (como mencione anteriormente está en Inglés) acá: [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922) Y tiene un año de antiguedad y esta aparentemente hecho por alguien no tan experto. De todas formas creo que vale la pena indagar un poquito mas a cerca de este programa ya que en Gutsy y Hardy viene defaulteado todavia en los repositorios, quiere decir que debe funcionar.

Te deseo mucha suerte, y aunque no sirva de nada te digo que estuve donde estuviste y muchos deben haber estado tambien. 

LES PIDO A QUIENES LEAN ESTO Y SEPAN ALGO (pues yo me cosidero un Noob) POR FAVOR COMENTEN y CORRIJAN LO QUE ESCRIBI.

Saludos a todos!

---

### Post by Elrengo on 2008-04-14
Aclaro que lo que hice, de acuerdo a lo que entiendo de informatica fue cambiar el sistema de archivos de NTFS a EXT2, y q al hacerlo formateo la particion, pero lo q es seguro es que no sobreescribio los datos, ya que era una particion de aporx 250 GB y tardo en realizar la operacion 30 segundos, Lo q voy a intentar hacer ademas de las posibles soluciones q me pasaron es cometer el mismo error q cometi antes con otro disco q tengo tirado (de 4gb), y correr programas de recuperacion de datos a ver q pasa, pero solo conozco 1 en plataforma windows, q segun parece reconoce particiones EXT2 y EXT3, 

MUCHAS GRACIAS POR SU RESPUESTA

Y SI OFENDER; ESPERO MAS,

---

### Post by marianom on 2008-04-14
No sean tan duros, era domingo y no griten que hoy es lunes.

El documento base para la recuperación en el wiki es [este]("https://help.ubuntu.com/community/DataRecovery"). Como dijiste que tu fuerte no es el inglés busqué algún recurso en castellano y por suerte [la página de TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_ES") está en castellano y bastante claro. 

Sugiero este approach: lee de punta a punta la página y volvé acá a plantear las dudas que se te presenten antes de proceder. TestDisk está en los repos así que instalarlo es tan facil como instalar cualquier otro programa en ubuntu: testdisk te va a decir si los archivos todavía existen en tu disco o no, una vez comprobado veremos que se puede hacer.

---

### Post by marianom on 2008-04-14
Con respecto al tema de si el inglés es o no tu fuerte, parece que me confundí con otro thread :)

---

### Post by pante on 2008-04-14
No toques la partición a recuperar por ningún motivo antes de saber qué hacer.

---

### Post by faktorqm on 2008-04-15
Hola, puede ser que solo hayas escrito la tabla de particiones, sin borrar los datos. Para este tipo de casos lo que te recomiendo, es bajate y graba en un cd el hiren-s boot cd ([http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)) y ahi elegis el Ontrack Easy Recovery Pro 6.10, que es un recupera particiones.

Lo que hace eso es, vos le decis que particion perdida queres recuperar, si es ilegible o no esta formateada te pregunta el tamaño, y te va preguntando "datos". Entonces va y busca posibles archivos en la extension, si encontro muchos, quiza puedas volver todo atras. Si no encontro nada, probaria con todos las recovery tools de ese cd que estan buenisimas. A veces, y sobre todo en informatica, nunca sabes quien te va a salvar el cu*o, y no todo es lo q parece. Acordate de eso. 

Salu2!!!!

---

### Post by Mauro22 on 2008-04-15
El disco sda2 estaba montado?? 

Si es asi no te hubiera dejado formatearlo, o no?

---

### Post by Tosh78 on 2008-04-15
A mi me paso algo similar hace un tiempo y pude recuperar absolutamente todo. El tema es que no conozco ningun programa de Linux para recuperar datos ya que entre hace poco a este mundo. Sin embargo, si queres, te paso el nombre del programa que use en Wingarch para recuperar los datos (ahora no lo tengo a mano y no me lo acuerdo).
Avisame.

---

### Post by faktorqm on 2008-04-16
mauro22: tengo entendido que lo podes hacer igual, solo que te saltan 15000 carteles de que no lo hagas si tenes la particion montada, pero te lo deja hacer igual. por que? todavia no lo se :D

---

### Post by Mauro22 on 2008-04-16
Jeje, Ok. Gracias por aclarame la duda!

---

### Post by Elrengo on 2008-04-20
Muchisimas gracias a todos, por suerte mis datos ya estan en mi disco otra vez, les voy a confesar algo, me considero un buen usuario de windows (aclaro que no me agrada, pero el mercado lo impone, soy tecnico) y los recupere desde esta plataforma con el GET DATA BACK, pedi auxilio aca porq la particion la cambie a EXT2, aunque este soft me los recupero sin porblema alguno, pero estoy porbando esto nuevo para mi de ubuntu, hasta ahora de mil maravillas, lo q mas me cuesta es instalar aplicaciones (fuera de synaptic por suspuesto), pero hasta ahora es todo muy sencillo y grcias a uds mucho mas.


ETERNAMENTE AGRADECIDO

LOS MOLESTARE EN OTRA OPORTUNIDAD y cuando aprenda mas, volvere a este foro no solo como un AHOGADO, sino tambien como SALVAVIDAS

---

### Post by faktorqm on 2008-04-20
OK, todo bien. No te sientas "mal" por tener y/o usar windows. Yo soy avanzado tambien de windows y seria algo mas q un principiante en linux, pero tengo los dos sistemas. (y esto se dio por mera casualidad, si hubiera conocido antes linux y no usaria tanta gente win, chau!, de hecho mi hijo calculo que no lo va a conocer :P) 
El mercado no te impone nada, es lo que queres hacer vos, lo que pasa es que los virus en windows te dan de comer igual que a mi, y como en linux se te corta eso, vos empezas a ver cómo si todos se instalan linux, te quedas cada vez con menos trabajo.
Yo tengo win xp sp2 con el driver para ext3 y el linux con ntfs-3g, tengo 1gb para win creo, 10 para linux, el resto son todas particiones de datos. No pasa nada! No te mandes mas macanas y presta atencion a los comandos :D Salu2!

---

### Post by subject-A on 2009-08-01
> **Elrengo said:**
> Muchisimas gracias a todos, por suerte mis datos ya estan en mi disco otra vez, les voy a confesar algo, me considero un buen usuario de windows (aclaro que no me agrada, pero el mercado lo impone, soy tecnico) y los recupere desde esta plataforma con el GET DATA BACK, pedi auxilio aca porq la particion la cambie a EXT2, aunque este soft me los recupero sin porblema alguno, pero estoy porbando esto nuevo para mi de ubuntu, hasta ahora de mil maravillas, lo q mas me cuesta es instalar aplicaciones (fuera de synaptic por suspuesto), pero hasta ahora es todo muy sencillo y grcias a uds mucho mas.


ETERNAMENTE AGRADECIDO

LOS MOLESTARE EN OTRA OPORTUNIDAD y cuando aprenda mas, volvere a este foro no solo como un AHOGADO, sino tambien como SALVAVIDAS


Hola, quiero aprovecharme del tema de este post ya que sufro de un problema similar.... bueno.. soy novato y perdí la info de una partición, bueno.. un disco...

intentando montar una unidad (otro hdd) que estaba formateado en ext4 apliqué los siguientes pasos:

        - sudo mkdir /media/datos

        - sudo mkfs.ext4 /dev/sdb1

        - sudo gedit /etc/fstab
            -> /dev/sdb1 /media/datos ext4 defaults 0 0 (última línea)

        - sudo mount -a

        - sudo chmod 777 /media/datos

estoy sumamente seguro que metí la pata al escribir este comando:
- sudo mkfs.ext4 /dev/sdb1

bueno, mi pregunta es... podré recuperar los datos usando el testDisk que describen aquí?, ya lo ejecute y llegué hasta la parte de la "búsqueda profunda", al terminar no me aparece nada que indique que se pueda recuperar... sniff....

si usé el comando mkfs, sería imposible recuperar algo, es posible hacerlo por otro medio??....

quedo atento a sugerencias... 
me disculpo de antemano por si no vi la solución en otro post....

saludos...

---

### Post by guillermolisi on 2009-08-01
No conozco todas las herramientas que puedan estar disponibles para este tipo de tareas de rescate, pero luego de aplicar mkfs a una particion, te diria que no quedo nada de lo que antes habia ahi.

Si solo lo querias montar, no hacia falta correr mkfs, con un simple mount manual o "mount -a" luego de haber editado el fstab incluyendo el segundo disco, era suficiente.

---

### Post by subject-A on 2009-08-02
> **guillermolisi said:**
> No conozco todas las herramientas que puedan estar disponibles para este tipo de tareas de rescate, pero luego de aplicar mkfs a una particion, te diria que no quedo nada de lo que antes habia ahi.

Si solo lo querias montar, no hacia falta correr mkfs, con un simple mount manual o "mount -a" luego de haber editado el fstab incluyendo el segundo disco, era suficiente.


sniff.. me lo temía...

bueno.. queda como experiencia.. al menos no mate al disco duro....

xD

gracias guillermo!

---

