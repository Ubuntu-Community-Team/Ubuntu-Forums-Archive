---
title: "COMO: Instalar Acetone ISO 2 en Ubuntu y Xubuntu"
date: 2007-08-29
forum: Software
---

### Post by faktorqm on 2007-08-29
Hola a todos, bueno, les comento que este programa sirve para manejar todo tipo de imágenes, en cd o dvd. 
Obviamente las ilegales NO. 
Vendría a ser el reemplazo del Alcohol 120% de Windows pero sin la parte ilegal xD
Este programa es nativo de Kubuntu, por lo tanto no expongo cómo se instala, ya que sólo hay que ir hasta la página y bajar el .deb.
La página del proyecto es: [http://www.acetoneteam.org/](http://www.acetoneteam.org/)
Aquí les dejo las features (características) del programa, en inglés y abajo traducidas por mí, por favor, si lo hice mal se aceptan correcciones :D

Features :
	
- Mount / Unmount ISO, MDF, NRG, BIN, NRG (no password required)
- Display showing mounted images
- Automatic Mount, destination is not required
- Convert / Extract / Browse to ISO :
  *.bin *.mdf *.nrg *.img *.daa *.cdi *.xbx *.b5i *.bwi *.pdi
- Play a DVD Movie Image inside Kaffeine / VLC with cover downloader
- Generate an ISO from a Folder or CD/DVD
- Generate / Check MD5 file of an image
- Encrypt / Decrypt an image
- Split / Merge image in X megabyte
- Compress with High Ratio an image in 7z format
- Rip a PSX cd to *.bin to make it work with epsxe/psx emulators
- Service-Menu support for Konqueror
- Restore a lost CUE file of *.bin *.img
- Blank CD/DVD
- Burn ISO / Cue to CD/DVD
- Mount Mac OS *.dmg images
- Retrieve INFORMATION of an image
- El-Torito support to create ISO bootable Cd
- Mount *.iso in a specified folder from the user
- Create a database of images
- Extract the Boot Image of a CD/DVD or ISO

Características:

- Montaje / Desmontaje de formatos ISO, MDF, NRG, BIN y NRG sin necesidad de contraseña.
- Pantalla que muestra las imágenes montadas.
- Montaje automático, sin necesidad de seleccionar un destino.
- Convertir / Extraer / Explorar a ISO desde .bin, .mdf, .nrg, .img, .daa, .cdi, .xbx, .b5i, .bwi, .pdi.
- Reproducir una película en DVD con el programa Kaffeine o VLC con descargador de las carátulas. (*)
- Generar un ISO desde una carpeta o desde un CD/DVD.
- Generar / Chequear un archivo MD5 de una imagen.
- Encriptar / Desencriptar una imagen.
- Separar / Unir una imagen con el tamaño en Mb que deseemos.
- Comprimir con alto nivel de compresión una imagen en formato 7z. (**)
- Traspasar un cd PSX a .bin que funcione con emuladores epsxe/psx.
- Menú de servicio con soporte para Konkeror.
- Restauración de archivos perdidos CUE de imágenes .bin e .img.
- Blanqueo de CD/DVD. (***)
- Grabar ISO / CUE a CD / DVD.
- Montar imágenes .dmg de Mac OS.
- Recuperación de información de una imagen.
- Soporte para El-Torito al crear una imagen de cd arrancable ISO.
- Montar .iso en una carpeta especificada por el usuario.
- Crear una base de datos de las imágenes.
- Extraer la imagen de arranque de un CD / DVD o una ISO.

(*) Descargador de las carátulas se refiere a la de las cajas de los DVD.
(**) Alto nivel se refiere al radio de compresión respecto del archivo original.
(***) Supongo que se refiere a blanquear CD's o DVD's regrabables.

Aquí, las instrucciones: (fueron probadas paso a paso por mi en Xubuntu y en Ubuntu, 32 bits, 7.04 feisty fawn, si, tengo 2 linux, y cuál es?!?)

1) ```
wget http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0%7E3v1ubuntu0_i386.deb
```

