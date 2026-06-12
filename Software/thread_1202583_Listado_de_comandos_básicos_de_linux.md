---
title: "Listado de comandos básicos de linux"
date: 2009-07-02
forum: Software
---

### Post by jorval on 2009-07-02
Hola amigos. **[RodrigoVB]("http://ubuntuforums.org/member.php?u=344624")** en el foro antiguo nos regaló un excelente listado de comandos básicos de linux que sería una pena que se perdieran así que los copio aquí:

Aquí les dejo un listado de comandos básicos de linux, nunca están de más para los con más experiencia y sin duda son una grán ayuda para los menos expertos como yo. Los saqué de algún lugar de la web que ya no recuerdo, asi que le dejo mis agradecimientos al autor original


COMANDOS SOBRE FICHEROS:

ls = Lista los archivos de un directorio concreto


ls -l = Añade informacion sobre los atributos
ls -a = Lista todos los archivos incluyendo los ocultos
ls -R = Lista el contenido del directorio y todos sus subdirectorios recursivamente



cat [fichero] = Muestra el contenido de un fichero


cat -n [fichero] = Muestra el contenido de un fichero numerando sus lineas



more [fichero] = Muestra un fichero de forma tabulada como una pagina del man

less [fichero] = Igual que more

echo [cadena] = Repite la cadena


echo -e [cadena] = Habilita la interpretacion de caracteres de escape



stat [fichero] = Muestra el estado de un fichero


stat -f [fichero] = Muestra el estado del sistema de ficheros



tail [archivo] = Muestra las ultimas lineas de un archivo


tail -n [n] [archivo] = Muestra las ultimas n lineas del archivo



head [archivo] = Muestra las primeras lineas de un archivo


head [n] [archivo] = Muestra las n primeras lineas de un archivo



find [patron] = Busca las coincidencias con el patron dentro del directorio y sus subdirectorios


find [ruta] [patron] = Busca las coincidencias con el patron dentro de la ruta
find [patron] -print = Busca las coincidencias y muestra la ruta completa de estas.
find -size [tam] = Busca aquellos archivos menores que el tamaño señalado
man find = Muestra un listado las multiples opciones y usos de find



whereis [programa] = Busca la ruta donde se encuntra el programa, su ayuda ...

type [comando] = Busca la ruta donde se encuentra el comando

which [programa] = Busca la ruta donde se encuentra el programa o comando

pwd = Muestra el directorio actual

history = Muestra los comandos utilizados por el usuario en orden cronologico

fc -l = Muestra los ultimos comandos usados por el usuario

eject [unidad optica] = Expulsa la unidad optica seleccionada (Podemos encontrarlas en /media)


eject -t [unidad optica] = Cierra la bandeja de la unidad optica (cdroom, dvd ...)



cd = Cambia al home o al directorio raiz si se lanza como root


cd [ruta] = Se desplaza al directorio especificado en la ruta
cd .. = Se mueve al directorio anterior
cd ../.. = Se mueve dos directorios atras.



cp [origen] [destino] = Copia el archivo origen al directorio destino


cp -R [origen] [destino] = Copia un directorio recursivamente
cp -p [orgien] [destino] = Copia preservando los permisos y las fechas
cp [archivo] [archivo nombre cambiado] = Copia el archivo y lo cambia de nombre



mv [orgien] [destino] = Mueve al archivo origen al directorio destino

mkdir [directorio] = Crea una nueva carpeta dentro del directorio.

rmdir [directorio vacio] = Elimina el directorio vacio

rm [archivo] = Elimina un archivo completamente


rm -r [directorio] = Elimina un directorio recursivamente



ln [archivo] = Crea un enlace duro (mismo archivo con distintos nombre)


ln -s [archivo] = Crea un enlace blando



diff [opciones] [fichero1] [fichero2] = Compara los dos ficheros


diff -w [fichero1] [fichero2] = Descarta el espacio en blanco cuando compara las lineas
diff -q [fichero1] [fichero2] = Informa solo si los ficheros son distintos
diff -y [fichero1] [fichero2] = Muestra la salida a dos columnas



passwd = Permite al usuario cambiar su contraseña


sudo passwd = Permite al usuario cambiar o crear la contraseña de root



