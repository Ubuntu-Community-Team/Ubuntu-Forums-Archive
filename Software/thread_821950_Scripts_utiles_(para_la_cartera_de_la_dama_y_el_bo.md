---
title: "Scripts utiles (para la cartera de la dama y el bolsillo del caballero)"
date: 2008-06-07
forum: Software
---

### Post by sergiom99 on 2008-06-07
Bueno, inspirado en la sugerencia de concurso de valucha, abro este thread para postear los scripts que cada uno haya armado y que sirvan para hacer algo, cualquier cosa, mas sencilla.
Dejo los mios:

```
#!/bin/bash
# ABR/08 SM -- montar.sh --
# monta un archivo .ISO o .NRG
# $1 es el nombre de archivo
# Ej: ./montar.sh /home/videos/peli.ISO

sudo mount -o loop $1 /mnt/tmp
```

```
#!/bin/bash
# ENE/08 SM
# crea un tunel de un puerto local a uno remoto.
# $1 es el numero de puerto
# $2 es el usuario@host_remoto
# $3 es el puerto de ssh remoto
# Ej: ./tunnel.sh 5432 yo@adonde.vos 5022

ssh -L $1:127.0.0.1:$1 $2 -p $3
```

```
#!/bin/bash
# ABR/08 SM
# reordena los archivos del reproductor mp3 q quedan desordenados al copiarlos
# requiere el fatsort:
# sudo apt-get install fatsort
# -- NO HACE FALTA EXPULSARLO NI DESMONTARLO ! --
$MP3DEV = /dev/sdb1

sudo umount $MP3DEV
sudo fatsort $MP3DEV
```

espero le sirva a alguno y todos se prendan a postear los scripts que usan para hacer las cosas mas faciles.

Ojala termine como STICKY.
\Sergio
> 
IMPORTANTE: Agrego un índice para ubicar los scripts que haya posteados en el resto del thread. Gracias Air23 por la primer recopilada.

[Montar un archivo .ISO o .NRG - Crear un tunel de un puerto local a uno remoto - Reordenar los archivos del reproductor mp3](http://ubuntuforums.org/showpost.php?p=5137693&postcount=1)

[Alias de bash](http://ubuntuforums.org/showpost.php?p=5145133&postcount=9)

[Mas alias de bash](http://ubuntuforums.org/showpost.php?p=5145327&postcount=10)

[Renombrar todos los archivos de un directorio a minúsculas - Grabar discos desde consola](http://ubuntuforums.org/showpost.php?p=5377741&postcount=12)

[Redimensionar imagenes](http://ubuntuforums.org/showpost.php?p=5524669&postcount=13)

[Comandos para cambiar formatos de videos](http://ubuntuforums.org/showpost.php?p=5831464&postcount=14)

[Backups de servidores.](http://ubuntuforums.org/showpost.php?p=6031352&postcount=25)

[Lista de Paquetes](http://ubuntuforums.org/showpost.php?p=6186917&postcount=26)

[Nautilus scripts](http://ubuntuforums.org/showpost.php?p=6190406&postcount=27)

[Cambiar el fondo de pantalla aleatoriamente - Renombrar archivos (guiones por espacios) - Compilar un archivo LaTeX](http://ubuntuforums.org/showpost.php?p=6191529&postcount=28)

[Actualizar las claves de los repositorios de launchpad](http://ubuntuforums.org/showpost.php?p=6689502&postcount=36)

[Ver tv y escuchar radios - Limpiar](http://ubuntuforums.org/showpost.php?p=6690485&postcount=37)

[Transformar en mp3 las canciones de Imeem](http://ubuntuforums.org/showpost.php?p=6699206&postcount=38)

[Covers como iconos de carpetas  de musica](http://ubuntuforums.org/showpost.php?p=6715075&postcount=39)

[Convertir video a formato Ipod]("http://ubuntuforums.org/showpost.php?p=7026919&postcount=43")


---

### Post by pol666 on 2008-06-07
para que sirve el 2do?

---

### Post by andy_91 on 2008-06-07
seria bueno poner para que sirven como instalarlos etc....

---

### Post by pol666 on 2008-06-07
> **andy_91 said:**
> seria bueno poner para que sirven como instalarlos etc....

el 1ero sirve para montar archivos ISO el 3ero para reordenar los archivos del reproductor mp3 q quedan desordenados al copiarlos

y el 2do no se... supuestamente si son scripts se pueden ejecutar asi nomas una vez que los guardamos en gedit.

---

### Post by sergiom99 on 2008-06-08
> **pol666 said:**
> para que sirve el 2do?

Estan todos comentados y salvo el que lo aclara, no hace falta instalar nada.
El IIdo arma un tunel para forwardear puertos por SSH.
Por ejemplo tengo un equipo con solo el puerto SSH 5022 abierto. Entonces, haciendo la conexion con el tunel, puedo forwardear el 3306 (mysql) de esa caja al 3306 de mi maquina. Y conecto al localhost:3306 con un GUI de mysql y en realidad estoy mirando la DB del server remoto.

Si confunde lo saco.

---

### Post by leo_rockway on 2008-06-08
EDIT: Había puesto algo, pero no es un script per se... mejor me voy a dormir y cuando me despierte reviso mis scripts.

---

### Post by sergiom99 on 2008-06-08
antes habia puesto este script [[1]]("http://ubuntuforums.org/showthread.php?t=797765") que sirve para tomar la senial de un router DDWRT y que la PC te la "cante" usando festival.
Nota> Solo sirve si tenes un router con el firmware OpenSource DD-WRT

[1] [http://ubuntuforums.org/showthread.php?t=797765](http://ubuntuforums.org/showthread.php?t=797765)

---

### Post by andy_91 on 2008-06-08
bueno yo por ej pel scrip del tunar para enviar por bluetooth lo tengo que guardar en un lugar especial para que compla su funcion

tmb ponerle un nombre y extencion determinada

---

### Post by Kantier on 2008-06-08
no son exactamente scripts, sino unos alias que tengo en el /etc/bash.bashrc :

```

alias hdf='df -hlt ext2 -t ext3 -t reiserfs'
alias rara='rar a -m5 -t'
alias rarx='rar x'
alias ll='ls -lh'
alias la='ls -A'
alias l='ls -CF'
alias pg='ps aux | grep'
alias gt='curl -# --retry 5 --retry-delay 1 -O'
alias sloc='slocate -i'

```

---

### Post by leo_rockway on 2008-06-08
> **Kantier said:**
> no son exactamente scripts, sino unos alias que tengo en el /etc/bash.bashrc :

```

alias pg='ps aux | grep'

```

Ese era el que iba a postear yo, pero me arrepentí porque no es un script, jaja. Los alias son muy útiles igual.

yo tengo los siguientes:

```

alias sagu='sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y'
alias sagi='sudo apt-get install'
alias acsr='apt-cache search'
alias acsw='apt-cache show'
```

---

### Post by Kantier on 2008-06-09
yo prefiero aptitude para mis manejos paquetísticos... la verdad que resulta mejor que apt-get cuando se tiene sólo la consola :-D

---

### Post by sergiom99 on 2008-07-13
Otros más:
(1) Para renombrar todos los archivos de un directorio a minúsculas.
```

#!/bin/bash
#lowercase.sh
# Convertir archivos a lowercase
# correrlo donde estan los archivos a renombrar
##################################

for i in $(ls);
 do
 oldname="$i"
 newname=$(echo "$oldname" | tr 'A-Z' 'a-z')
 if [ "$oldname" != "$newname" ]
 then
        mv -i "$oldname" "$newname"
 fi
done
```

(2) Para Grabar discos desde consola, lo uso mucho en los servidores sin X.
Con esto terminan los scripts de backup diario que uso, grabando un DVD.
```

#!/bin/bash
#quemar archivos desde Konsole
#Uso: burn_cd.sh directorio-a-grabar etiqueta-cd
#

# sudo cdrecord dev=ATA: -scanbus
# con este comando sacamos los parametros para completar el device abajo
CDRECORD_DEV="/dev/scd0:6,0,0"

#borra el disco
/usr/bin/cdrecord dev=$CDRECORD_DEV blank=fast

IMG_SIZE=`/usr/bin/mkisofs -J -r -V $2 -q -print-size $1 2>&1 | \
          sed -e "s/.* = //"`
echo $IMG_SIZE [ "0$IMG_SIZE" -ne 0 ] && /usr/bin/mkisofs -J -V $2 $1 | \
    /usr/bin/cdrecord dev=$CDRECORD_DEV fs=30m tsize=${IMG_SIZE}s -data -

```

espero les sirva a alguno, y sigamos posteando scripts, que siempre pueden ser útiles.

---

### Post by Mauro22 on 2008-08-04
Aca les dejo este para achicar o agrandar imagenes:

```
 convert -sample medida original redimensionado
```Donde:
* Medida, ponen los pixeles que necesitan
* Original, archivo de entrada
* Redimensiondado, archivo de salida.

Para pasar parametros seria algo como:

./redimensionar 100x100 mifoto.jpg mifoto_100x100.jpg

```
convert -sample $1 $2 $3
```Siendo 'redimensionar' el script con permisos de ejecucion

---

### Post by Mauro22 on 2008-09-21
Aca les dejo un par de la coleccion XXX a YYY que estoy armando...

```

WMV -> AVI
mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

FLV -> AVI
ffmpeg -i archivo.flv nombreArchivoSalida.avi

FLV -> MPEG
ffmpeg -i video_descargado.flv nuevonombre_video.mpeg

FLV -> MP3
ffmpeg -i videofile.flv -f mp3 audiofile.mp3 

MP3 -> OGG
mp32ogg music.mp3 music.ogg

WMA -> MP3
ffmpeg -i ficheroEntrada.wma -f mp3 -ab 192 ficheroSalida.mp3

MP3 -> AMR
ffmpeg -i music.mp3 -acodec amr_nb -ar 8000 -ac 1 -ab 32 music.amr

WAV -> AMR
ffmpeg -i music.wav -acodec amr_nb -ar 8000 -ac 1 -ab 32 music.amr

MPG -> MP3
ffmpeg -i video.mpg -f mp3 audio_track.mp3

MIDI -> WAV
timidity -Ow -s 44100 -o output.wav input.mid

MIDI -> OGG
timidity -Og -s 44100 -o output.ogg input.mid

AVI -> FLV
ffmpeg -i movie.avi -acodec mp3 -ar 11025 movie.flv

MPG -> FLV
ffmpeg -i pelicula.mpg -vcodec flv -y pelicula.flv

3GP -> AVI
ffmpeg -i movie.3gp -vcodec mpeg4 -acodec mp3 movie.avi


AVI -> VCD
Añadiendo la opción -hq usa alta calidad.
ffmpeg -i myfile.avi -target pal-vcd myfile_vcd.mpg

MPEG -> 3GP
ffmpeg -i archivo.mpeg -s qcif -r 12 -ac 1 -ar 8000 -b 30 -ab 12 salida.3gp

O también con más calidad:

ffmpeg -i archivo.mpeg -s qcif -r 15 -ac 1 -ar 8000 -b 256000 -ab 15 salida.3gp

MPEG -> XviD
ffmpeg -i pelicula.mpg -acodec mp3 -vcodec xvid -b 687 pelicula.avi

PEGAR SUBTITULOS A AVI
mencoder -ovc lavc -oac mp3lame pelicula.avi -o pelicula_con_subtitulos.avi -sub subtitulos.srt

ROTAR VIDEO
rotar 90 grados e invertir (0)
rotar 90 grados (1)
rotar 90 grados en sentido antihorario (2)
rotar 90 grados en sentido antihorario e invertir (3)
mencoder -vf rotate=1 -oac copy -ovc lavc entrada.avi -o salida.avi

RMVB -> AVI
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video_entrada.rmvb -o video_salida.avi

```



Se que no es un script pero creo que deberia ir aca :P


Fuentes: Varias, paginas, blogs y wikipedia.
Todos los creditos a los autores. Coleccion basado en la recopilacion.
(Por si las dudas)

---

### Post by ramiro_md on 2008-09-21
> **Mauro22 said:**
> 
RMVB -> AVI
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video_entrada.rmvb -o video_salida.avi
[/code]

Muchas gracias !!! estoy buscando convertir una peli en rmvb hace 2 horas hasta que me avive a buscar x aca. Sale una estrellita.

---

### Post by Mister X on 2008-09-22
> **Mauro22 said:**
> Aca les dejo un par de la coleccion XXX a YYY que estoy armando...

```

WMV -> AVI
mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

FLV -> AVI
ffmpeg -i archivo.flv nombreArchivoSalida.avi

FLV -> MPEG
ffmpeg -i video_descargado.flv nuevonombre_video.mpeg

FLV -> MP3
ffmpeg -i videofile.flv -f mp3 audiofile.mp3 

MP3 -> OGG
mp32ogg music.mp3 music.ogg

WMA -> MP3
ffmpeg -i ficheroEntrada.wma -f mp3 -ab 192 ficheroSalida.mp3

MP3 -> AMR
ffmpeg -i music.mp3 -acodec amr_nb -ar 8000 -ac 1 -ab 32 music.amr

WAV -> AMR
ffmpeg -i music.wav -acodec amr_nb -ar 8000 -ac 1 -ab 32 music.amr

MPG -> MP3
ffmpeg -i video.mpg -f mp3 audio_track.mp3

MIDI -> WAV
timidity -Ow -s 44100 -o output.wav input.mid

MIDI -> OGG
timidity -Og -s 44100 -o output.ogg input.mid

AVI -> FLV
ffmpeg -i movie.avi -acodec mp3 -ar 11025 movie.flv

MPG -> FLV
ffmpeg -i pelicula.mpg -vcodec flv -y pelicula.flv

3GP -> AVI
ffmpeg -i movie.3gp -vcodec mpeg4 -acodec mp3 movie.avi


AVI -> VCD
Añadiendo la opción -hq usa alta calidad.
ffmpeg -i myfile.avi -target pal-vcd myfile_vcd.mpg

MPEG -> 3GP
ffmpeg -i archivo.mpeg -s qcif -r 12 -ac 1 -ar 8000 -b 30 -ab 12 salida.3gp

O también con más calidad:

ffmpeg -i archivo.mpeg -s qcif -r 15 -ac 1 -ar 8000 -b 256000 -ab 15 salida.3gp

MPEG -> XviD
ffmpeg -i pelicula.mpg -acodec mp3 -vcodec xvid -b 687 pelicula.avi

PEGAR SUBTITULOS A AVI
mencoder -ovc lavc -oac mp3lame pelicula.avi -o pelicula_con_subtitulos.avi -sub subtitulos.srt

ROTAR VIDEO
rotar 90 grados e invertir (0)
rotar 90 grados (1)
rotar 90 grados en sentido antihorario (2)
rotar 90 grados en sentido antihorario e invertir (3)
mencoder -vf rotate=1 -oac copy -ovc lavc entrada.avi -o salida.avi

RMVB -> AVI
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video_entrada.rmvb -o video_salida.avi

```

muy bueno, gracias

---

### Post by sajnox on 2008-09-22
> **ramiro_md said:**
> Muchas gracias !!! estoy buscando convertir una peli en rmvb hace 2 horas hasta que me avive a buscar x aca. Sale una estrellita.

Los archivos con extension rmvb los veo con el mplayer, para hacerlo tuve que seguir este [1] tuto

[1] [http://www.esubuntu.com/c%C3%B3mo_reproducir_archivos_rmvb_en_hardy](http://www.esubuntu.com/c%C3%B3mo_reproducir_archivos_rmvb_en_hardy)

---

### Post by ramiro_md on 2008-09-22
> **sajnox said:**
> Los archivos con extension rmvb los veo con el mplayer, para hacerlo tuve que seguir este [1] tuto

[1] [http://www.esubuntu.com/c%C3%B3mo_reproducir_archivos_rmvb_en_hardy](http://www.esubuntu.com/c%C3%B3mo_reproducir_archivos_rmvb_en_hardy)

GRax por la info sajnox, pero ver los puedo ver tranquilamente con vlc, pasa que lo queria convertir a avi para pasarlo a dvd.
Igualmente buscando y buscando encontre gtk-mencoder para convertir de rmvb a avi. Tambien recomiendo WinFF para convertir entre otros formatos y codecs. Un saludo.

---

### Post by ramiro_md on 2008-09-22
DEjo uno copado para agregar subtitulos a las peliculas :)

mencoder video_sin_subtitulo.avi -sub archivo_subtitulos.srt -oac copy -ovc lavc -o video_con_subtitulo.avi -subcp latin1

Al final se le puede agregar esta línea para especificar letra y el tamaño de la misma:

-font fuente.ttf -subfont-text-scale 3.8

Sinceramente lo probe una vez sola, y me anduvo bien, sin desfasaje. ESpero les sirva. Un saludo.

---

### Post by ramiro_md on 2008-09-22
Uhhh no lo vi en el post de mauro ¬¬ que colgado, borrenlo.

---

### Post by sergiom99 on 2008-10-19
grosso! hoy estrene uno de los de conversion. que no decaiga que debe haber mas scripts para recopilar!

---

### Post by victor_nesta on 2008-10-22
Estuve ocupadito y me perdí varios post.
Pero Este se lleva premios!!!
Que no decaiga che!! 

Hasta ahora mi ganador es ramiro_md de subtítulos, por que no lo había visto en ningún lado y por que revive la consola hasta para eso.  EDITO: Uhhh no lo vi en el post de mauro ¬¬ que colgado, borrenlo. BIS. yo tambien cai

Mas allá de eso, están todos buenisimos y super útiles

---

### Post by fedeavila on 2008-10-22
> **sergiom99 said:**
> Bueno, inspirado en la sugerencia de concurso de valucha, abro este thread para postear los scripts que cada uno haya armado y que sirvan para hacer algo, cualquier cosa, mas sencilla.
Dejo los mios:

```
#!/bin/bash
# ABR/08 SM -- montar.sh --
# monta un archivo .ISO o .NRG
# $1 es el nombre de archivo
# Ej: ./montar.sh /home/videos/peli.ISO

sudo mount -o loop $1 /mnt/tmp
```

```
#!/bin/bash
# ENE/08 SM
# crea un tunel de un puerto local a uno remoto.
# $1 es el numero de puerto
# $2 es el usuario@host_remoto
# $3 es el puerto de ssh remoto
# Ej: ./tunnel.sh 5432 yo@adonde.vos 5022

ssh -L $1:127.0.0.1:$1 $2 -p $3
```

```
#!/bin/bash
# ABR/08 SM
# reordena los archivos del reproductor mp3 q quedan desordenados al copiarlos
# requiere el fatsort:
# sudo apt-get install fatsort
# -- NO HACE FALTA EXPULSARLO NI DESMONTARLO ! --
$MP3DEV = /dev/sdb1

sudo umount $MP3DEV
sudo fatsort $MP3DEV
```

espero le sirva a alguno y todos se prendan a postear los scripts que usan para hacer las cosas mas faciles.

Ojala termine como STICKY.
\Sergio

Che, uno de los tres, el último; el que ordena los archivos dentro del mp4 me sirve mucho porque en windows uso el SortFolder pero en Linux ni idea... Pregunta: No entiendo, donde tengo que poner ese código? En el bloc de notas y guardarlo con alguna extensión especial? ¡Gracias!

---

### Post by sergiom99 on 2008-10-22
si, en los comentarios te dice si tenes que instalar algo mas> 
> #!/bin/bash
# ABR/08 SM
# reordena los archivos del reproductor mp3 q quedan desordenados al copiarlos
# requiere el fatsort:
# sudo apt-get install fatsort
# -- NO HACE FALTA EXPULSARLO NI DESMONTARLO ! --
$MP3DEV = /dev/sdb1

sudo umount $MP3DEV
sudo fatsort $MP3DEV

1. creas un archivo en tu home que se llame ordenar_mp3.sh (o el nombre que te guste) y pegas el contenido. podés hacerlo por consola con nano, vim, mcedit o el editor de texto Kate o el que tenga gnome.
tenés que cambiar el parámetro $MP3DEV a la ruta que tenga tu dispositivo. el mío era /dev/sdb1.
2. en una consola le das permiso de ejecución:
chmod 775 ~/ordenar_mp3.sh
3. en la misma consola lo corrés, parado en tu home:
./ordenar_mp3.sh

Suerte!

---

### Post by sergiom99 on 2008-10-25
Aca dejo uno (viene de la lista de correos) para hacer backups de servidores.
Esta basado en CentOS/RHEL, pero se puede adaptar por eso los comandos estan como variables.
Esta es la version basica que hace una copia de las DB PgSQL.
Yo lo croneo en /etc/crontab pasando el parametro '-cron' al script y termina grabando en DVD/CD con el script que esta posteado en este mismo thread un poco mas atras.

```

# /etc/scripts/backup/backup.sh
# script de backups de servidores CentOS con DB PgSQL
#usar parametro '-cron' para grabar todo a CD. ver ultima linea
#!/bin/sh

OPTION="$1"


#############################################################


TAR="/bin/tar"
LS="/bin/ls"
GREP="/bin/grep"
AWK="/bin/awk"
RM="/bin/rm"
CAT="/bin/cat"
TAR="/bin/tar"
MYSQLDUMP="/usr/bin/mysqldump"
MYSQL="/usr/bin/mysql"
GZIP="/bin/gzip"
DU="/usr/bin/du"
MKDIR="/bin/mkdir"
CP="/bin/cp"
MOUNT="/bin/mount"
UMOUNT="/bin/umount"
CHOWN="/bin/chown"

DISPOSITIVO="/dev/cdrom"
ALIAS_DISPOSITIVO="/mnt/cdrom"
ARCHIVO_LOG="/etc/scripts/backup/backup.log"

START_PGSQL="/etc/rc.d/init.d/postgresql start"
STOP_PGSQL="/etc/rc.d/init.d/postgresql stop"


function maximo_baks()
{
  BACKUP_DIR=$1
  BACKUP_PREFIX=$2
  BACKUP_MAX=$3
  if [ -z "$BACKUP_MAX" ]; then
    nNumBackupsMax=7
  else
    nNumBackupsMax=$BACKUP_MAX
  fi
  BACKUP_TMP="/tmp/info.MAXCOUNT"
  if [ -z "$BACKUP_DIR" ]; then
    echo "BACKUP_DIR is empty"
    exit 1
  fi
  echo -en "/*/ $BACKUP_PREFIX - &#65533;ltimos $nNumBackupsMax backups\n"
  $LS -l $BACKUP_DIR | $GREP "^d" | $GREP "$BACKUP_PREFIX" | $AWK '{print $9}' > $BACKUP_TMP
  NUMBACKUPS=`$CAT $BACKUP_TMP | wc -l`
  if [ $NUMBACKUPS -eq $nNumBackupsMax ]; then
    COUNT=1
    $RM -f ${BACKUP_TMP}2
    $CAT ${BACKUP_TMP} | while read filename
    do
      if [ $COUNT -eq 1 ]; then
         echo "* deleting: $filename"
         $RM -fr $BACKUP_DIR/$filename
         COUNT=2
      else
         echo "-   adding: $filename"
         echo $filename >> ${BACKUP_TMP}2
      fi
    done
  else
    if [ $NUMBACKUPS -gt $nNumBackupsMax ]; then
    COUNT=1
    TOTAL=`$CAT $BACKUP_TMP | wc -l`
    let TOTAL=TOTAL-$nNumBackupsMax+2
    $CAT $BACKUP_TMP | while read filename
    do
      if [ $COUNT -lt $TOTAL ]; then
         echo "* deleting: $filename"
         $RM -fr $BACKUP_DIR/$filename
         let COUNT=COUNT+1
      else
         echo "-   adding: $filename"
         echo $filename >> ${BACKUP_TMP}2
      fi
    done
    fi
  fi
  $RM -f $BACKUP_TMP ${BACKUP_TMP}2
  echo -en "-- Backups Actuales --\n"
  $LS -l $BACKUP_DIR | $GREP "^d" | $GREP "$BACKUP_PREFIX"
  echo -en "\n"
}

function do_sysbackup()
{
  local THIS_BAK
  THIS_BAK="sys-${HOSTNAME}-${CUR_DATE}"
  mkdir $THIS_BAK

  echo "Backing up SYS at $HOSTNAME"
  echo "* Backing up DNS"
  $TAR cvfz $THIS_BAK/${HOSTNAME}-named-$CUR_DATE.tar.gz /etc/named.conf /var/named > /dev/null
  echo _____________________________________________________________________________
  echo "* Backing up /etc"
  $TAR cvfz $THIS_BAK/${HOSTNAME}-etc-$CUR_DATE.tar.gz /etc/ > /dev/null
  echo _____________________________________________________________________________
  echo "* Backing up system files"
  $TAR cvfz $THIS_BAK/${HOSTNAME}-recomended-$CUR_DATE.tar.gz \
      /etc/passwd* /etc/shadow* \
      /etc/fstab* /etc/inittab /boot/* /etc/resolv.conf /etc/modules.* /etc/host* \
      /var/lib/rpm/* > /dev/null
  echo _____________________________________________________________________________
  echo "* SMB"
  $TAR cvfz $THIS_BAK/${HOSTNAME}-smb-$CUR_DATE.tar.gz \
      /etc/samba/* /etc/pam.d/ > /dev/null
  echo _____________________________________________________________________________
  echo "* homes"
  $TAR cvfz $THIS_BAK/${HOSTNAME}-homes-$CUR_DATE.tar.gz \
      /home/* > /dev/null
  echo ________________________________ END BACK UP _________________________________
}

############################################################
## pgSQL
############################################################

PG_DUMP=/usr/bin/pg_dump
PSQL=/usr/bin/psql

function do_pgsql_backup()
{
  local THIS_BAK
  THIS_BAK="pgsql-${HOSTNAME}-${CUR_DATE}"
  mkdir $THIS_BAK
  echo -en "\n\nBacking up pgSQL at $HOSTNAME\n"

  SQL_DB="SELECT datname
            FROM pg_database
           WHERE datname NOT IN ('template0','template1') ORDER BY 1"
  echo $SQL_DB | $PSQL -U $PSQL_USER template1 -t | awk '!/^$/ { print $0}' | \
  while read DATABASE
  do
    echo "SCHEMAS in DB $DATABASE"
    if [ -z $DEBUG ]; then
      SQL_SCHEMA="SELECT DISTINCT schemaname
                    FROM pg_catalog.pg_tables
                   WHERE schemaname NOT IN ('information_schema','pg_catalog')"
    else
      SQL_SCHEMA="SELECT DISTINCT schemaname
                    FROM pg_catalog.pg_tables
                   WHERE schemaname IN ('public')"
    fi
    echo $SQL_SCHEMA | $PSQL -U $PSQL_USER $DATABASE -t | awk '!/^$/ { print $0}' | \
      while read SCHEMA
      do
        echo -en " * $SCHEMA\t"
        CUR_BACKUP_FILE="${THIS_BAK}/${HOSTNAME}-pgsql-${DATABASE}-${SCHEMA}-${CUR_DATETIME}.sql"
        $PG_DUMP --username=$PSQL_USER ${DATABASE} --schema=${SCHEMA} > $CUR_BACKUP_FILE
        if [ "$?" -eq 0 ]; then
          $GZIP $CUR_BACKUP_FILE
          if [ "$?" -eq 0 ]; then
            echo -en "OK\n"
          else
            echo -en "(could not compress file)\n"
          fi
        else
          echo -en "(cannot make dump)\n"
        fi
      done
  done
  /usr/bin/vacuumdb -U postgres -a -z
}

function tar_var_lib_pgsql()
{
  local THIS_BAK
  THIS_BAK="pgsql-data-${HOSTNAME}-${CUR_DATE}"
  mkdir $THIS_BAK
  echo -en "\n\nBacking up pgSQL (data) at $HOSTNAME\n"

  echo "copying data ..."
  $STOP_PGSQL
  $CP -r /var/lib/pgsql /var/lib/pgsql-${CUR_DATETIME}
  $START_PGSQL
  echo "compressing ..."
  TIME="Completado en: %E min." /usr/bin/time \
  $TAR cfj $THIS_BAK/pgsql-data-${HOSTNAME}-${CUR_DATETIME}.tar.bz2 \
           /var/lib/pgsql-${CUR_DATETIME}/data/
  $RM -fr /var/lib/pgsql-${CUR_DATETIME}
#  $CP $THIS_BAK/pgsql-data-${HOSTNAME}-${CUR_DATETIME}.tar.bz $ALIAS_DISPOSITIVO
  echo "end."
}

##############################################################
## BACKUP
##############################################################

BACKUP_DIR="/backup"
CUR_DATE=$(date +%Y-%m-%d)
CUR_DATETIME=$(date +%Y-%m-%d_%H-%M-%S)
CUR_BACKUP="backup_${CUR_DATE}"

## STARTing

$MKDIR -p $BACKUP_DIR/$CUR_BACKUP 2> /dev/null

## starting...
maximo_baks $BACKUP_DIR "backup_"

cd $BACKUP_DIR/$CUR_BACKUP

do_sysbackup
## pgSQL backup
PSQL_USER=postgres
do_pgsql_backup

if [ "$OPTION" == "-cron" ]; then
  tar_var_lib_pgsql
  echo /etc/scripts/backup/burn_cd.sh $BACKUP_DIR/$CUR_BACKUP $CUR_DATE
  /etc/scripts/backup/burn_cd.sh $BACKUP_DIR/$CUR_BACKUP $CUR_DATE
fi


```

---

### Post by Etrigan on 2008-11-15
aca les dejo uno que realiza una lista de todos los paquetes intalados en la distribucion guardandolos en un plano con dia y hora de nombre. 
Me es  muy util a la hora de actualizar la distribucion, para tener presente los paquetes que antes tenia. 
Tambien lo utilizo en caso de una pifia, para poder restaurar los paquetes como los tenia antes del ultimo apt-get instal
 ```

 #!/bin/bash


# Lista de Paquetes 
# se forma el nombre del archivo
DIA=`date +%d`
MES=`date +%m`
AnO=`date +%Y`
time=`date +%R`


ARCHIVO=paquetes.$AnO-$MES-$DIA.$time.lst
# lista y ordena los paquetes instalados
dpkg --get-selections | grep -v deinstall | sort  > ~/Documentos/Respaldo/$ARCHIVO 

```

---

### Post by Zootropo on 2008-11-16
Aquí están mis scripts para Nautilus, por si a alguno le interesa:

[http://mundogeek.net/nautilus-scripts/](http://mundogeek.net/nautilus-scripts/)


[LIST]
[*]nautilus-send-gmail: para enviar archivos a Gmail.
[*]nautilus-mount-image: para montar imágenes de DVD y CD
[*]nautilus-tag-music: para cambiar las etiquetas ID3 de los MP3 y establecer género, artista, año, disco y nombre de la canción basándose en el path
[*]nautilus-rename-exif-date: para renombrar las fotografías a la fecha y hora en la que fueron tomadas
[*]nautilus-play-amarok: para reproducir la carpeta o archivos seleccionados en Amarok
[*]nautilus-play-banshee: para reproducir la carpeta o archivos seleccionados en Banshee
[*]nautilus-play-mplayer: para reproducir la carpeta o archivos seleccionados en MPlayer
[/LIST]

---

### Post by brunovecchi on 2008-11-16
[B]
Para cambiar el fondo de pantalla aleatoriamente[/B] entre las imágenes de un directorio. Si el nombre del archivo de imágen comienza con la palabra "tile", setea que se muestre la imagen en mosaico.

Se puede programar la ejecución de este script mediante cron para que se ejecute regularmente. Yo lo puse en el archivo .profile, para que haya un wallpaper nuevo en cada inicio de sesión.


```
#!/bin/bash
picsfolder=$HOME"/Imagenes/Wallpapers/"

cd $picsfolder

files=( *.jpg )

N=${#files[@]}

((N=RANDOM%N))

randomfile=${files[$N]}
echo $randomfile

A=`echo $randomfile | sed 's/^\(\w\{4\}\).*/\1/'`
if [ "$A" = "tile" ]; then
    OPTION="wallpaper"
    echo $OPTION
else
    OPTION="streched"
    echo $OPTION
fi


gconftool-2 -t str --set /desktop/gnome/background/picture_filename $picsfolder$randomfile

gconftool-2 -t str --set /desktop/gnome/background/picture_options $OPTION #posibles valores "none", "wallpaper" (mosaico), "centered" "scaled", "stretched"
```

**Renombrar archivos**, reemplazando espacios por guiones.

```
#!/bin/bash
for F in `ls`; do B=`echo $F | sed 's/\s/-/g'`; mv $F $B; done

```

**Compilar un archivo LaTeX** usando la línea de comandos.

```
#!/bin/bash
# Chequear que haya un archivo como argumento
if [ -z "$1" ]; then 
    	echo usage: $0 document.tex
		exit
		fi

# quitarle la extensión al archivo.
FILE=`basename $1`

# Compilar usando rubber, luego abrir el pdf si el proceso tuvo éxito.
rubber -f -s --inplace -d "$1" && gnome-open $FILE.pdf &

# Eliminar los archivos basura que deja latex por ahí.
mv *.{aux,bbl,blg,brf,idx,ilg,ind,log,out,toc,dvi,ps,*~,chktex*} $HOME/.local/share/Trash/files 2> /dev/null
```

---

### Post by granjero on 2008-11-20
hola, espero no estar offtopicqueando...

yo necesito un script o algo para que cada vez que mi proveedor de internet me cambie la ip del ordenador me envie el nuevo ip a una casilla de mail. esto es porque el VNC se maneja por ip y cuando quiero loguear y me cambio la ip no puedo averiguarla y no me puedo loguear...

alguno lo tiene bajo la manga?

salud!

[-o<
[-o<
[-o<

---

### Post by Mauro22 on 2008-11-20
Lo mas sencillo es usar el cliente de NO-IP para linux

[http://www.no-ip.com/downloads.php?page=linux](http://www.no-ip.com/downloads.php?page=linux)


Con este programa reemplazas el uso de direcciones IP por nombres de host.


```

**Keep your current IP address in sync with your No-IP host or domain** with our Dynamic Update Client (DUC). Our dynamic DNS update client continually checks for IP address changes in the background and automatically updates the DNS at No-IP whenever it changes.

```

---

### Post by sergiom99 on 2008-11-20
esto lo podes hacer con dyndns y el ddclient que corre como demonio en linux.
[http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

suerte.

---

### Post by c4d0rn4 on 2008-12-21
Rianse conmigo... xD

Mi intento de crear el comando automatizado "sumo"
```
#!/bin/bash
(sleep 1 && echo "password
")&
sudo $1
```
Si lo ejecutan no sirve, pero creo que alguno le puede causar gracia el resultado final.

----------------------
Se que para hacer cosas así está el sudoers, y que no es seguro tener algo así, pero yo no tengo cosas tan importantes y la verdad es poco probable que justo "adivinen" el nombre del sh que ejecuta sudo con el pass; el nombre del sh podría ser supercalifraglisticoespecialidosos y no sumo jaja XD.

creen que si hago un sh, con 
```
sudo $1
``` y lo agrego a sudoers para que no pida pass funcione?
Nunca toque lo de sudoers porque no me llevo bien con vi.

---

### Post by sergiom99 on 2009-01-03
bump!
Agreguen sus scripts che!

---

### Post by MeduZa on 2009-01-07
excelentes para meter en el nautilus actions xD

---

### Post by sergiom99 on 2009-01-08
MeduZa, 
en otro thread me decias que no hace falta montar las iso con el primer script del thread para reproducirlas, pero esto lo tengo que hacer si o si con otras extensiones de imagenes (IMG y NRG) porque Kaffeine no las abre de una. (o no encontre la forma de hacerlo)
Saludos-

---

### Post by sergiom99 on 2009-02-06
Este script para actualizar las claves de los repositorios de launchpad no puede faltar:
[http://b2dbuntu.wordpress.com/2009/01/29/solucion-actualizar-las-llaves-publicas-gpg-de-launchpad-en-ubuntu/](http://b2dbuntu.wordpress.com/2009/01/29/solucion-actualizar-las-llaves-publicas-gpg-de-launchpad-en-ubuntu/)
Creditos al autor del script **blackgr** y al autor del blog.

---

### Post by Mauro22 on 2009-02-06
Aca les dejo un script para ver tv y escuchar radios (Se pueden agregar muy facil, yo agregue un par)

```

#!/bin/bash 
# 
# llama a mplayer, segun la radio indicada 
# 
# $Id: radio,v 1.8 2007-01-04 14:48:32 javier Exp $ 
# 
# Fixes en etapa de ejecucion por Arturo 'Buanzo' Busleiman 
# - 20070104 

case "$1" in 

# 
# radios argentinas 
# 

mitre) # Radio Mitre 792 AM 
URII='mms://streammitre.uigc.net/mitrevivo' 
;; 
rp) # Rock and Pop 
URII="mms://200.59.146.10/rockandpop-ba" 
;; 
delplata) # Del Plata AM 1030 
URII='mms://delplata.telecomdatacenter.com.ar/delplata' 
;; 
continental) # AM 590 Continental 
URII='http://66.175.96.10/arcontinental' 
;; 
los40) # Los 40 Principales 
URII='http://66.175.96.10/ARLOS40P' 
;; 
mega) # Mega 98.3 Puro Rock Nacional 
URII='http://mega.telecomdatacenter.com.ar/mega' 
;; 
fm100) # FM 100 99.9 rtsp://g2.prima.com.ar/vivo/cadena100.rm 
URII='mms://streamla100.uigc.net/la100' 
;; 
fmsi) # 89.1 FM BA San Isidro 
# (requiere faad/aac) 
URII='http://streaming.euro-web.com.ar:8000' 
;; 
america) # Radio 10 (Dolina) AM 710 
URII='mms://radio10.telecomdatacenter.com.ar/radio10' 
;; 
itaipu) # 105.7 FM Brasil Foz do Iguazu 
URII='mms://streamer-br1.apkomp.com.br/itaipufm' 
;; 
rmisiones) # FM Radio Misiones 
URII='http://streammax.alsolnet.com/radiomisiones' 
;; 
city) # Radio City 107.1 FM 
URII='http://69.65.102.148:8000/' 
;; 
lared) # Radio La Red AM 9100 
URII='mms://lared.wms.sinectis.com.ar/laredam910' 
;; 

# 
# television 
# 

tn24) # TN 24 Horas 
URII="mms://streamtn.uigc.net/TN" 
;; 
cn13) # Canal 13 de Bs As 
URII="mms://canal13.uigc.net/canal13vivo" 
;; 
cn26) # Canal 26 de Bs As 
URII="http://200.115.194.1:8080/Canal26" 
;; 
cn6) # Canal 6 de Posadas 
URII="http://streampwr.alsolnet.com:89/noticiasdel6" 
;; 
cn7) # Canal 7 de Bs As 
URII="mms://canal7envivo.telecomdatacenter.com.ar/canal7envivo" 
;; 
tv5) # CcTV5 
URII="mms://202.201.0.202/CCTV5" 
;; 
cn11) # America 24 
URII="mms://win.1.c2.audiovideoweb.com/1c2winlive6551" 
;; 
cn10) # Telefe
URII="http://wm.streamingmediahosting.com/telefe-internacional"
;;
sony) # Sony Music
URII="mms://morrich.gekimedia.net/MainStream500"
;;
c5n) # C5N
URII="http://www.ustream.tv/flash/live/199131"
;;
cm) # Canal de Musica
URII="http://es.delicast.com/tv/Argentina/CMTV"
;;

# 
# otras radios 
# 

kehuelga) #Radio libre y social 102.9FM > 
URII="http://www.kehuelga.org:8000/radio.mp3" 
#Aca estan otros espejos en caso de saturacion: 
#http://stream.r23.cc:2323/kehuelga.mp3 
#http://radio.resistenciacreativa.org.mx:8000/radioresisteincia.mp3.m3u 
#http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u 
#http://radio.indymedia.org:8000/appo.mp3.m3u 
;; 

*) 
echo " 
Uso: radio.sh opcion 

mitre ( Radio Mitre 792 AM ) 
rp ( Rock and Pop ) 
delplata ( Del Plata AM 1030 ) 
continental ( Contiental AM 590 ) 
los40 ( Los 40 Principales ) 
mega ( Mega 98.3 Puro Rock Nacional ) 
fm100 ( FM 100 99.9 ) 
fmsi ( FM BA San Isidro 89.1 ) 
america ( Radio America ) 
itaipu ( Radio Itaipu Brasil) 
rmisiones ( Radio Misiones) 
city ( Radio City Jujuy ) 
lared ( La Red ) 

kehuelga ( Radio libre y social 102.9 FM ) 

tn24 ( TN 24 Horas ) 
cn13 ( Canal 13 de Bs As) 
cn26 ( Canal 26 Bs As) 
cn6 ( Canal 6 Posadas) 
cn7 ( Canal 7 de Bs As) 
tv5 ( CCtv5) 
cn11 ( America 24) 
" 
exit 1 
;; 
esac 

mplayer -af lavcresample=44100 -cache 512 "$URII"

```

Y este es para limpiar:

¿ Remueve el cache de apt
¿ Remueve archivos de configuracion viejos
¿ Remueve kernels menos el que esta en uso
¿ Vacia la papelera

```

#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: Se necesitan privilegios de superusuario"
  echo -e $YELLOW"Saliendo..."$ENDCOLOR
  exit 0
fi

echo -e $YELLOW"Limpiando cache de aptitude..."$ENDCOLOR
aptitude clean

echo -e $YELLOW"Borrando archivos de configuracion antiguos..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"Borrando kernels antiguos..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Vaciando Papelera..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Listo!"$ENDCOLOR

```

PD: Este ultimo, no lo probe. no se si funciona o necesita alguna modificacion.

La base no me acuerdo de donde la saque. Pero los creditos van a quien lo hizo.

---

### Post by c4d0rn4 on 2009-02-08
Transforma en mp3 las canciones de Imeem

en realidad necesitaría una limpieza, dado que es una mezcla de varias cosas que saqué de internet y al final ejecuto un loop para un solo archivo jaja xD

```
#!/bin/bash
cd /tmp/
cp Flash* ~/mp3/
cd ~/mp3/
mplayer -dumpstream Flash*
rm Flash*
for i in *.dump
do 
ffmpeg -i "${i}" -acodec pcm_s16le -ac 2 -ab 128k -vn -y "$1.wav"
lame --preset cd "$1.wav" "$1.mp3"
rm "$1.wav"
rm *.dump
done
exit
```

Uso:

debe haber una carpeta mp3 en home, o cambian eso, o
```
cd ~
mkdir mp3
```

Si escuchan un video o audio en imeem, y ya se terminó de cargar la barra de streaming, ejecutan el script (supongamos se llama imeem el archivo).

en la terminal donde esté el archivo

sh imeem Nombre_del_archivo_como_les_guste

ejm: sh imeem Claro_de_Luna-Ludwig_van_Beethoven

---

### Post by Air23 on 2009-02-11
Un script que sirve para poner como icono de todas las carpetas de musica la tapa de los distintos discos.

Hacer esto disco por disco es una autentica tortura por lo cual cuando lo encontre en el foro general toque el cielo con las manos. 

Descarga:[custom_icon.py](http://ubuntuforums.org/attachment.php?attachmentid=28357&d=1174971303)

Uso:
```
$ python custom_icon.py --help
usage: custom_icon.py [options] folder [folder2 ...]

options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  --names=NAMES    specification to match image filenames [default:
                   "[Ff]older.jpg"]
  -R, --recursive  set icons for folders recursively

$ python custom_icon.py ~/music
/home/user/music ...
done.

$ nautilus -q
```

Fuente: [http://ubuntuforums.org/showpost.php?p=2359786&postcount=18](http://ubuntuforums.org/showpost.php?p=2359786&postcount=18)

---

### Post by sergiom99 on 2009-02-11
Gracias Air23, ya cree un indice para buscar mas facil.
Si alguno se anima se pueden transcribir al wiki.

---

### Post by c4d0rn4 on 2009-02-17
hoy vi un EXCELENTE post the makeuseof y quería compartirlo, [4 Websites To Learn Cool Linux Command Line Tricks]("http://www.makeuseof.com/tag/4-websites-to-learn-cool-linux-command-line-tricks/")

En mi opinion debería tener un thread aparte, pero acá está bien dado que puede ser fuente de inspiración para muchos futuros scripts

---

### Post by Mauro22 on 2009-03-02
Estos no son scripts pero son comandos... y para no abrir un post nuevo, lo mando aca...


Montar un servidor http:

```
python -m SimpleHTTPServer
```

Esto, primero se van a la carpeta donde quieren el servidor y ponen ese comando.
Todo lo que este en esa carpeta y subcarpetas sera compartido a traves de internet, entrando a:
```
http://SUIP:8000
```

y localmente:
```
http://localhost:8000
```


Esta muy bueno... con ese comando tienen la posibilidad de compartir archivos, etc. Tambien lee los index.htm, asi que pueden poner una web o algo. Yo hice un index que pide contraseña para que no se me mande ningun mono...


---------------------------------


Este es para ver peliculas en la consola ¿? OMFG!!
Mplayer es capaz de mostrar la pelicula en ASCII mediante la consola...

El parametro caca (si caca !! ) es para verla en colores...
```
mplayer -vo caca pelicula.avi
```

aa es para en escala de grises!
```
mplayer -vo aa pelicula.avi
```

---

### Post by sergiom99 on 2009-04-06
Encontre este script buenisimo para convertir peliculas a formato Ipod.
[http://thomer.com/howtos/ipod_video.html](http://thomer.com/howtos/ipod_video.html)

Fuente original: [http://ubuntuforums.org/showthread.php?t=507558](http://ubuntuforums.org/showthread.php?t=507558)

---

### Post by totolinux on 2009-05-07
Aquí posteo un comando para ver en el Terminal la película "La Guerra de las Galaxias" Muy loco el que se tomo el trabajo =D> 

 $ telnet towel.blinkenlights.nl

Fuente: 

[http://braulioaquino.blogspot.com/2008/07/star-wars-telnet-towelblinkenlightsnl.html](http://braulioaquino.blogspot.com/2008/07/star-wars-telnet-towelblinkenlightsnl.html)

Agrego el script (radios) con algunos retoques me es muy muy util

Code:

#!/bin/bash 
# 
# llama a mplayer, segun la radio indicada 
# 
# $Id: radio,v 1.8 2007-01-04 14:48:32 javier Exp $ 
# 
# Fixes en etapa de ejecucion por Arturo 'Buanzo' Busleiman 
# - 20070104 

case "$1" in 

# 
# radios argentinas 
# 

mitre) # Radio Mitre 792 AM 
URII='mms://streammitre.uigc.net/mitrevivo' 
;; 
rp) # Rock and Pop 
URII="http://streaming.fmrockandpop.com/rockandpop" 
;; 
delplata) # Del Plata AM 1030 
URII='mms://delplata.telecomdatacenter.com.ar/delplata' 
;; 
continental) # AM 590 Continental 
URII='http://66.175.96.10/arcontinental' 
;; 
los40) # Los 40 Principales 
URII='http://66.175.96.10/ARLOS40P' 
;; 
mega) # Mega 98.3 Puro Rock Nacional 
URII='http://mega.telecomdatacenter.com.ar/mega' 
;; 
fm100) # FM 100 99.9 rtsp://g2.prima.com.ar/vivo/cadena100.rm 
URII='mms://streamla100.uigc.net/la100' 
;; 
fmsi) # 89.1 FM BA San Isidro 
# (requiere faad/aac) 
URII='http://streaming.euro-web.com.ar:8000' 
;; 
america) # Radio 10 (Dolina) AM 710 
URII='mms://radio10.telecomdatacenter.com.ar/radio10' 
;; 
itaipu) # 105.7 FM Brasil Foz do Iguazu 
URII='mms://streamer-br1.apkomp.com.br/itaipufm' 
;; 
rmisiones) # FM Radio Misiones 
URII='http://streammax.alsolnet.com/radiomisiones' 
;; 
city) # Radio City 107.1 FM 
URII='http://69.65.102.148:8000/' 
;; 
lared) # Radio La Red AM 9100 
URII='mms://lared.wms.sinectis.com.ar/laredam910' 
;; 
rf) # Radio Fónica 100.5 FM Rosario 
URII='http://player.services.digitar.net/files/radiofonica/radiofonica.asx' 
;; 
taringa) # Taringa Radio 
URII='http://stream.giss.tv:8000/Taringaradio.mp3' 
;; 
aspen) #Radio Aspen 102.3
URII='mms://200.59.146.10/radioaspen-ba'
;;

# 
# television 
# 

tn24) # TN 24 Horas 
URII="mms://streamtn.uigc.net/TN" 
;; 
cn13) # Canal 13 de Bs As 
URII="http://es.wwitv.com/tv/b1635.htm"
#URII="mms://canal13.uigc.net/canal13vivo" 
;; 
cn26) # Canal 26 de Bs As 
URII="http://200.115.194.1:8080/Canal26" 
;; 
cn6) # Canal 6 de Posadas 
URII="http://streampwr.alsolnet.com:89/noticiasdel6" 
;; 
cn7) # Canal 7 de Bs As 
URII="mms://canal7envivo.telecomdatacenter.com.ar/canal7envivo" 
;; 
tv5) # CcTV5 
URII="mms://202.201.0.202/CCTV5" 
;; 
cn11) # America 24 
URII="mms://win.1.c2.audiovideoweb.com/1c2winlive6551" 
;; 
cn10) # Telefe
URII="http://wm.streamingmediahosting.com/telefe-internacional"
;;
sony) # Sony Music
URII="mms://morrich.gekimedia.net/MainStream500"
;;
c5n) # C5N
URII="http://www.ustream.tv/flash/live/199131"
;;
cm) # Canal de Musica
URII='mms://200.32.3.35:9080 '
;;
national) # National Geographic English
URII="mms://211.167.102.66/ch-19"
;;
discovery) # Discovery Channel English
URII="mms://211.167.102.68/ch-11"
;;