2) ```
wget http://www.acetoneteam.org/Archivia/xAcetoneISO2-src_BETA3.tar.gz
```

3) ```
sudo aptitude install fuse-utils libfuse2 mkisofs libqt4-core libqt4-gui libfuse-dev build-essential
```

4) ```
sudo dpkg -i fuseiso_20061017-0~3v1ubuntu0_i386.deb
```

5)```
 tar -zxvf xAcetoneISO2-src_BETA3.tar.gz
```

6) ```
cd xAcetoneISO2-src
```

7) ```
sudo ./installer
```

_SALIDA DEL PROGRAMA_:

```
Welcome to xAcetoneISO2, a gtk port of the KDE AcetoneISO2 software

checking write permissions
user has full permissions to write
installation will now start
3
2
1
Starting installation
please wait

intallation 100%

I will now do a quick test to check most important dependencies

zenity found OK
fusermount found OK
fuseiso found OK


You seem to be able to use most functions of xAcetoneISO2
Please don't forget to visit http://www.acetoneteam.org/manual.html

I suppose everything is OK
Please run xAcetoneISO2 as normal user typing 'acetoneiso2'

The End
```

8 ) Abrir ACETONEISO 2 haciendo click en Aplicaciones, luego en accesorios, luego en ACETONE ISO 2.
Una vez abierto, nos debe mostrar un cartel de que todas las dependencias están bien, (el cartel dice: "All dependencies are installed!") ahí le damos OK.

Si nos pide una contraseña, corresponde la que usamos cuando usamos sudo. (A menos que ejecutemos el X como root, claro)

Una vez hecho esto, ir a la ficha "convert", y luego apretar el botón "Convert Image to ISO".
Allí, nos abrirá un terminal y bajará el programa "poweriso" automáticamente, y luego nos pedirá la contraseña que usamos cuando usamos sudo. 
Luego muestra un cartel de éxito pidiendo que volvamos a hacer click sobre el botón para utilizar la función.
(el cartel dice: "PowersISO succesfully downloaded and installed. Please click again on Convert button")

9) La instalación ha finalizado. Hagan click en la cruz verde en la esquina superior derecha para más opciones. 

**Que lo disfruten!!**:guitar:

---

### Post by leo_rockway on 2007-08-29
no lo conocia al programa, ya entre a la pagina para ver q onda (igual yo tengo kubuntu)

x cierto... el titulo del thread esta mal. de solo pensar en automatix me dan escalofrios :-P

EDIT:
por alguna razon me dice q no tengo fuse-utils instalado, cuando lo acabo de instalar... medio raro.

---

### Post by faktorqm on 2007-08-29
MIL GRACIAS POR AVISAR! w0w!!! PUSE CUALKIER BANANA!!
habia puesto automatix 2, cuando era acetone iso 2.
aparte, el automatix 2 es re facil de instalar jajajajajaja hacer un como sobre eso es cualkiera. bue, salu2!!

---

### Post by Mataca on 2007-08-31
FAKTORQM lee imagenes .ccd ??
Yo tengo un par hechas x mi de unos cds, mas precisamente del indio solari y otro de los heroes del silencio y otros mas que guardé por las dudas cuando era usuario de Window$ y no sabía nada del tema...

No encontré nada con las que pueda grabarlas y hacerlas cd de nuevo

Espero que esto no cause conflicto, si es así avisen =)

---

### Post by kowal on 2007-08-31
> **Mataca said:**
> FAKTORQM lee imagenes .ccd ??
Yo tengo un par hechas x mi de unos cds, mas precisamente del indio solari y otro de los heroes del silencio y otros mas que guardé por las dudas cuando era usuario de Window$ y no sabía nada del tema...

No encontré nada con las que pueda grabarlas y hacerlas cd de nuevo

Espero que esto no cause conflicto, si es así avisen =)


No se si Acetone ISO maneja .CDD, pero hay un paquete en los repositorios que se llama **ccd2iso** que justamene convierte .CDD a .ISO

Saludos

---