man termino = Muestra una ayuda sobre termino

clear = Limpia la pantalla

reset = Reinicia la terminal

date = Muestra la hora y la fecha en formato completo


date -u = Muestra la hora y fecha en formato completo en UTC
date '+format' = Formatea la hora y la fecha -> date '+Dia: %m/%d/%y%n Hora:%H:%M:%S'
man date = Muestra un listado con todos los posibles formatos



who = Muestra los usuarios que hay logeados en el sistema

whoami = Muestra la informacion del propio usuario

write [user] = Permite mandar un mensaje a un usuario conectado al sistema (valido para red), para finalizar pulsar Ctrl+d

mesg = Muestra el estado actual de la terminal


mesg [y | n] = Esta orden permite al usuario que la ejecuta habilitar (y) o inhibir (n) el permiso de escritura sobre su terminal



mail [usuario] = permite intercambiar correo electrónico con otros usuarios. Similar a write solo que el usuario no necesita estar conectado.

uname = Muestra el sistema unix sobre el que estamos trabajando


uname -a = Muestra toda la informacion sobre el tipo de sistema que se esta utilizando
uname -m = Muestra el tipo de arquitectura que se esta utilizando
uname -s = Muestra el nombre del sistema
uname -n = Muesta el nombre por el que se identifica el sistema en la red
uname -r = Muestra la revision (release) del kernel que estamos usuando
uname -v = Muestra la version del kernel que estamos usando



chmod [+|-][rwx] [archivo] = Añade(+) o elimina(-) los permisos de lectura(r), escritura(w) o ejecucion(x) del archivo o directorio.


chmod [u|g|o|a][+|-][rwx] [archivo] = Cambia los persmisos al usuario(u), grupo(g), otros(o) o a todos(a)
chmod [mascara] [archivo] = Cambia los permisos al archivo segun la mascara, donde 000 quita todos los permisos y 777 da todos los permisos.



umask = Muestra los permisos con los que el usuario creara sus archivos por defecto


umask [mascara] = Fija los permisos que tendra por defecto cualquier archivo creado por el usuario. 777 quita todos los permisos y 000 da todos los permisos.



chown [nuevo propietario] [archivos] = Cambia de propietario a los archivos

chgrp [grupo nuevo][archivos] = Cambia de grupo a los archivos

mkfs.msdos /dev/fd0 = Formatea en formato MsDos un disquette

fdformat /dev/fd0 = Formatea en formato MsDos un disquette y despues verifica el formateo

sleep [tiempo] = Congela la terminal durante los segundos especificados

export [identificador][=valor] = Define, marca y/o asigna el identificador(es) como variables de entorno que seran exportada a los subprocesos que se generen.

unset [identificador] = Permite eliminar una variable identificada por su nombre o identificador

| = Redirecciona la salida de un comando con la entrada del siguiente comando

alias nombre='comando' = Asigna un nombre simbolico a un comando


IMPRIMIENDO

lpr fichero = Añade el fichero a la cola de impresion


lpr -#n fichero = Realiza "n" copias del fichero, donde n es un numero natural (1,2,3,4,5 ...)



lpq = Muestra los documentos en la cola

lprm = Cancela la impresion del documento actual


lprm n = Cancela la impresion del trabajo n, siendo n un numero natural.



pr +2 l70 -w 80 -h "Comandos" fichero -t = Formatea un archivo de texto para la impresion


-t = No imprimira cabeceras ni pies de pagina
l70 = Establece la longitud de la página de 70 lineas (66 por defecto)
-w 80 = Establece el ancho de linea en 80 caracteres(72 por defecto).
-h "Comandos" = Establece "Comandos" como cabecera de cada página.



pr l70 -d comandos.txt | lpr = Una vez formateado el texto lo manda a la cola de impresion


FORMATOS:

tidy fichero.html = Analiza el codigo de un documento html


tidy -m fichero.html = Corrige modificando el codigo del fichero html
tidy -m -asxml fichero.html = Convierte el fichero html a xml
tidy -m -asxhtml fichero.html = Convierte el fichero html a xhtml
tidy -m -ashtml fichero.xhtml = Convierte un fichero xhtml a html