# 
# otras radios 
# 

kehuelga) #Radio libre y social 102.9FM > 
URII="http://www.kehuelga.org:8000/radio.mp3" 
#Aca estan otros espejos en caso de saturacion: 
#[http://stream.r23.cc:2323/kehuelga.mp3](http://stream.r23.cc:2323/kehuelga.mp3) 
#[http://radio.resistenciacreativa.org.mx:8000/radioresisteincia.mp3.m3u](http://radio.resistenciacreativa.org.mx:8000/radioresisteincia.mp3.m3u) 
#[http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u](http://radio.indymedia.org:8000/radiozapote-alta.mp3.m3u) 
#[http://radio.indymedia.org:8000/appo.mp3.m3u](http://radio.indymedia.org:8000/appo.mp3.m3u) 
;; 

*) 
echo " 
Uso: radio.sh opcion 

mitre ( Radio Mitre 792 AM ) 
rp ( Rock and Pop ) 
delplata ( Del Plata AM 1030 ) 
continental ( Contiental AM 590 ) 
los40 ( Los 40 Principales ) 
mega ( Mega 98.3 Puro Rock Nacional ) 
fm100 ( FM 100 99.9 ) 
fmsi ( FM BA San Isidro 89.1 ) 
america ( Radio America ) 
itaipu ( Radio Itaipu Brasil) 
rmisiones ( Radio Misiones) 
city ( Radio City Jujuy ) 
lared ( La Red ) 
rf ( Radio Fónica 100.5 FM Rosario )
kehuelga ( Radio libre y social 102.9 FM ) 
taringa ( Taringa Radio )
aspen ( Radio Aspen 102.3 )

