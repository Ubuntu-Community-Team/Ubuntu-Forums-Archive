---
title: "Grub2"
date: 2009-06-22
forum: Software
---

### Post by pablo.s on 2009-06-22
He instalado la alpha2 de 
Karmic Koala hace un rato.
Como ustedes saben, esta 
versión trae por defecto 
GRUB2, que no es igual al 
GRUB al que estamos 
acostumbrados.
Una de las peculiaridades
que tiene, es que cuando
se instala, no toma a los
demas S.O que tengamos
cargados en otras particiones.
En un primer momento
vamos a decir: bueno, edito
menu.lst, le agrego las
entradas y solucionado.
No utiliza más menu.lst:
ahora tiene un archivo que
se llama grub.cfg que tiene
un formato distinto.
Pero a no desesperar, porque
hay una serie de pasos que
podemos hacer para que
añada las entradas de los
S.O. al menú.

Primer paso:
**[COLOR=DarkGreen]sudo apt-get install --reinstall libdebian-installer4[/COLOR]**

(o en caso que esto no
funcione reinstalar el
paquete desde Synaptic)

Segundo paso:

**[COLOR=DarkGreen]sudo os-prober[/COLOR]**

Tercer paso:

**[COLOR=DarkGreen]sudo update-grub[/COLOR]**

---

### Post by juancarlospaco on 2009-06-22
Interesante, muy interesante, que mas hay de lindo...?

---

### Post by gmunioz on 2009-06-23
Sumimasen por la intromisión:


El Grub2 aún es experimental y no esta documentado.

Aún carece de la opción de colocar una contraseña y

tiene problemas con arranques multiboots. 

Y tal como informa Pablo, se ha comenzado a usar en Karmic Koala alfa 2.

La versión 1 de Grub, ahora se denomina Grub Legacy, es la que utiliza la 

mayoría de las distribuciones de GNU/Linux actuales y ya no está siendo 

desarrollada activamente por la comunidad; no se están añadiendo nuevas 

funcionalidades y sólo se están aplicando los parches necesarios para 

mantenerlo al día mientras la versión 2 se estabiliza. 

Los objetivos de esta nueva versión son, entre otros:
   
    * Permitir scripting, condicionales, bucles, variables y funciones.

    * Interfaz gráfica.

    * Extensibilidad mediante carga dinámica de módulos.

    * Portabilidad a distintas arquitecturas.

    * Internacionalización. Soporte para caracteres fuera del conjunto 

ascii, mensajes localizados, etc.

    * Mejor administración de memoria.

    * Marco de trabajo modular, jerárquico y orientado a objetos para 

sistemas de archivo, archivos, dispositivos, unidades, terminales, comandos, 

tablas de partición y cargadores de SO.

    * Instalación multiplataforma.

    * Modo de rescate para casos en los cuales es imposible iniciar.

    * Corregir errores de diseño de la versión anterior de GRUB, que no 

pueden resolverse debido a compatibilidad inversa, por ejemplo el 

numerado de las particiones.

Dado que estoy usando karmic desde la alfa 1, y como reemplazar el 

cargador de arranque es un riesgo innecesario, la actualización mantiene

el Grub Legacy, asi que lo instalé en la pc con karmic y luego en la que

corre jaunty.


Tanto en Jaunty como en Karmic el procedimiento que utilicé fue:

Al iniciar el sistema, presionar escape para entrar al menu del Grub

Seleccionar la opción recuperación (recovery mode)

En el submenu emergente seleccionar netroot

En la consola en que se inicia, como administrador sin contraseña y

con conexión a internet ejecutar:

```
apt-get install grub2 grub2-splashimages desktop-base grub-pc os-prober
```

Terminada la descarga de archivos, y comenzada la instalación de las

aplicaciones aparecerán dos advertencias, a las que se responde OK

Lo que ocurrirá a partir de esto es que:

Se elimina el Grub Legacy del sistema, no del mbr del disco rígido.

Se reemplaza con el Grub2 en el sistema, no en el mbr

Se agrega al comienzo del menu, del Grub Legacy, la opción de iniciar 

con el Grub2 para probarlo en el sistema.


====================================================================
**Advertencia a los usuarios de Jaunty:**

El instalador comete un error, deja las opciones al final del archivo

/boot/grub/menu.lst del Grub Legacy así:

```

## ## End Default Options ##

title		Chainload into GRUB 2
root		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.30-020630-generic
root		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro quiet splash
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Debian GNU/Linux, kernel 2.6.30-020630-generic (recovery mode)
root		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro single
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Este error inutiliza el sistema y no permite iniciar, para evitarlo

ejecutar en la consola, **antes de reiniciar el sistema**:

```
nano /boot/grub/menu.lst
```

Y una vez abierto el archivo, cambiar **root** por **uuid**, para dejarlo asi:

```
## ## End Default Options ##