pdftops fichero.pdf fichero.ps = Convierte un fichero pdf a ps


COMPRIMIR Y DESCOMPRIMIR:

zip -r fichero.zip ficheros = Comprime en formato .zip


unzip archivo.zip = Descomprime un .zip
unzip -v archivo.zip = Muestra el contenido de un .zip sin descomprimirlo



rar a -r0 fichero.rar ficheros = Comprime los ficheros en formato .rar


unrar e -r archivo.rar = Descomprime el fichero.rar en el directorio actual
unrar x -r archivo.rar ruta_destino = Extrae el fichero.rar en la ruta especificada
unrar v archivo.rar = Muestra el contenido del fichero.rar sin descomprimirlo



gzip -r ficheros = Comprime ficheros a gz


gzip -d fichero.gz = Descomprime un fichero.gz
gzip -c fichero.gz = Muestra el contenido de un fichero.gz sin descomprimirlo



bzip2 ficheros = Comprime ficheros al formato bz2


bzip2 -d fichero.bz2 = Descomprime un fichero.bz2
bzip2 -c fichero.bz2 = Muestra el contenido de un fichero.bz2 sin descomprimirlo



tar -vcf archivo.tar /fichero1 /fichero2 ... = Empaqueta ficheros o directorios en tar


tar -vxf archivo.tar = Desempaqueta el archivo.tar
tar -vtf archivo.tar = Muestra el contenido del archivo.tar sin descomprimirlo



tar -zvcf archivo.tgz directorio = Empaqueta y comprime (tgz) directorios o ficheros


tar -zvxf archivo.tgz = Desempaqueta y descomprime un archivo.tgz
tar -zvtf archivo.tgz = Muestra el contenido de un tgz sin descomprimirlo ni desempaquetarlo



tar -jvcf archivo.tbz2 directorio = Empaqueta y comprime (tbz2) directorios o ficheros


tar -jvxf archivo.tbz2 = Desempaqueta y descomprime el archivo.tbz2
tar -jvtf archivo.tbz2 = Muestra el contenido sin desempaquetar ni descomprimir el .tbz2




RENOMBRADO:

rename 'y/A-Z/a-z/' *.zip = Cambia mayusculas por minisculas en todos los .zip. *.zip indica el tipo de archivos a renombrar (llamado con * renombra todos). A-Z indica el patron a modificar y a-z el patron por el que se modifica. rename 'y/ /_/' * Cambiaria espacios por _ en todos los archivos


rename 's/expresión //' *.mp3 = Elimina una expresion de todos los mp3.




GRAFICOS:

glxinfo = Informacion sobre OpenGl y Glx


glxinfo | grep "direct rendering" = Indica si esta activada la aceleracion 3D



showrgb = Muestra los colores reconocidos por el sistema y su codigo RGB

banner texto = Muestra un cartel ascii con el texto de forma vertical


banner -w[n] texto = Hace el banner con el tamaño indicado por n, siendo n un numero (Sin los corchetes)



figlet texto = Muestra un cartel ascii con el texto de forma horizontal


figlet texto
figlet -w[n] texto = Similar a banner pero en formato horizontal
figlet -t texto = La salida se mostrara con su anchura maxima
figlet -c texto = La salida se mostrara centrada



xwd > ventana.xwd = Captura una ventana


xwd -root -screen > pantalla.xwd = Captura la pantalla



gnome-screenshot = Captura la pantalla en el escritorio gnome


gnome-screenshot --window = Captura la ventana en el escritorio gnome



import -window - ventana.jpg = Captura una ventana en cualquier formato

xwud -in pantalla.xwd = Muestra imagenes en formato xwd

identify imagen.gif = Muestra las propiedades de una imagen

pdfimages fichero.pdf nombre_para_las_imágenes = Extrae las imagenes de un .pdf

convert *.jpg catálogo.pdf = Crea un catalogo pdf con las imagenes

display "vid:*.jpg" = Crea un indice grafico con las miniaturas

convert imágen_color.jpg -monochrome imágen_b/n.jpg = Convierte una imagen a blanco y negro

convert imagen_original.ppm imagen_nueva.jpg = Cambia el formato de una imagen