tn24 ( TN 24 Horas ) 
cn13 ( Canal 13 de Bs As) 
cn26 ( Canal 26 Bs As) 
cn6 ( Canal 6 Posadas) 
cn7 ( Canal 7 de Bs As) 
tv5 ( CCtv5) 
cn11 ( America 24) 
sony ( Sony Music)
cm  (Canal de Musica)
cn10 (Telefe)
c5n (C5N)
national (National Geographic English)
discovery (Discovery Channel English)
" 
exit 1 
;; 
esac 

mplayer -af lavcresample=44100 -cache 512 "$URII"

---

### Post by beatlina on 2009-06-30
A ver si alguien me ayuda... porque no entiendo nadinas ... Me gustaría hacer un script que me abra los tres programas de siempre abro cuando prendo la Pc que son Amsn, Pidgin y el Checkgmail. debería hacer yo algo así¿¿???
> 

#!/bin/bash
# pidgin &
# amsn &
# checkgmail &



---

### Post by staar on 2009-06-30
está bien, pero tendías que descomentar (borrar el # del comienzo) las líneas para que te inicien los programas, y dejar un espacio antes de /bin/bash, sería asi..```

#! /bin/bash
pidgin &
amsn &
checkgmail &
``` después le das permisos de ejecución (desde las propiedades), y lo agregás en Sistema > Preferencias > Sesiones...

saludos

---

### Post by beatlina on 2009-07-01
Chas gracias Staar...

---

### Post by staar on 2009-07-15
a este lo tengo en mi .bashrc, es muy útil ```

ex ()
{
  if [ -f $1 ] ; then
    case $1 in
      *.tar.bz2)   tar xjf $1   ;;
      *.tar.gz)    tar xzf $1   ;;
      *.bz2)       bunzip2 $1   ;;
      *.rar)       unrar x $1     ;;
      *.gz)        gunzip $1    ;;
      *.tar)       tar xf $1    ;;
      *.tbz2)      tar xjf $1   ;;
      *.tgz)       tar xzf $1   ;;
      *.zip)       unzip $1     ;;
      *.Z)         uncompress $1;;
      *.7z)        7z x $1      ;;
      *)           echo "'$1' no puede ser extraido por ex()" ;;
    esac
  else
    echo "'$1' no es un archivo valido"
  fi
}
``` el uso es ```
ex *archivoaextraer*
```

saludos

---

### Post by aledruetta on 2009-07-25
Hola, pregunto antes de meter la pata:

En Taringa hay un script para bajar los 50 números atrasados de la revista Linux Magazine ¿Se puede agregar? El que creó el post dice "que lo robó por ahí" y no dice dónde.

---

### Post by Hei Ku on 2009-07-25
No, no se puede agregar ningun contenido o link que no respete las licencias de derechos de autor.

---

### Post by alguien845 on 2009-11-06
Los que lei sobre alias no me gustaron, asi que agrego el mio:
```

