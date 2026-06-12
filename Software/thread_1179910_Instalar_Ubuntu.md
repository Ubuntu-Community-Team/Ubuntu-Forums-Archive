---
title: "Instalar Ubuntu"
date: 2009-06-06
forum: Software
---

### Post by Pablo.ar on 2009-06-06
Hola, descarge ubunto 9.04 y lo que tengo al descomprimir el .rar es un carpeta comun no un archivo iso, si aparece un md5sum, pregunto hay una falla en la descarga o hay que pasarlo a iso, gracias por la ayuda.

---

### Post by Hei Ku on 2009-06-06
No deberías tener un .rar en primer lugar. De donde lo descargaste?

---

### Post by Pablo.ar on 2009-06-06
Ah mira entre en ubuntu.ar y de ahi fui a ubuntu oficial donde lo babe, es la segunda ves que me lo hace ya lo habia bajado anteriormente con bittorent y me paso lo mismo, me sale un archivo rar para descargar y cuando lo descomprimo una carpeta ubuntu-9.04-desktop-i386 por eso preguntaba si es que tenia que pasarlo a iso.

---

### Post by Hei Ku on 2009-06-06
Desde ubuntu-ar.org? Te tiene que llevar a una pagina que te baje un archivo .iso.

Me arriesgo a decir que tenes configurado que te oculte las extensiones de archivo conocidas y que el Winrar te lo muestra como archivo rar, pero en realidad es un archivo .iso.

---

### Post by Pablo.ar on 2009-06-06
Bien y ¿cual seria la solucion a donde voy o que puedo modificar para que lo muestre iso?.

---

### Post by Pablo.ar on 2009-06-06
Fui a propiedades y en archivo dice ISO 9660 joliet archive es tal cual tu dices el rar me lo oculta o cambia al iso, la verdad es que no se que se debe hacer para que lo muestre.

---

### Post by guillermolisi on 2009-06-06
> **Pablo.ar said:**
> Bien y ¿cual seria la solucion a donde voy o que puedo modificar para que lo muestre iso?.
Panel de Control - Opciones de Carpetas - Ver

Desmarca el checkbox que dice "Ocultar extensiones de archivos para tipos de archivos conocidos"

---

### Post by Pablo.ar on 2009-06-06
Si hice eso y tube que hacer modificaciones a el winrar porque el iso esta integrado a este, ahora tengo el CD grabado con alcohol, despues voy a ver como anda, gracias por la ayuda, para la instalacion cuanto del disco toma tengo 2 discos uno C y otro E y quiero istalarlo en este ultimo ¿se puede hacer sin problemas? conbiene que se particione solo o hacer las particiones de manera manual?, quiero dejar algo para guardar archivos de windows. Bueno la verdad es que ando como ciego nuevo, ire viendo de apoco. Gracias.

---

### Post by Hei Ku on 2009-06-06
Como ya tienes particiones, tienes que hacer las particiones manualmente. No puedes aprovechar las de Windows, porque el formato de Linux es diferente. Si queres usar el espacion que ahora tenes en el disco E, entonces te convendria borrar esa particion desde Windows, dejarla como espacio sin particionar y al instalar Ubuntu, decirle que utilice el espacio libre. A partir de ahi el instalador se arregla.
Luego puedes ver desde Ubuntu las particiones de Windows. Hay que habilitarlo manualmente pero no es mas que un par de clicks.

---

### Post by Pablo.ar on 2009-06-07
¿Como se borran las particiones del Disco E desde windows?, disculpa la inorancia, pero del tema de formateo, particiones e instalar SO no conosco nada. Gracias

---

### Post by Hei Ku on 2009-06-07
En las herramientas de administracion de la PC, hay una que es administrador de discos. Desde ahí, deberías poder hacerlo. Si no, consulta con la persona que te la instaló.

Si alguien mas quiere ayudar, bienvenido. Yo hace mucho no instalo o administro un windows.

---

### Post by Pablo.ar on 2009-06-07
Gracias creo que de apoco le tomare la mano, me lo tomare con calma hasta estar seguro, mil gracias.

---

### Post by LaVikinga on 2009-06-09
> **Pablo.ar said:**
> Si hice eso y tube que hacer modificaciones a el winrar porque el iso esta integrado a este, ahora tengo el CD grabado con alcohol, despues voy a ver como anda, gracias por la ayuda, para la instalacion cuanto del disco toma tengo 2 discos uno C y otro E y quiero istalarlo en este ultimo ¿se puede hacer sin problemas? conbiene que se particione solo o hacer las particiones de manera manual?, quiero dejar algo para guardar archivos de windows. Bueno la verdad es que ando como ciego nuevo, ire viendo de apoco. Gracias.