convert -sample 100x50 imagen_original.jpg imagen_nueva.jpg = Cambia las dimensiones de una imagen

mogrify -format jpg *.ppm = Convierte a jpg todas las imagenes ppm

mogrify -format png -sample 20%x20% *.jpg = Crea miniaturas de varias imagenes

convert -delay 15 imag1.jpg imag2.jpg imag3.jpg remero.gif = Crea un gif animado con varias imagenes (15 es es el tiempo entre imagenes en centesimas)

convert imagen.gif -adjoin imagen.jpg = Extrae los fotogramas de un gif animado

convert -font courier -fill yellow -pointsize 25 -draw 'text 100,250 texto' imagen.jpg imagen_con_txt.jpg = Añade texto a una imagen


IMAGENES:

mkisofs -R -J -T -o imagen1.iso fichero1 = Crea una imagen de un fichero que se encuentre en nuestro disco duro.

dd if=/dev/cdrom of=imagen.iso = Crea una imagen del cdroom y la vuelca en imagen.iso

cat /dev/cdrom > debian.iso = Similar al anterior

nrg2iso imagen.nrg imagen.iso = Convierte una imagen nrg a iso (instalar paquete nrg2iso)

bin2iso imagen.cue = Convierte una imagen bin o cue a iso (Instalar paquete bin2iso)

ccd2iso imagen.img imagen.iso = Convierte una imagen img/ccd/sub/cue a iso (Instalar paquete ccd2iso)

mdf2iso imagen.mdf imagen.iso = Convierte una imagen mdf o mds a iso (Instalar paquete mdf2iso)

mount -t iso9660 -o loop imagen.iso punto_montaje = Monta una imagen iso

umount punto_montaje = Desmonta una imagen

md5sum archivo.iso > archivo.iso.txt = Genera la suma md5 de un archivo

md5sum -w -c archivo.iso.txt = Verifica la suma md5 de un archivo


GRABACION DE CD Y DVD:

cdrecord -v dev=0,0,0 fs=16M speed=30 imagen.iso = Grabar un cd de datos/imagen

cdrecord -v dev=0,0,0 fs=16M speed=30 -eject -isosize /dev/sr1 = Copiar un cd de datos/imagen

cdrecord -v dev=0,0,0 fs=16M speed=30 -pad -audio *.wav = Grabar un cd de audio

cdrdao copy -v 2 --device 0,0,0 --source-device 0,1,0 --reload \ --eject --on-the-fly --fast-toc --paranoia-mode 0 = Copia un cd de audio

cdrecord -v dev=0,0,0 fs=16M speed=30 -pad -audio *.wav -data imagen.iso = Graba un cd mixto

cdrecord -v blank=fast = Borrar un cd regrabable

growisofs -Z /dev/sr0 -R -J archivo = Grabar un cd de datos/imagen

growisofs -M /dev/sr0 -R -J archivo = Añade mas datos a un dvd multisesion

growisofs -dvd-compat -Z /dev/sr0=imagen.iso = Graba una imagen previamente creada

dvdrecord -v dev=0,0,0 blank=fast = Borra un dvd regrabable

dvdbackup -M -i/dev/sr0 -o ~/copia_dvd/ = Ripea un video dvd

vobcopy -i /dev/sr0 -m -o ~/copia_dvd/ = Similar a la anterior


RIPEO DE UN CD:

cdda2wav -B -H -D /dev/sr1 -s -x = Extrae disco completo en archivos wav separados

cdda2wav -H -D /dev/sr1 -s -x -t 5 = Extrae la pista numero 5

cdparanoia -B -d /dev/sr1 = Extrae disco completo en archivos wav separados

cdparanoia 5 -d /dev/sr1 = Extrae la pista numero 5

abcde -d /dev/sr1 -N -x -o mp3 = Extrae disco completo en archivos mp3 separados (Necesario instalar paquete abcde)


abcde -d /dev/sr1 -N -x -o mpc = Extrae el disco completo en archivos mpc separados
abcde -d /dev/sr1 -N -x -o ogg = Extrae el disco en archivos ogg separados
abcde -d /dev/sr1 -N -x -o ogg tracks 1-3 5 = Extrae las 3 primeras canciones y la quinta