### Post by faktorqm on 2007-08-31
hola, como montarlas no las monta, lo que hay que trae este programa es para montar .iso, pero tambien trae un .algo to .iso, que es un conversor de cualquier formato a formato iso 9660. lo que no se es si ese convertidor trae para ccd. yo creo que si, por que cuando migre de windows a linux, me di cuenta que tenia bardo, tenia imagenes de dvd en .iso, en .mdf, cd's en .bin, .ccd, .iso, .mdf, .nrg, tenia un bardo de la hostia, y tuve que convertir one by one a iso. todo legal por supuesto..................................................................... 8-[:roll::-\"#-o:---)
instalatelo, sino hace una cosa, inicia en windows, con el alcohol pasala a .iso y listo el pollo. yo ya despues de convertir cosas durante 6 meses, ya estoy en condiciones de no depender del windows. lo dejo para probar los programas que les instalo a los clientes, y la verdad que solo por eso. salu2!!!!!!!!!!

---

### Post by por100pre1 on 2007-08-31
Habia ignorado este post porque tenia otro nombre. ¡Excelente!  =D> ¡Gracias!

---

### Post by bulletxt on 2007-08-31
@ ALL

AcetoneISO2 does support CCD and all other images. If you need to burn them on cd/dvd, go to convert and convert it. Or else you can try to Extract the image to a folder.


It is also able to mount, in this case it supports:

ISO BIN NRG MDF IMG


this page will explain everything it does:
[http://www.acetoneteam.org/latest-news.html](http://www.acetoneteam.org/latest-news.html)

---

### Post by Mataca on 2007-08-31
Pero que barbaridad! mi pregunta derivo respuestas internacionales

[B]Gracias Faktorqm 
Tanks Bulletxt[/B]

No tengo mas Guindow$ me pasé integramente a Ubuntu hace un 1 mes.   Me di cuenta que Linux es mas que un SO es una ideología que comparto =) Cuando llegue a casita lo pruebo GRACIAS

---

### Post by leo_rockway on 2007-08-31
> **bulletxt said:**
> @ ALL

AcetoneISO2 does support CCD and all other images. If you need to burn them on cd/dvd, go to convert and convert it. Or else you can try to Extract the image to a folder.


It is also able to mount, in this case it supports:

ISO BIN NRG MDF IMG


this page will explain everything it does:
[http://www.acetoneteam.org/latest-news.html](http://www.acetoneteam.org/latest-news.html)

Para TODOS

AcetoneISO2 tiene soporte para CCD y todas las demas imagenes. Si necesitas copiarlas a cd/dvd anda a convert y convertilas. Si no, podes probar extraer la imagen a una carpeta.

Tambien puede montar y tiene soporte para los siguientes formatos:

ISO BIN NRG MDF IMG

esta pagina explica todo lo que hace
[http://www.acetoneteam.org/latest-news.html](http://www.acetoneteam.org/latest-news.html)

---

### Post by Hei Ku on 2007-08-31
tengan en cuenta que las imagenes iso se pueden montar tambien directamente desde la consola, con mount, aunque no me acuerdo exactamente los comandos ahora.

---

### Post by faktorqm on 2007-08-31
Hola, el comando es:

```
sudo mount -t iso9660 -o loop xubuntu-7.04-alternate-i386.iso /media/disk
```

este era un ejemplo, la forma general es:

```
sudo mount -t iso9660 -o loop tu_imagen.iso directorio_destino
```

El man de mount es muy interesante, para aquellos que buscan aprender un poco más sobre el extraño proceso de montaje/desmontaje, les va a interesar mucho, y se lo recomiendo a todos.

COPIO EN EL POST ORIGINAL LAS FEATURES TRADUCIDAS. Salu2 a todos y gracias por sus aportes!! :D

---

### Post by z-itou16 on 2008-01-19
excellente. yo uso ahora mismo gmountiso me trabaja muy bien pero no se le compara nada a aceTone iso. gracias.

mmm bueno otra manera mas facil de installar seria usando gdebi ya q linux es basado en debian. aun q tengas 7.04 (7.10 ya viene installado) aun puedes installarlo, si no te gusta eso de installar primero los dependecies y cosas asi gdebi es lo mejor para ti.

bueno saludos y gracias por url. saludos :)

---

### Post by itsvan on 2008-03-16
Hola! como Podria Installar ACETONE ISO en UBUNTU 64bit,,no tengo la menor idea...ayuda por favor!!!!!:)