Hola, qué tal? Estuve leyendo este post y veo que me pasa lo mismo que te pasó en un principio. Quisiera saber qué modificaciones le hiciste al .rar, ya que aún habiendo desmarcado "Ocultar extensiones...", no puedo ver la imagen .iso. 
Muchas gracias! 
Saludos!

---

### Post by pablo.s on 2009-06-09
Los archivos .ISO los toma
WinRAR, pero no son RAR.
El problema radica en la
asociacion de extensiones:
cuando se instala WinRAR,
al final pregunta si el
usuario desea asociar tal
y cual archivo para ser abierto
con WinRAR, entre ellos están
las imagenes .ISO, pero no
porque los vaya a poder grabar
a CD, sino para poder ver los
contenidos.
Si bajás la .ISO de Ubuntu,
tenés que grabarla en un CD
con algún programa de quemado,
por ejemplo CDBurnerXP.

---

### Post by LaVikinga on 2009-06-09
Muchas gracias Pablo. Entonces ahora me surge la siguiente duda: Yo justamente lo que había hecho es bajar la .iso desde Ubuntu, y al querer grabarla en un CD, vi que la misma está con formato .rar. Tengo que volver a bajarla? O cómo puedo hacer para que no me lo transforme en un .rar? (Considerando que el .rar ya está instalado en la máquina, con la configuración que se le puso en su momento.
Saludos! (Y disculpen mi ignorancia, recién empiezo con todo esto...)

---

### Post by pablo.s on 2009-06-09
Abrís el programa de
grabación de CD. Elegí
grabar imagen .ISO en
el menu (también puede
aparecer como abrir
imagen, dado que hay 
mas tipos de imagen).
Ahi te va a dar para
abrir un archivo y ahí
elegís el archivo que
tenés como RAR, pero es
.ISO y lo grabás.
Cerrá el programa de
grabación, reiniciá la
maquina y entrá en la
BIOS (con F2, o con la
tecla Supr).
Después cerciorate donde
está la opción para que
arranque desde CDROM, o
sea que el primer disco
de la cola sea la lectora.

Si llegaste a este paso,
reinicias la maquina con
el CD de Ubuntu en la
lectora y va a cargar el
LiveCD.

---

### Post by LaVikinga on 2009-06-09
Infinitas gracias!!!!!!!!!!!!!! Buenísima y muy específica tu explicación!!! 
Muchas gracias nuevamente!!!
Lo malo es que me larga un error cuando intenta iniciar el LiveCD, será problema del DVD? "Disk error BB, AX = 4200, drive 82"

---

### Post by pablo.s on 2009-06-09
El error puede deberse
a dos factores:

a) Lo has grabado en
una velocidad muy alta
(digamos 24x).
Cuando grabas imagenes
.ISO se recomienda que
se grabe a 4x ó 2x.
¿Por qué? Por la razón
que si la grabadora
comete el minimo error
en la grabación, todo el
disco se va al garete.

b) El disco que utilizaste
es de baja calidad (Eso es
muy discutible).

---

### Post by LaVikinga on 2009-06-09
No lo grabé a la máxima velocidad, porque ya tengo como costumbre no hacerlo, justamente por lo que me comentaste, pero tampoco lo hice a tan baja velocidad. 
Con respecto a la calidad, la verdad que no había tenido problemas antes con estos DVDs. 
Tendré que intentar volver a grabar entonces. Cuando termine y reinicie, te cuento cómo me va.
MUCHAS GRACIAS POR TENERME PACIENCIA!

---

### Post by LaVikinga on 2009-06-09
No! Grabé otro DVD, a la mínima velocidad, y salta el mismo error. Supongo que es por el formato .rar, es lo único de lo que puedo sospechar...

---

### Post by pablo.s on 2009-06-09
Entonces tendrias
que bajar la .ISO
otra vez y comprobar
la integridad para
ver si bajó bien.

¿Con qué programa
grabas?

---

### Post by LaVikinga on 2009-06-09
Si, eso iba a hacer...
Estoy grabando con el Nero, que es el que tengo instalado.

---

### Post by milovan1971 on 2009-06-09
Hola, No es un problema ni con el CD/DVD, ni con la lectora. Parece que tenes un problema en el BIOS de la maquina.
Tenes que dejar el disco duro (o discos duros) configurados (no con la opcion "auto"). Fijate que te dice el BIOS, y postealo aca si no sabes que hacer.

---

### Post by LaVikinga on 2009-06-10
Ya hice los test en el sistema y no saltó ningún error...

---

### Post by guillermolisi on 2009-06-10
> **LaVikinga said:**
> Ya hice los test en el sistema y no saltó ningún error...
Disculpen las preguntas pero hay algunas cosas que no me quedan del todo claras.

Exactamente, cual es el link (la URL) desde la cual bajas esa supuesta imagen ISO ?

