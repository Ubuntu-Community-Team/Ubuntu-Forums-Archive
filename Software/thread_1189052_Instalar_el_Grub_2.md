---
title: "Instalar el Grub 2"
date: 2009-06-16
forum: Software
---

### Post by gmunioz on 2009-06-16
Soy usuario de Karmic en mis ordenadores de prueba y de Jaunty en el de

trabajo.

Ante el aviso, tras la salida del alfa 2 de karmic, del uso del Grub2,

que por el riesgo inherente solo se activaria en nuevas instalaciones y

no se actualizaría, decidí investigar al respecto, obteniendo muy poca

información, a la que agrego a mis experiencias, experiencias que me han 

permitido utilizar actualmente en todos mis ordenadores como cargador de 

arranque al Grub2.

Introducción:

La antigua versión del Grub, ahora se denomina Grub Legacy, es la que 

se utiliza por defecto en la mayoría de las distribuciones de Gnu/Linux 

actuales y  salvo el parche para el sistema de archivos ext4, 

prácticamente no está siendo desarrollada activamente por la comunidad; 

ni se le están añadiendo nuevas funcionalidades, es decir que solo se 

están aplicando los parches necesarios para mantenerlo al día mientras 

la versión nueva se estabiliza. 

Los objetivos de esta nueva versión son, entre otros:
   
    * Permitir scripting, condicionales, bucles, variables y funciones.

    * Interfaz gráfica.

    * Extensibilidad mediante carga dinámica de módulos.

    * Portabilidad a distintas arquitecturas.

    * Internacionalización. Soporte para caracteres fuera del conjunto 

ascii, mensajes localizados, etc.

    * Mejor administración de memoria.

    * Marco de trabajo modular, jerárquico y orientado a objetos para 

sistemas de archivo, archivos, dispositivos, unidades, terminales, 

comandos, tablas de partición y cargadores de SO.

    * Instalación multiplataforma.

    * Modo de rescate para casos en los cuales es imposible iniciar.

    * Corregir errores de diseño de la versión anterior de GRUB, que no 

pueden resolverse debido a compatibilidad inversa, por ejemplo el 

numerado de las particiones.

Tanto en Karmic como en Jaunty el procedimiento que utilicé fue:

Al iniciar el sistema, presionar escape para entrar al menu del Grub

Seleccionar recuperación

En el submenu emergente seleccionar netroot

En la consola en que se inicia ejecutar:

```
apt-get install grub2 grub2-splashimages desktop-base grub-pc os-prober
```

Terminada la descarga de archivos, y comenzada la instalación de las

aplicaciones apareceran dos advertencias, a las que se responde OK

Lo que ocurrió fue que:

Se eliminó el Grub del sistema, no del mbr, se reemplazó con el Grub2

se agregò al comienzo del menu la opción de optar por el Grub2 para 

prueba en sistema.

Usuarios de jaunty:

El instalador comete un error, deja las opciones al final del archivo

/boot/grub/menu.lst así:

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

Esto es un error que inutiliza el sistema y no permite iniciar, para 

evitarlo ejecutar en la consola, antes de reiniciar el sistema:

```
nano /boot/grub/menu.lst
```

Y una vez abierto el archivo, cambiar root por uuid, para dejarlo asi:

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

Si no se efectua la corrección en Jaunty, aparecera este error:

```

Error 11: Unrecognized device string
Press any key to continue…

```

En este caso al reiniciar, al aparecer el menu del grub pulsar e de edit

dos veces para editar la linea de booteo que se elija y cambiar 

root por uuid, para entonces, una vez editada la linea continuar con el

inicio del sistema.  

Al reiniciar aparece en el menu del Grub, que aún esta instalado en el mbr

una nueva opción  **Chainload into Grub 2**

Con esta opción se iniciará el Grub2 que ofrecerá las opciones de

inicio del menu original completo

Si el Grub 2 no nos agrada, ejecutando en consola:

```

sudo apt-get purge grub2

```

Lo eliminamos del sistema.

Si nos agrada, para dejarlo definitivo hace falta ejecutar, tambien en consola:

```

upgrade-from-grub-legacy

```

Si bien aun no esta documentado, el Grub 2 tiene sus archivos de 

configuración en los directorios: 

```
/etc/grub.d/

/etc/default/
```


Para cambiar el tiempo de espera y las opciones de inicio es necesario

editar el archivo /etc/default/grub

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

Para agregar otros operativos o kernels o para cambiar las splashimages, 

es necesario crear o modificar archivos dentro de /etc/grub.d/

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

Se le dan permisos de ejecución al script y se agrega la opción al menu

ejecutando en consola las ordenes:


```
sudo chmod +x /etc/grub.d/20_windows_xp

sudo update-grub

```

Si la imagen de fondo de Grub2 no es del agrado, se pueden obtener más 

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
  for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do
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

y la cambiamos por:

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

---

### Post by rodrigovb-cl on 2009-06-16
Gracias por el tutorial, en cualquier caso no puedo dejar de decir "niños, no lo intenten en sus casas".

Si eres un usuario novato o tienes un equipo productivo, mejor esperar a que grub 2 venga de serie, no vaya a ser cosa que algo no vaya como queremos ;)

---

### Post by gmunioz on 2009-06-16
Hola Rodrigo:

De nada.
```
no puedo dejar de decir "niños, no lo intenten en sus casas".
```

Realmente esto es a título absolutamente experimental.

Fuera de ello, no le veo el caso de instalar el Grub2, y no me parece

prudente instalarlo solo para tener "Un Grub lindo y colorido", motivación

casi exclusiva según lo registrado en la red.

---

### Post by rodrigovb-cl on 2009-06-16
> **gmunioz said:**
> Hola Rodrigo:

De nada.
```
no puedo dejar de decir "niños, no lo intenten en sus casas".
```

Realmente esto es a título absolutamente experimental.

Fuera de ello, no le veo el caso de instalar el Grub2, y no me parece

prudente instalarlo solo para tener "Un Grub lindo y colorido", motivación

casi exclusiva según lo registrado en la red.

100% de acuerdo, pero sabemos que a muchos les gusta los "dulces", por lo que mi experiencia dice que hay que avisar que si quieres probar esto debes **hacerlo con responsabilidad**.

---