AUDIO:

lame -b 192 -m j tema.wav = Convierte una cancion wav a mp3 con brittate de 192 (Este valor puede sustituirse, la opcion -h indica maxima calidad)

lame -h -m j --nogap *.wav = Convierte todos los archivos wav a mp3

oggenc -b 128 -q 5 tema.wav = Convierte un archivo wav a ogg (-q 5 indica la calidad de 0 a 10)


oggenc *.wav = Convierte todos los wav en un unico fichero ogg
oggenc -a -l -t *.wav = Convierte todos los wav en sus respectivos ogg
oggdec tema.ogg = Convierte un archivo ogg a wav
oggdec *.ogg = Convierte todos los ogg a wav



lame -h --decode tema.mp3 tema.wav = Convierte un archivo mp3 a wav

mplayer -ao pcm fichero.asf = Convierte un archivo asf o wma a wav

play cancion = Reproduce una cancion en la terminal


VARIOS:

man comando = Muestra informacion sobre el comando



apropos palabra_clave = Busca dentro de las declaraciones de man la palabra exacta
apropos -e palabra_clave = Busca la palabra exacta



cal = Muestra el calendario del mes actual


cal -my = Muestra el calendario de todo el año



uptime = Muestra la hora,tiempo de funcionamiento,nº usuarios conectados y la carga media

tzconfig = Permite seleccionar la zona horaria

tzselect = Permite seleccionar la zona horaria

date = Muestra la fecha del sistema en formato local


date --help = Muestra todas las opciones de date en castellano



hwclock --show = Muestra el reloj Hardware o reloj de Bios


hwclock -systohc = Pone el reloj Hardware a la hora del sistema



watch -n tiempo comando = Ejecuta un comando cada x segundos (defecto = 2)

clear = Limpia la pantalla

reset = Reinicia la terminal

hostname = Muestra el nombre de la maquina

tty = Muestra el nombre del fichero de la terminal conectada a la salida estandar.

/etc/init.d/servicio stop = Para un servicio o demonio


/etc/init.d/servicio start = Inicia un servicio o demonio
/etc/init.d/servicio restart = Reinicia un servicio o demonio



startx = Arranca el entorno grafico

sh script = Ejecuta un script

java -jar fichero.jar = Ejecuta un programa java

./[archivo.bin] = Ejecuta un archivo binario (Tambien puede usarse con script)

consolechars -f fuente.psf.gz = Cambiar la fuente de la consola.Las fuentes se encuentran en /usr/share/consolefonts/

reportbug = Enviar bugs

exit = Termina la ejecucion del programa actual

shutdown -t1 -h now = Apaga el pc


shutdown -t1 -r now = Reinicia el pc



su = Entra como superusuario

adduser usuario = Crea un nuevo usuario


adduser usuario grupo = Añade un usuario existente a un grupo existente
adduser --no-create-home usuario = Crea un usuario pero sin directorio personal



addgroup grupo = Crea un grupo nuevo

deluser usuario


deluser usuario grupo = Elimina un usuario del grupo especificado
deluser --remove-home usuario = Elimina un usuario y su carpeta personal



delgroup grupo = Elimina el grupo


delgroup grupo --only-if-empty = Elimina el grupo solo si no tiene ningun usuario



usermod -l nuevo_login = Cambia el nombre del usuario


usermod -d nueva_home -m login = Cambia el nombre del usuario (lo crea si no existe) y tranfiere su contenido.



usermod -e AAAA-MM-DD login = Fecha en que la cuenta de usuario sera desactivada

groupmod -n nuevo_nombre grupo = Cambia el nombre de un grupo

locale = Muestra la zona geografica configurada

dpkg-reconfigure locales = Reconfigura los locales

dpkg-reconfigure console-data = Reconfigura el teclado

loadkeys ruta_mapa_teclado.gz = Carga el mapa de teclado que le indicamos,que estará en: /usr/share/keymaps

locale charmap = Muestra el codigo de caracteres en uso

set = Muestra las variables locales definidas

env = Muestra las variables de entorno definidas

export = Muestra las variables de entorno declaradas


PROCESOS:

memtest = Hace una comprobacion del estado de la memoria