La imagen ISO que estarias bajando es de un CD o de un DVD ? (el tamaño del archivo nos dara la respuesta)

Cuando usas Nero para quemar el CD/DVD, que opciones utilizas para lograr el cometido ?

Como media, usas DVD o CD ?

---

### Post by LaVikinga on 2009-06-10
Ah! Lo que veo es que nunca les dije la máquina que tengo, a ver si hay algo que pueda estar influyendo. Es una portátil Dell Inspiron 1420, Core 2 Duo, 250Gb Disco, 2Gb Memoria. Cuando la recibí, traía Vista, y luego un Técnico le instaló el XP. Posteriormente empezó a aparecer un problema que supuse, era del teclado, ya que repentinamente se cuelga como si hubiera una tecla apretada de manera continua. Le hice todos los tests y demás, para ver si Dell tendría que cambiar el teclado, pero dieron bien. Saltó otro error, por lo que me recomendaron reinstalar Windows, y justamente ahora me quería disponer a hacer eso, instalarle a la máquina Vista (porque dispongo del mismo, y para ciertas tareas) y Ubuntu, porque quiero iniciarme con este SO.

---

### Post by LaVikinga on 2009-06-10
El link me lo pasaron en este mismo foro, es [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

La imagen tiene 2,34Gb, por lo que entiendo que es un DVD.

Para grabar, uso Nero Burning ROM, Recorder, Burn Image y después selecciono las opciones correspondientes.

CD o DVD, es indistinto, depende para qué.

---

### Post by LaVikinga on 2009-06-10
Bueno, finalmente resolví el problema, lo que estaba mal era la imagen que estaba bajando! Descargué otra, la grabé en CD, reinicié con el CD puesto y comenzó a correr el LiveCD.
Ahora tengo otra complicación, cuando elijo la opción de probar Ubuntu sin alterar nada, me da error de booteo, y me lleva a reiniciar, pero cuando reinicia, vuelvo a lo mismo, elijo esa opción y salta el mismo error.
Qué puede pasar ahora?

---

### Post by staar on 2009-06-10
cual es exactamente el error? postealo aca para que nos demos una idea de cual es el problema...

saludos

---

### Post by LaVikinga on 2009-06-10
Es que justamente me dice eso, "Error de booteo", y sólo aparece la opción de reiniciar.

---

### Post by LaVikinga on 2009-06-10
"Error reading boot CD", perdón, eso es lo que dice. Pero... si lee e inicia el LiveCD, será problema del CD? Deberé intentar volver a grabarlo???

---

### Post by pablo.s on 2009-06-10
Si tenés un pendrive
podrías hacer que te
instale desde ahi con
la ayuda de una utilidad.
Eso si tenés uno de mas
de 2 GB.

---

### Post by guillermolisi on 2009-06-10
> **LaVikinga said:**
> "Error reading boot CD", perdón, eso es lo que dice. Pero... si lee e inicia el LiveCD, será problema del CD? Deberé intentar volver a grabarlo???
Ya que es un LiveDVD, podrias probarlo en otra maquina para ver que pasa.

Si funciona bien, me inclino a sospechar de tu unidad de CD/DVD.
Si no funciona bien, es el DVD y/o la unidad donde lo quemaste.

Para resolver la ultima posibilidad, deberias quemar la imagen ISO en otra maquina, que sepas que la unidad optica es confiable. Con el DVD generado asi, probar de nuevo en tu maquina a ver que pasa.

---

### Post by LaVikinga on 2009-06-10
Sigo intentando... Dudo que sea la lectograbadora, ya que intenté cargando la imagen en un pen, y también dio error, por lo que puedo suponer que es la imagen descargada. La que descargué ahora pesa 117Mb, será correcta? Supongo que sí, al menos por el nombre, es la ubuntu-9.04-desktop-i386.iso

---

### Post by Hei Ku on 2009-06-10
Nop. Las iso pesan alrededor de 700MB. 117MB quiere decir que la que bajaste esta mal.

---

### Post by LaVikinga on 2009-06-10
Me parecía muy poco, por eso especifiqué el tamaño! 
No pego una!!! Ahora busco otra.

---

### Post by Pablo.ar on 2009-06-11
Hola, queria contribuir con el tema del winrar por si a alguien le pasa, en mi caso no solo hice modificaciones en la carpeta, sino que en el winrar tambien llendo a Opciones luego Configuracion y entrando en la solapa Integracion hay que desmarcar ISO porque sino lo seguremos viendo en RAR.
Inserte el CD y de las 2 opciones Demo, full y Install inside windows elegi esta, entre en ubuntu cuando renicie y todo joya aunque lo probe desde el cd sin instalar pero cuando apague y entre a el XP, me hizo fallas con el antivirus y el navegador Firefox, asi que como no tengo ni idea para formatear y menos tengo un CD XP la lleve al tecnico, y me instalo el XP, pero no se animo a instalar el Ubunto porque no lo ha instalado nunca, pero le pedi que me dejara en uno de los dos Discos Rigidos un espacio o particion para este, asi que antes tenia El disco C y el E, ahora tengo EL E donde esta el XP y el C donde ban las carpetas o documentos para el XP, ¿debo suponer que es el el D donde instalar Ubuntu?, ¿supongo que debo elegir en la instalacion usar espacio continuo libre y ubunto hara el resto?, bueno gracias por la ayuda.

---

### Post by staar on 2009-06-11
primero que nada, esa denominación para las particiones (disco es uno solo, particiones son las divisiones internas de este) C:, D:, E: es exclusiva de Ventanas, no te asustes si en ubuntu (y en cualquier otro sistema) se llaman diferente...

para saber bien como está tu disco, inicía con el livecd (lo que hiciste antes de probar el SO desde el cd), andá a Aplicaciones > Accesorios > Terminal y escribí ```
sudo fdisk -l
``` y apretá enter, copiá lo que te salga y pegalo acá...

esto es para saber si tu 'técnico' particionó o no el espacio que quedó, porque depende de lo que haya hecho, va a ser la opción de instalación que más te convenga...

saludos

---

### Post by Pablo.ar on 2009-06-13
Disculpa la tardanza pero la primera vez cometi el error de instalarlo con wubi en windows y me hizo un par de desastres en windows asi que tube que mandar a intalarlo devuelta, ahora estoy llendo por fuera de windows, esto es lo que salio al ir Aplicaciones> Accesorios> Terminal> sudo fdisk-l

ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ 

La verdad es que no se si sirve de algo pero dice que el comando no a sido creado.

Como decia tengo 3 particiones, en donde en el E esta el Windows xp instalado en el C se estan instalando las carpetas ¿se supone que tomara el D que es el que esta libre si uso la opcion que el eliga la mayor parte libre continua? o algo asi.

---

### Post by Hei Ku on 2009-06-13
fdisk -l

tenes que dejar un espacio despues de fdisk

---

### Post by Pablo.ar on 2009-06-13
Disco/dev/sda: 250.0 GB, 250059350016 Bytes.
255 cabezas, 63 sectores/pistas, 30401 cilindros.
Unidades= cilindros de 16065 *512= 8225280
Identificador de disco 0c9dfa9dfa

Disposit.   Inicio   Comienzo     Fin       Bloques       Id      Sistema
/dev/sda1                   1          15935    127997856    7      HPFS/NTFS
/dev/sda2              15936        30401    116190112+  f       W95 Ext'd (LBA)
/dev/sda5              15936        30400    116190081    7       HPFS/NTFS

Disco/dev/sdb:160 Gb 160041885696 Bytes
255 cabezas, 63 sectores/pistas 19457 cilindros
Unidades= cilindros de 16065 *512= 8225280 bytes
Identificador de disco: 0x3c483c47

Disposit.   Inicio   Comienzo     Fin       Bloques       Id      Sistema
dev/sdb       *              1        19456    156280288     7       HPFS/NTFS

---

### Post by staar on 2009-06-13
bien, tenés, físicamente, dos discos duros, el primero con dos particiones, y el segundo con una sola...
por lo que se ve, Ventanas está ocupando todo el segundo disco, y la partición que quedaría para ubuntu es una lógica del primer disco, lo malo es que tu 'técnico' formateo esa partición en NTFS (el sistema de archivos de windos) por lo que no nos sirve, además ubuntu necesita de dos particiones (una para el sistema y otra para la memoria de intercambio o swap)

mi recomendación sería que inicies con el livecd, vayas a Sistema > Administración > Editor de particiones, y elimines (click derecho > eliminar o borrar, no recuerdo) la partición lógica que te creo tu 'técnico', te vas a dar cuenta cual es, porque va a estar rodeada de un marco celeste (que representa la partición extendida que contiene a la lógica), y después elimines también la extendida (tenés que hacer click derecho sobre el marco celeste), dejando, en tu disco de 250 GB, solo la primera partición, de tipo primaria, que sería la que Ventanas nombra C:, y el resto del disco como espacio libre sin particionar...

después, en la instalación de ubuntu, seleccioná la opción usar el espacio libre, y el instalador solito va a hacer las particiones que necesita ubuntu....

saludos

---

### Post by Pablo.ar on 2009-06-14
Bien, ya esta hecho, en un principio comense a dudar porque decia que tenia 3 Gb en used y me parecio raro que windowos estubiera ahi asi que fui por el XP y mirando no habia nada asi que lo borre dejando libre, para ubuntu. 

PD: Me olvidava de preguntar ¿cual seria la mejor forma de instalarlo?.

---

