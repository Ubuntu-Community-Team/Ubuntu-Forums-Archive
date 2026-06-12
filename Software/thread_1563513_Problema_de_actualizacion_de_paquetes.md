---
title: "Problema de actualizacion de paquetes"
date: 2010-08-29
forum: Software
---

### Post by dam1977 on 2010-08-29
Estoy usando en una PC Core 2 Duo con Ubuntu 10.04 y me asombra este mensaje que aparece cuando abro un icono rojo en la barra superior ....

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Problem parsing dependency Replaces, E:Ocurrió un error mientras se procesaba language-pack-kde-sv-base (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

No se cómo solucionarlo. No tengo idea que tan grave será. Gracias.

---

### Post by guillermolisi on 2010-08-29
Podrias mostrar el contenido de /etc/apt-get/sources-list y /etc/apt-get/sources.d.list ?

Que estas usando basado en KDE ?

---

### Post by dam1977 on 2010-08-29
Bueno ahi va el contenido del archivo sources.list
Un poco largo nomás!!

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by dam1977 on 2010-08-29
Ah! no estoy usando KDE para nada, solo Gnome.

---

### Post by guillermolisi on 2010-08-29
La lista de repositorios que mostras no tiene nada raro.

Solo a titulo experimental y considerando que decis no usar ninguna aplicacion basada en KDE, probaria de cambiar el origen de los mirrors. En lugar de utilizar los de Argentina probaria con los de Brasil, mas especificamente con los de red globo, a ver que resultado genera.

Ahora, si tenes alguna aplicacion basada en KDE, la cosa cambia pero habria que saber cual es como para afinar el diagnostico.

---

### Post by dam1977 on 2010-08-30
Bueno, cambié la ubicación del servidor para descargar actualizaciones, puese el que me indicaste (Brasil, globo), descargó e instaló actualizaciones, y desapareció el mensaje de error.  Muchas gracias de nuevo!

---