free -m -s 3 = Muestra el uso de la memoria

ps -aux = Muestra informacion sobre los procesos en curso

top = Muestra informacion detallada sobre los procesos en curso (tecla z colorea los activos)

pstree = Muestra los procesos en curso en forma de arbol

pidof [comando] = Muestra el id del comando

killall [proceso] = Para el proceso

strace [comando] = Muestra las llamadas al sistema originadas por el comando

fuser -v [archivo] = Muestra los procesos que estan usando un archivo o directorio

lsof = Lista los ficheros abiertos por los procesos


lsof -c [comando] = Lista los ficheros abiertos por un proceso
lsof +D [Directorio] = Lista los procesos que estan usando el directorio
lsof -i :60627 = Muestra los procesos que se encuentren detras del puerto 60627



[comando] & = Ejecuta un comando en segundo plano

nohup [comando] & = Ejecuta un comando de forma que si cerramos la terminal siga ejecutandose

jobs = Lista los procesos en segundo plano identificandolo con su numero de tarea

fg nº_tarea = Pasa un comando a primer plano

bg = Pasa a segundo plano un proceso que hemos suspendido temporalmente con Ctrl-Z

nice -n prioridad [comando] = Ejecuta un comando con una prioridad determinada

renice prioridad PID_del_proceso = Cambia la prioridad de un proceso en marcha

at [-f script] [tiempo] = Ejecuta un script a una hora y/o fecha concretas


atq = Muestra la lista de tareas programadas de forma numerada
atrm nº = Elimina una tarea indentificada por su nº



batch = Igual que at, salvo que batch solo ejecuta el script si la carga de cpu es inferior al 80%


DISCO DURO:

du -h [fichero] = Muestra el espacio que ocupa el fichero o directorio

tree -a -s -L 2 = Igual que el anterior pero lo muestra en forma de arbol

df = Muestra informacion sobre particiones montadas

cfdisk = Muestra informacion sobre particiones

mount = Muestra un listado de los dispositivos montados


mount punto_montaje = Monta un dispositivo establecido en fstab
umount punto_montaje = Desmonta un dispositivo establecido en el fstab
mount -t [Sistema_Archivos] /dev/[dispositivo] [punto_montaje] = Monta el dispositvo, ej: mount -t ext3 /dev/hda1 /media/disco1
umount /dev/[dispositivo] = Desmonta un disco



fsck /dev/[dispositivo] = Chequea y repara el sistema de archivos de una particion no montada


fsck.ext2 -vpf /dev/hdx = Chequea y repara el sistema de archivos de una particion ext2 no montada
fsck.ext3 -vpf /dev/hdx = Igual pero con una particion ext3



mkfs.ext2 /dev/hdXX = Crea un sistema ext2 en la particion seleccionada


mkfs.ext3 /dev/hdXX = Crea un sistema ext3 en la particion seleccionada
mkfs.ext2 /dev/fd0 = Crea un sistema ext2 en el disquette



mkswap /dev/hda2 = Crea un sistema de ficheros swap

tune2fs -O ^has_journal /dev/hdXX = Convierte la particion de ext3 a ext2

tune2fs -j /dev/hdXX = Convierte la particion de ext2 a ext3


INSTALACION DE SOFTWARE:

dpkg -i paquete = Instala un paquete


dpkg -r paquete = Desinstala un paquete
dpkg --purge paquete = Desisntala un paquete y sus archivos de configuracion
dpkg --force -r paquete = Fuerza la desinstalacion de un paquete
dpkg --force-all -r paquete = Fuerza aun mas la desinstalacion de un paquete (Puede comprometer el sistema)
dpkg -c paquete = Muestra el contenido de un paquete
dpkg -L paquete = Muestra todos los ficheros que se instalaron con un paquete
dpkg -S fichero = Muestra a que paquete pertenece un fichero
dpkg --get-selections = Muestra un listado con todos los paquetes instalados
dpkg-reconfigure paquete = Reconfigura el paquete



aptitude update = Actualiza la lista de paquetes


