---
title: "Error al abrir synaptic"
date: 2010-08-08
forum: Software
---

### Post by maghoxfr on 2010-08-08
Hola,

Intenté instalar BURG según un tutorial de OMG Ubuntu, se ve que hice algo mal, y dado que no soy un experto ahora aarruiné synaptic.

Al abrir synaptic me salta este mensaje

> Se ha producido un error
Se proporcionaron los siguientes detalles:
E: Tipo 'n' desconocido en la línea 1 de lista de fuentes /etc/apt/sources.list.d/bean123ch-burg-lucid.list
E: No se pudo leer la lista de fuentes.
Vaya al diálogo del repositorio para corregir el problema.
E: _cache->open() failed, please report.

Y ahora tengo un círculo rojo (como la señal de contramano) en el área de notificación de el panel superior que al clickearlo me dice:

> No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Tipo 'n' desconocido en la línea 1 de lista de fuentes /etc/apt/sources.list.d/bean123ch-burg-lucid.list, E:No se pudieron leer las listas de fuentes.'

Si alguien sabe cómo solucionar esto le agradezco muchísimo. Me tiene bastante preocupado, y la lección aprendida es: no meter mano ciegamente, y menos por un ajuste estético.

Gracias

---

### Post by atari130xe on 2010-08-08
> **maghoxfr said:**
> Hola,

Intenté instalar BURG según un tutorial de OMG Ubuntu, se ve que hice algo mal, y dado que no soy un experto ahora aarruiné synaptic.

Al abrir synaptic me salta este mensaje



Y ahora tengo un círculo rojo (como la señal de contramano) en el área de notificación de el panel superior que al clickearlo me dice:



Si alguien sabe cómo solucionar esto le agradezco muchísimo. Me tiene bastante preocupado, y la lección aprendida es: no meter mano ciegamente, y menos por un ajuste estético.

Gracias

Hola, intentá borrar ese archivo de tu sources list (tenés que navegar hasta llegar a ese directorio /etc/apt/sources.list.d/[COLOR="Red"]bean123ch-burg-lucid.list[/COLOR]) 
 y luego hacé

```
sudo apt-get update
``` a ver si se soluciona el problema con eso.

---

### Post by maghoxfr on 2010-08-08
Me imagino que debería solucionarse, pero hay otro problema. No posteé ayer pero de madrugada intenté borrar el archivo .list y el .save pero no me deja, al menos de la manera simple (supr o arrastrar a la papelera). Me dice que no se pueden borrar, y aunque me da la opción eliminar completamente, no hace nada.

El repositorio de burg ya lo eliminé de la lista de "otro software", pero no puedo eliminar los archivos .save y .list que aparentemente son los causantes del problema.

Hice esto en la terminal pero
> sudo rm -i bean123ch-burg-lucid.list
[sudo] password for general: 
rm: no se puede borrar «bean123ch-burg-lucid.list»: No existe el archivo o directorio

¿cómo podría borrarlos desde la terminal?

Te paso mi sources.list por si ayuda en algo.

> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

Si hago sudo apt-get update, me salta lo mismo que en synaptic
> $ sudo apt-get update
E: Tipo 'n' desconocido en la línea 1 de lista de fuentes /etc/apt/sources.list.d/bean123ch-burg-lucid.list

Por último, si abro el archivo bean123ch-burg-lucid.list en gedit, su contenido es nada más que una "n" en la primera línea.

Muchas gracias

---

### Post by guillermolisi on 2010-08-08
Mostra el contenido del directorio /etc/apt/sources.list.d y, segun lo que aparezca, vemos si hay algo para eliminar (lo mas probable es que el repo en cuestion se encuentre ahi ya que tu sources.list esta perfecto.

---

### Post by maghoxfr on 2010-08-08
Hola, este es el contenido de sources.list.d


> /etc/apt/sources.list.d$ ls
abogani-ppa-lucid.list          invada-ppa-lucid.list
abogani-ppa-lucid.list.save     invada-ppa-lucid.list.save
bean123ch-burg-lucid.list       nvidia-vdpau-ppa-lucid.list
bean123ch-burg-lucid.list.save  nvidia-vdpau-ppa-lucid.list.save
bisigi-ppa-lucid.list           philip5-extra-lucid.list
bisigi-ppa-lucid.list.save      philip5-extra-lucid.list.save
falk-t-j-lucid-lucid.list       ubuntu-x-swat-x-updates-lucid.list
falk-t-j-lucid-lucid.list.save  ubuntu-x-swat-x-updates-lucid.list.save

los bean123... son los que no puedo borrar.

---

### Post by guillermolisi on 2010-08-08
Tenes mas de una forma de eliminar los repos que no queres usar o te estan trayendo problemas.

Una es a traves de Origenes de Software o Synaptic mismo (que te lleva a Origenes de Software de todas formas). Ahi destildas los repos que no queres usar mas.

La otra es "a mano", como creo estas intentado hacer.

Mi sugerencia es usar Origenes de Software/Synaptic, desmarcar todos los repos que no sean originales de la distribucion (es decir, los PPA que figuran en la salida que mostraste) y luego agregas de a uno hasta que vuelvas a tener errores, asi sabras cual es o cuales son, en definitiva, los conflictivos (mas alla del mensaje de error que recibis).

---

### Post by maghoxfr on 2010-08-08
LO SOLUCIONÉ!!! Era mi error ya que al intentar eliminar los archivos burg123ch... no lo hacia con derechos de root

corrí sudo su, después fui al directorio, y rm [archivo] para borrarlo. Listo. Ahora me entró a synaptic sin problema.

Muchas gracias por la ayuda.

---