#!/bin/bash
#Scrip para Agregar alias personales
#Mariano Zunino, 6/9/09
#alguien845@hotmail.com
cls
echo "        SCRIPT PARA AGREGAR ALIAS"
echo - Desisntalar 
echo - Instalar     
echo - Reset GDM
echo - Reset RED
echo - Cls
echo - Go to Home
echo - Go to /
echo "- cd .."
echo - ADSL
echo "           .:Presionar Enter:."
echo "        .:Ctrl+c para cancelar:."
read -n1

echo alias desinstalar="'sudo apt-get remove'" >> ~/.bashrc && source ~/.bashrc
echo alias instalar="'sudo apt-get install'" >> ~/.bashrc && source ~/.bashrc
echo alias resetgdm="'/etc/init.d/gdm restart'" >> ~/.bashrc && source ~/.bashrc
echo alias resetred="'/etc/init.d/networking restart'" >> ~/.bashrc && source ~/.bashrc
echo alias cls="'clear'" >> ~/.bashrc && source ~/.bashrc
echo alias cd..="'cd ..'" >> ~/.bashrc && source ~/.bashrc
echo alias .h="'cd ~'" >> ~/.bashrc && source ~/.bashrc
echo alias .r="'cd /'" >> ~/.bashrc && source ~/.bashrc
echo alias ADSL="'sudo pon dsl-provider'" >> ~/.bashrc && source ~/.bashrc