title		Chainload into GRUB 2
uuid		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.30-020630-generic
uuid		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro quiet splash
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Debian GNU/Linux, kernel 2.6.30-020630-generic (recovery mode)
uuid		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro single
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
uuid		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
uuid		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d2f7f1a8-3863-438d-84cb-24a177377122 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
uuid		d2f7f1a8-3863-438d-84cb-24a177377122
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

A los apresurados que no han leido esta advertencia y hayan reiniciado

sin efectuar la corrección en Jaunty,  les aparecera este error:

```
Error 11: Unrecognized device string
Press any key to continue…
```

La solución consiste en reiniciar

Al aparecer el menu del grub pulsar **e** de edit

dos veces para editar la linea de inicio que se elija y cambiar 

**root por uuid**, en el menu, para entonces si, una vez editada la/s 

linea/s continuar con el inicio del sistema.  

**Fin de la advertencia para usuarios Jaunty**
=====================================================================

Al reiniciar aparece en el menu del Grub Legacy, que aún continua 

instalado en el mbr del disco rígido, una nueva opción:

**Chainload into Grub 2**

Con esta opción se iniciará el Grub2 que ofrecerá todas las opciones 

de inicio del menu original del Grub Legacy

Si el Grub 2 no nos agrada, ejecutando en consola:

```
sudo apt-get purge grub2
sudo apt-get install grub
```

Se lo elimina del sistema y se restaura el Grub legacy, en el sistema

del mbr hasta ahora nunca se removió.

Si nos agrada el Grub2 y queremos dejarlo definitivo hace falta ejecutar, 

tambien en consola la orden:

```
upgrade-from-grub-legacy
```

El Grub 2 tiene sus archivos de configuración en: 

```
/etc/grub.d/

/etc/default/
```

No se debe editar por ningun motivo el archivo /boot/grub/menu.cfg

Para cambiar el tiempo de espera y las opciones de inicio es necesario

editar el archivo 

```
/etc/default/grub
```

Este es su contenido:

```
# This file is sourced by update-grub, and its variables are propagated
# to its children in /etc/grub.d/
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

```
Para agregar otros operativos o kernels o para cambiar las splashimages, es necesario

Crear o modificar archivos dentro de /etc/grub.d/

Por ejemplo, para añadir una entrada de arranque a Windows XP se crea un 

archivo 20_windows_xp en /etc/grub.d con las siguientes líneas

```
 #! /bin/sh -e

    cat << EOF
    menuentry "Microsoft Windows XP Professional" {
    set root=(hd0,1)
    chainloader +1
    }
    EOF

```
Y se le dan permisos de ejecución al script y se agrega la opción al menu

ejecutando en consola las ordenas:

```
sudo chmod +x /etc/grub.d/20_windows_xp

sudo update-grub
```

Si la imagen de fondo de Grub2 no les agrada, se pueden obtener más 

imágenes del paquete grub2-splashimages.

Para cambiar la splash image, es necesario editar el archivo: 

```
etc/grub.d/005_debian_theme
```

Este es su contenido:

```
#!/bin/bash -e

source /usr/lib/grub/update-grub_lib

set_blue_theme()
{
  cat << EOF
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL" = "gfxterm" ] ; then
 <b> for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do</b>
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
EOF
fi

# otherwise, set the traditional Debian blue theme
if ${use_bg} ; then
  set_blue_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_blue_theme
fi
```


Hay que buscar la linea que dice:

```
for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do

```
y cambiar por:

```
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/nuevaimg.{png,tga} ; do
```


Donde nuevaimg es el nombre del archivo imagen elegido de las 

splashimages, instaladas en /usr/share/images/grub.

Una vez guardado el archivo, para que las preferencias se hagan efectivas 

es necesario tal como en el caso anterior, de agregar una opción del 

menu, ejecutar en consola:

```
sudo update-grub
```

Para hacer que el sistema inicie sin mostrar el menu, tal como el Grub 

Legacy se crea un archivo /etc/grub.d/03_hiddenmenu con las siguientes 

líneas:

```
#!/bin/sh
# This is to provide legacy "hiddenmenu" from /etc/default/grub

if [ "x${GRUB_HIDDENMENU}" = "xtrue" ]; then
 cat << EOF
echo -n "Press ESC to enter the menu... "
if sleep --verbose --interruptible ${GRUB_TIMEOUT} ; then
 set timeout=${GRUB_TIMEOUT}
else
 set timeout=-1
fi
EOF
fi
```

Y se le dan permisos de ejecución al script y se agrega la opción al menu

ejecutando en consola las ordenas:

```
sudo chmod +x /etc/grub.d/03_hiddenmenu

sudo update-grub
```

[B][U]Esto es experimental e indocumentado, como tal esta sujeto a cambios y su 

uso puede dejar el sistema inutilizable.[/U][/B]

---

### Post by jose.ibarra on 2009-07-29
Muchas gracias por la ayuda que encontré en este tema, resulta que tenia el error 11, y no encontraba por ninguna parte la solución, y justo me encuentro este tópico en la comunidad.

Gracias :D :D  ):P

---