---

### Post by faktorqm on 2008-03-17
Recien me pase por la pagina y no existe version para 64. no si queres intentar correrla con algun wrapper o intentar compilar el source a mano aunke sea para ver que pasa. Salu2!

---

### Post by itsvan on 2008-03-17
Pues si no hay otra solucion,,qualquier cosa,,o habra otra programa parecido? necisito montar las imagenes .daa ,iso, etc...per yo no se un ****** de esto

---

### Post by faktorqm on 2008-03-17
capo, las .iso las podes montar con el mount, lee un par de post mas arriba que yo mismo expliko como se hace. las otras si necesitas otra cosa. salu2!

---

### Post by leo_rockway on 2008-03-18
Para archivos de imagen esotéricos yo uso aplicaciones del tipo bin2iso o mdf2iso y después monto el ISO a la vieja usanza.

---

### Post by itsvan on 2008-03-19
Hola,,sabes que sigo los pasos pero cuando llego al paso 4..me sale este error: ~$ sudo dpkg -i fuseiso_20061017-0~3v1ubuntu0_i386.deb
dpkg: error processing fuseiso_20061017-0~3v1ubuntu0_i386.deb (--install):
 package architecture (i386) does not match system (amd64)


creo que debe que yo tengo el 64Bit y no el 32bit,,,que puedo hacer?eh intendtado de todo,y no encuentro solucion al **** problema...:confused:

---

### Post by Hei Ku on 2008-03-19
> **itsvan said:**
> Hola,,sabes que sigo los pasos pero cuando llego al paso 4..me sale este error: ~$ sudo dpkg -i fuseiso_20061017-0~3v1ubuntu0_i386.deb
dpkg: error processing fuseiso_20061017-0~3v1ubuntu0_i386.deb (--install):
 package architecture (i386) does not match system (amd64)


creo que debe que yo tengo el 64Bit y no el 32bit,,,que puedo hacer?eh intendtado de todo,y no encuentro solucion al **** problema...:confused:

efectivamente, el .deb es para 32bit y tu sistema es de 64.

Lo mejor seria que consiguieras un deb de 64bits, o sino te va a convenir compilar directamente.

---

### Post by faktorqm on 2008-03-19
Hola, bueno estuve indagando con el problema este y lo primero que se me ocurrio es preguntarte por que no te instalaste la version de 32 bits...... jajajaj mentira!