echo LISTO
echo SALIENDO Y LIMPIANDO CONSOLA
echo
echo PRESIONE ENTER
read -n1
cls

```
No lo hice "simple"(o osea insertar el codigo de one y listo) porque se lo pase a varios amigos que son novatillos y servia mas que funcionara mas asi, "guiado"...

---

### Post by sergiom99 on 2010-02-11
**Script para tomar capturas de pantalla a intervalos regulares**

```

## capturas.sh
#!/bin/bash
scrot -e 'mv $f ~/Pictures/scrot/`date +%d-%m-%y_%H:%M:%S`_sreenshot.png'

```

Esto lo corremos con 

```
watch -n 3 ./capturas.sh
```

y va a grabar cada 3 segundos un snapshot de la pantalla actual en ~/Pictures/scrot.

(Gracias alfplayer por la idea del watch)

---

### Post by jmanuel_cool on 2010-04-05
Ok, uno mío es para descargar con el wget:

```
#!/bin/bash
##llama a wget y descarga lo que le indiquemos con la velocidad que digamos
## y en la carpeta que queramos
clear
echo "Puedes ingresar un archivo de texto"
echo "con las direcciones asi: '-i archivo.txt'"
sleep 2
echo -n "Ingresa la direccion a Descargar: "
read descarga
sleep 1
echo "El Destino debe ser una carpeta existente en tu PC"
echo -n "Ingresa la Carpeta de Destino: "
read destino
sleep 1
echo "La Velocidad es en kb o mb Ej: 50k 1m"
echo "o ingresa 0 (cero) para ilimitado"
echo -n "Ingresa la Velocidad de Descarga: "
read velocidad
sleep 1
wget -c --limit-rate=$velocidad -P$destino $descarga
fichero=`basename $descarga`
hora=$(date +%H:%M:%S)
echo "Finalizada la descarga de $fichero en $destino a las $hora"
sleep 3
```

Se puede guardar en /usr/bin con permisos de ejecución y si se ejecuta desde la carpeta donde se quiere la descarga solo se indica con un punto (.) para decirle que lo baje allí mismo

---

### Post by gadolinio on 2010-05-07
Hola a todos. Posteo un sencillo script para cambiar la previsualización de imágenes, entre "nunca" y "sólo archivos locales". La idea es poder solamente hacer un click en un lanzador a modo de toggle button, en vez de ir a buscar las preferencias de nautilus o ir a sistema--> preferencias--> gestión de archivos, buscar la solapa de vista previa, desplegar la lista, seleccional la opción deseada, y cerrar la ventana.

```