aptitude upgrade = Actualiza el sistema (no instala ni elimina paquetes)
aptitude dist-upgrade = Actualiza el sistema eliminando e instalando paquetes si fuera necesario
aptitude install [paquetes] = Instala los paquetes indicados
aptitude reinstall [paquetes] = Reinstala los paquetes indicados
aptitude remove [paquetes] = Elimina los paquetes indicados
aptitude purge [paquetes] = Elimina los paquetes y sus ficheros de configuracion
aptitude download [paquetes] = Descarga los paquetes en el directorio actual
aptitude hold [paquetes] = Bloqua los paquetes indicados
aptitude unhold [paquetes] = Desbloquea los paquetes seleccionados
aptitude unmarkauto [paquetes] = Desmarca paquetes como instalados manualmente
markauto = Marca paquetes como instalados manualmente
aptitude search [expresion] = Busca un paquete por nombre o expresion
aptitude show [paquete] = Muestra informacion detallada de un paquete
aptitude clean = Elimina los paquetes .deb descargados


Saludos,
_________________
RodrigoVB
Ubuntu User # 3824 / Linux user #362801

---

### Post by moreback on 2009-07-03
A propósito de comandos de consola, esta polera se ve buena ;-)

[http://store.xkcd.com/xkcd/#LinuxCheatShirt](http://store.xkcd.com/xkcd/#LinuxCheatShirt)

Saludos!

---

### Post by CarlosRuiz on 2009-07-03
Holap:

Creo que usar algo así es demasiado para mí... xD

Saludooos :p

---

### Post by Patriciologico on 2009-07-05
Es tu experiencia clinica? vamos que sólo es una polera...Yo si la usaria

Saludos! :p

---

### Post by dnovai on 2009-07-06
Esta pro!
Además me ayudaría con mi pésima memoria.

Saludos!
PD: Cómo la consigo?

\\:D/

---

### Post by Carlos C on 2009-07-06
Señores, recordemos que el tema del thread son los comandos que RodrigoVB seleccionó y que jorval amablemente recuperó del foro antiguo. Otros temas se deben tocar en otros hilos.

---

### Post by zhelo on 2009-07-06
de mas qye alguno me sirve gracias

---

### Post by jorval on 2009-07-06
Hola amigos. Recién encontré este sitio con explicación de la mayoría de los comandos básicos. Vale la pena, creo. Saludos.

[http://www.comandos-linux.we.bs/index.html#controlProcesos]("http://www.comandos-linux.we.bs/index.html#controlProcesos")

---

### Post by Patriciologico on 2009-07-06
> **Carlos C said:**
> Señores, recordemos que el tema del thread son los comandos que RodrigoVB seleccionó y que jorval amablemente recuperó del foro antiguo. Otros temas se deben tocar en otros hilos.

Toda la razon, mis disculpas, me he indisciplinado ultimamente.

Para aporta al tema original dejo un enlace con comando que **NO DEBEN EJECUTARSE**

[http://www.linuxla.cl/?p=3609](http://www.linuxla.cl/?p=3609)

Saludos!

---

### Post by Patriciologico on 2009-07-06
Si utilizan aptitude se habran fijado que en la última versión el comando upgrade está obsoleto. El típico sudo aptitude upgrade ha sido sustituido por sudo aptitude safe-upgrade, y de forma similar, sudo aptitude dist-upgrade por sudo aptitude full-upgrade.

No os preocupéis porque es lo mismo de siempre pero con otro nombre:
upgrade = safe-upgrade
dist-upgrade = full-upgrade

Echando un vistazo al man de aptitude vemos que safe-upgrade actualiza todos los paquetes que pueda sin tener que borrar otros paquetes o instalar otros nuevos. Cuando sea necesario borrar o instalar un paquete para actualizar una aplicación, tendremos que utilizar full-upgrade.

full-upgrade es más agresivo: instalará y borrará todos los paquetes que haga falta hasta que se resuelvan todas las dependencias. Como implica los nombres de ambos comandos, full-upgrade no es del todo seguro, así que hemos de tener cuidado al utilizarlo.

Conclusión: utiliza siempre safe-upgrade a menos que te sientas aventurero.

[Fuente]("http://mundogeek.net/archivos/2007/10/20/aptitude-safe-upgrade-y-full-upgrade/") 

Pd: Espero haber purgado mis culpas :p

---