En esta direccion: [http://ubiz.ru/dm/fuseiso-20061017.tar.bz2](http://ubiz.ru/dm/fuseiso-20061017.tar.bz2) tenes el fuse iso generico para compilar.

Si no va eso, o mejor dicho, si terminaste todo y sigue sin andar, hace esto:

- Instala el paquete libqt4-dev
- Baja el archivo AcetoneISO2-generic-src.tar.gz (En la seccion Source download), descomprimilo, entra al directorio que se creo cuando descomprimiste y escribi:

qmake-qt4

make

Ahora reemplaza el archivo /usr/bin/acetoneiso2 con el archivo acetoneiso2 nuevo que recien compilaste.

NOTA: Si cuando haces qmake-qt4 te devuelve un error, simplemente escribi antes qmake.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

AHORA BIEN, EN OTROS LUGARES ENCONTRE LO SIGUIENTE:

wget [http://belnet.dl.sourceforge.net/sourceforge/acetoneiso2/AcetoneISO2_1.0.2-all.deb](http://belnet.dl.sourceforge.net/sourceforge/acetoneiso2/AcetoneISO2_1.0.2-all.deb) 

sudo dpkg --force-architecture -i AcetoneISO2_1.0.2-all.deb

Lo que no tengo intuido es si luego de hacer esto tenes que hacer lo del paquete libqt4-dev en adelante.

Suerte con eso y contame como te fue y que metodo usaste asi el que viene atras ya lo tiene. Salu2!!!!

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

EDITO: si se te sigue complicando la cosa revisa esta entrada en un blog que dice como hacer un monton de cosas a mano:

[http://www.cesarius.net/montando-archivos-iso-bin-cue-mdf-img-y-nrg-en-ubuntulinux/](http://www.cesarius.net/montando-archivos-iso-bin-cue-mdf-img-y-nrg-en-ubuntulinux/)

---

### Post by bulletxt on 2008-03-19
AcetoneISO2 2.0.1 is out! 

[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

### Post by SLA_leandrin on 2008-03-19
> **leo_rockway said:**
> 
por alguna razon me dice q no tengo fuse-utils instalado, cuando lo acabo de instalar... medio raro.

Lo instalé siguiendo estos pasos y me dió el mismo error. Lo instala, pero cuando lo abre te larga una advertencia de que es "strongly reccomended" instalar unos packages...

Así que me fui a la web del proyecto y me bajé el paquete .deb

[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2]("http://www.acetoneiso.netsons.org/viewpage.php?page_id=2")

y resultó que hay que hacer lo siguiente:

```
$ sudo chmod 4755 /bin/fusermount
 sudo chmod o+rw /dev/fuse
 sudo addgroup <nombre de usuario> fuse

```

Y eso es todo...

---

### Post by faktorqm on 2008-03-19
si tiene razon aca el chabon, yo me fije en los tutos ke tenia yo :S despues revisa bien los links para las nuevas versiones. si tenes problemas compila el sou8rce de la nueva y fijate ke onda. salu2!

---

### Post by LePresident on 2010-03-25
Q tal!

Estoy tratando de instalar el acetone, pero por alguna extraña razón no corre con los pasos que han posteado.

Me indica que debo instalar 'fuse-utils'.  Ya revisé si lo tengo descargado y al parecer esta en su versión mas reciente... ¿que puede estar deteniendome?

De antemano, muchas gracias por su ayuda!

[HTML]Welcome to xAcetoneISO2, a gtk port of the KDE AcetoneISO2 software

checking write permissions
user has full permissions to write
installation will now start
3
2
1
Starting installation
mkdir: no se puede crear el directorio «/opt/acetoneiso2»: El archivo ya existe
please wait

intallation 100%

I will now do a quick test to check most important dependencies

zenity found OK
Please install:  fuse-utils
And then run again this installer
[/HTML]

---

### Post by euzkoarima on 2010-03-27
Si efectivamente tenés instalado el paquete fuse-utils (podes comprobarlo en el synaptic) entonces no se que puede ser.

Pero te sugiero probar de instalarlo desde [getdeb]("http://www.getdeb.net/") al menos así es como lo instalé yo.

Saludos,
Eduardo

---

### Post by The_PoWeR on 2010-04-03
Yo tengo una versión instalada de un Deb de 32bit. 

Aqui teneis el enlace: [http://www.taringa.net/posts/linux/3907212/Descargar-Acetoneiso-Deb.html](http://www.taringa.net/posts/linux/3907212/Descargar-Acetoneiso-Deb.html)

Se encarga solo de bajarte y ponerte lo que te falta, no tienes que hacer nada. Eso si, solo vale para 32 bits.

Este programa tiene un fallo MUY GRAVE. No se puede configurar la Codificación para los caracteres para seleccionar UTF-8 o ISO-8859-1.

Qué pasa entonces? pues extraes una imagen Iso, Bin, etc.. y si dentro hay archivos con tildes, Ñ , etc... los extrae renombrandolos todos. UNA BASURA VAMOS.
Nadie sabe alguna manera para arreglar esto? renombrar tal cantindad de archivos una vez extraidos es una LOCURA. Además que ironía al tema, en cada archivo que contenía una ñ o tilde añade de nombre esto "(codificación no válida)" que SI QUE lleva acentos xDD que cosas no?
Si alguien puede ayudar ahí queda.

Salu2

---