#!/bin/bash

SHOW=$(gconftool-2 --get /apps/nautilus/preferences/show_image_thumbnails)

if [ $SHOW = "never" ] ; then
   gconftool-2 --type string --set /apps/nautilus/preferences/show_image_thumbnails "local_only"
   else
   gconftool-2 --type string --set /apps/nautilus/preferences/show_image_thumbnails "never"
   fi

```

---

### Post by kmai on 2010-05-12
> **sergiom99 said:**
> Bueno, inspirado en la sugerencia de concurso de valucha, abro este thread para postear los scripts que cada uno haya armado y que sirvan para hacer algo, cualquier cosa, mas sencilla.
Dejo los mios:

```
#!/bin/bash
# ABR/08 SM -- montar.sh --
# monta un archivo .ISO o .NRG
# $1 es el nombre de archivo
# Ej: ./montar.sh /home/videos/peli.ISO

sudo mount -o loop $1 /mnt/tmp
``````
#!/bin/bash
# ENE/08 SM
# crea un tunel de un puerto local a uno remoto.
# $1 es el numero de puerto
# $2 es el usuario@host_remoto
# $3 es el puerto de ssh remoto
# Ej: ./tunnel.sh 5432 yo@adonde.vos 5022

ssh -L $1:127.0.0.1:$1 $2 -p $3
``````
#!/bin/bash
# ABR/08 SM
# reordena los archivos del reproductor mp3 q quedan desordenados al copiarlos
# requiere el fatsort:
# sudo apt-get install fatsort
# -- NO HACE FALTA EXPULSARLO NI DESMONTARLO ! --
$MP3DEV = /dev/sdb1

