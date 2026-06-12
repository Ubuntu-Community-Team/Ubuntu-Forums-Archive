---
title: "Wallpaper changer"
date: 2008-12-14
forum: The Cafe
---

### Post by tuxsheadache on 2008-12-14
Does anyone know of a program that could change my desktop wallpaper every few minutes from a selection in a folder?
I'm not sure if said program exists, but would by mightily awesome.

EDIT: found: [http://ubuntuforums.org/showthread.php?t=888746&highlight=wallpaper](http://ubuntuforums.org/showthread.php?t=888746&highlight=wallpaper)
*headdesk* Forgot to search before posting xD

---

### Post by lukjad on 2008-12-14
Only for 8.04, and you're using 8.10. The GNOME team changed it so that it can't be done with the program that I know, at least not yet. Keep an eye on the thread though, the answer may yet come.


[http://ubuntuforums.org/showthread.php?t=888746](http://ubuntuforums.org/showthread.php?t=888746)

---

### Post by brunovecchi on 2008-12-14
This script changes your wallpaper randomly from a folder.
You can schedule a cron job to execute it every couple of minutes if you want to; I set it up to get executed at the beginning of each session.
If the picture name starts with the word "tile", it sets the wallpaper in tile mode. Otherwise, it stretches the picture to fit the screen. Pictures must be in *.jpg.
Before running it, edit line 5 with your pics folder path.

Comments are in spanish, sorry.

```

#!/bin/bash
# almacenamos en una variable la carpeta donde residen las imagenes. en mi
# caso /home/jose, cambia este valor por el que quieras usar en tu caso.

picsfolder="/home/bruno/Imagenes/Wallpapers/"

# Nos movemos al directorio donde estan las imagenes
cd $picsfolder

# Creamos un array con todos los ficheros de ese directorio que tengan
# extension .jpg Un array es un concepto de programacion, podriamos
# considerarlo como una lista de valores a los que podemos acceder por un
# indice que es su posicion en esa lista. Por ejemplo, podriamos tener un
# array llamado "dias" que almacenara los siguientes valores: lunes,
# martes, miercoles, jueves y viernes. dias = [ lunes, martes,
# miercoles, jueves, viernes]. Con ese array podriamos referenciar a un
# elemento del mismo a partir de su posicion. Ejemplo: dias[0] es lunes,
# dias[2] es miercoles.  En este ejemplo lo que hacemos es crear un array
# con los nombres de todos los ficheros .jpg del directorio
files=( *.jpg )

# Recuperamos el numero de ficheros, N almacenara el numero de elementos del
# array
N=${#files[@]}

# Seleccionamos "aleatoriamente" un valor de esos N ficheros
((N=RANDOM%N))

# Con ese valor aleatorio (indice del array) accedemos al array y
# recuperamos el nombre del fichero
randomfile=${files[$N]}
echo $randomfile

# Si el nombre de archivo comienza con "tile", setear la opción
# correspondiente

A=`echo $randomfile | sed 's/^\(\w\{4\}\).*/\1/'`
if [ "$A" = "tile" ]; then
    OPTION="wallpaper"
    echo $OPTION
else
    OPTION="streched"
    echo $OPTION
fi


# Y una vez recuperado el nombre de ese fichero llamamos a gconftool para
# fijar ese fichero como fondo de escritorio
gconftool-2 -t str --set /desktop/gnome/background/picture_filename $picsfolder$randomfile

# cambiamos tambien las propiedades de la imagen que se muestra
gconftool-2 -t str --set /desktop/gnome/background/picture_options $OPTION #posibles valores "none", "wallpaper" (mosaico), "centered" "scaled", "stretched"

```

---

### Post by MikeTheC on 2008-12-14
Wallpaper Tray works great for me. It can be installed via either apt-get or Synaptic Package Manager. The package title is [font="courier new"]wallpaper-tray[/font].

---