sudo umount $MP3DEV
sudo fatsort $MP3DEV
```espero le sirva a alguno y todos se prendan a postear los scripts que usan para hacer las cosas mas faciles.

Ojala termine como STICKY.
\Sergio



```
#!/bin/bash
# ABR/08 SM -- montar.sh --
# monta un archivo .ISO o .NRG
# $1 es el nombre de archivo
# Ej: ./montar.sh /home/videos/peli.ISO

sudo mount -o loop $1 /mnt/tmp
```

Monta una imagen como un pseudo-dispositivo loop. Qué es esto?

Un dispositivo loop es un pseudo dispositivo que hace que un archivo sea accesible como si fuese un block device. Es común ver el uso de estos pseudo dispositivos en imagenes de CDs, DVDs y discos de otros tipos y sirve para que los archivos dentro de estas imágenes sean accesibles

```
#!/bin/bash
# ENE/08 SM
# crea un tunel de un puerto local a uno remoto.
# $1 es el numero de puerto
# $2 es el usuario@host_remoto
# $3 es el puerto de ssh remoto
# Ej: ./tunnel.sh 5432 yo@adonde.vos 5022

ssh -L $1:127.0.0.1:$1 $2 -p $3
```

Crea un tunel local, es util para acceder a servicios bloqueados por un router dentro de tu red. Es decir, creas un tunel usando ssh, el cual pasa por el router sin problemas (siempre que ssh este abierto).

Con esto, podemos crear un tunel del puerto 8080 de nuestra pc, al puerto 80 de un servidor bloqueado, y cada vez que nos conectemos al 8080, en verdad el trafico se dirige al 80 del destino, pasando por el túnel.

Muy util para acceder a archivos de tu casa desde el laburo :P

```
#!/bin/bash
# ABR/08 SM
# reordena los archivos del reproductor mp3 q quedan desordenados al  copiarlos
# requiere el fatsort:
# sudo apt-get install fatsort
# -- NO HACE FALTA EXPULSARLO NI DESMONTARLO ! --
$MP3DEV = /dev/sdb1

sudo umount $MP3DEV
sudo fatsort $MP3DEV
```

Ordena los archivos en /dev/sdb1. No usaria este script, porque por mas que sea util, si tenes al menos dos discos scsi/sata, va a tratar de ordenar de la particion 1 del disco sdb.

---

### Post by Wiredfixer on 2011-02-02
No hay algun script para mover archivos de sus carpetas?

Digamos que tengo varios dir:

/pool/administracion
/pool/dominio
/pool/software

Y la idea es copiar el contenido de cada directorio (son archivos DEB) y pasarlos a su carpeta raiz que es POOL

/pool

La idea es tener todos los archivos en /pool y despues borrar las carpetas.

---

### Post by staar on 2011-02-02
```
cp /pool/*/* /pool

```
bash rules

---

### Post by Wiredfixer on 2011-02-03
> **staar said:**
> ```
cp /pool/*/* /pool

```
bash rules

Ya realize un script mejorado, la idea es ir manteniendo un repositorio para una serie de equipos desktop.

borrar.sh
```

#!/bin/bash
#
# Script para Mover y Borrar archivos DEB
#
mv main/*/* /var/repositorio/pool
rm -r main/
```

Gracias por el Tip :D

---

### Post by granjero on 2012-02-07
Acá va un scriptcito que hice para poder llevar los videos que carga cualquier reproductor flash web a la TV con un pendrive. Una vez que el reproductor flash terminó de cargar el archivo se corre el script y deja el video en el escritorio. Se buscan sugerencias para mejorarlo.

```
#!/bin/bash
clear
echo "Antes de ejecutar este script asegurese que el video se ha cargado por completo. "
echo "Ahora espere unos momentos hasta que se genere la salida del comando: lsof | grep Flash."
echo "La salida tendrá una forma similar a esta:"
echo " "
echo "plugin-co	13348	nombreusuario	16u	REG	8,1 28230017	1443085	/tmp/FlashXXEnkk3Q (deleted)"
echo " "
echo "Los campos que nos interesan son el segundo campo que contiene un número. En el ejemplo anterior | 13348 | y el cuarto campo que es un número seguido de una letra. SOLO nos interesa en número. En el ejemplo anterior es | 16 |"
echo " "
echo "esperando"
lsof | grep Flash
echo " "
echo "tipear el numero del segundo campo y pulsar ENTER"
echo " "
read segundo
echo " "
echo "tipear el numero del cuarto campo sin la letra y pulsar ENTER"
echo " "
read cuarto
echo " "
cp /proc/$segundo/fd/$cuarto ~/Escritorio/video.extension
echo " "
echo "Si ud. ve un cartel como este es porque algún dato fue ingresado erroneamente"
echo "cp: no se puede efectuar stat sobre «/proc/58/fd/15»: Permiso denegado"
echo "De lo contrario en su Escritorio se encuentra un archivo llamado video.extension al cuál deberá cambiar la extensión según corresponda."
```

Salud!

---

### Post by granjero on 2012-03-16
Este es para controlar Rhythmbox por ssh. Me logueo a la máquina, corro el script. tiene que llamarse cr.sh y estar en /bin

[CODE][#!/bin/bash
clear
echo ""
echo ""
echo ""
echo ""
echo P. Play / Pausa
echo N. Siguiente
echo A. Anterior
echo 0. Salir
echo 
echo ingrese valor:

read valor

case "$valor" in

"P" | "p" )
	clear
	echo ""
	echo ""
	echo ""
	echo ""
	echo "PLAY / PAUSE"
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --play-pause --print-playing
	sleep 3
	clear
	cr.sh
;;

"N" | "n" )
	clear
	echo ""
	echo ""
	echo ""
	echo ""
	echo "PROXIMA"
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --next --print-playing
	sleep 2
	clear
	cr.sh
;;

"A" | "a" )
	clear
	echo ""
	echo ""
	echo ""
	echo ""
	echo "ANTERIOR"
	echo "Estaba sonado:"
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	echo "Ahora suena:"
	DISPLAY=:0 rhythmbox-client --previous --print-playing
	sleep 2
	clear
	cr.sh
;;

"0" )
	echo "Gracias por usar este script"
	exit 0
;;

* )
	clear 
	echo ""
	echo ""
	echo ""
	echo ""
	echo "Entrada incorrecta, vuelva a intentar"
	echo "Ingresó '$valor' las posibles opciones son:"
	echo "p / n / a / 0"
	sleep 2
	cr.sh
;;

esac/CODE]

---

