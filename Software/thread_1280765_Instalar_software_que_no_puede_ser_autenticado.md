---
title: "Instalar software que no puede ser autenticado"
date: 2009-10-02
forum: Software
---

### Post by MPx1 on 2009-10-02
Hola gente, hoy se me abrió la ventana de actualizacion y en la ventana para aplicar los cambios dice: 

AVISO

Esta a punto de instalar software que **no puede ser autenticado**

[IMG]http://img515.imageshack.us/img515/9890/64545320.png[/IMG]

por supuesto no apliqué nada, uds. saben a que se debe esto..?

---

### Post by Cajuma on 2009-10-02
Hasta donde se, es parte de la bateria de actualizaciones pre Upgrade a KK
estos ultimos días actualice varias veces y las aplicaciones que veo en tu screen
yo ya las tengo instaladas y todo bién...
Sin embargo a mi no me notifico lo mismo que a vos, puede tener que ver con los 
repos que tenes habilitados.
Saludos....

---

### Post by guillermolisi on 2009-10-02
Por favor, postea el contenido de /etc/apt/sources.list y de /etc/apt/sources.list.d

El primero es un archivo y el segundo es una directorio.

Normalmente ese tipo de mensajes aparecen cuando falla el reconocimiento de la clave de seguridad, el certificado digital, entre tu PC y el repositorio, ya sea por una cuestion de comunicacion, porque cambio la clave (cosa muy rara) o porque no importaste el certificado/clave del repositorio en tu maquina.

---

### Post by santiagoward2000 on 2009-10-02
> **guillermolisi said:**
> Normalmente ese tipo de mensajes aparecen cuando falla el reconocimiento de la clave de seguridad, el certificado digital, entre tu PC y el repositorio, ya sea por una cuestion de comunicacion, porque cambio la clave (cosa muy rara) o porque no importaste el certificado/clave del repositorio en tu maquina.

Hola!
Si no agregaste ningún repositorio últimamente, lo más probable es que sea una cuestión de comunicación. La Beta de Karmic salió ayer, y hoy los servers deben estar sobrecargados. Yo hoy todavía no pude revisar si hay actualizaciones.
Saludos!

---

### Post by MPx1 on 2009-10-02
el primero:


# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main
# deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) jaunty/

y en /etc/apt/sources.list.d no hay archivos y si hay archivos ocultos no se como visualizarlos..

esta es la lista para ser actualizado:

apport (versión1.0-0ubuntu5.2) será actualizado a la versión 1.0-0ubuntu5.4
apport-gtk (versión1.0-0ubuntu5.2) será actualizado a la versión 1.0-0ubuntu5.4
dbconfig-common (versión1.8.40) será actualizado a la versión 1.8.40ubuntu1
kopete (versión4:4.2.2-0ubuntu2) será actualizado a la versión 4:4.2.2-0ubuntu2.1
libpam-smbpass (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2
libsmbclient (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2
libwbclient0 (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2
linux-headers-2.6.28-15 (versión2.6.28-15.49) será actualizado a la versión 2.6.28-15.52
linux-headers-2.6.28-15-generic (versión2.6.28-15.49) será actualizado a la versión 2.6.28-15.52
linux-image-2.6.28-15-generic (versión2.6.28-15.49) será actualizado a la versión 2.6.28-15.52
linux-libc-dev (versión2.6.28-15.49) será actualizado a la versión 2.6.28-15.52
openoffice.org-base-core (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-calc (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-common (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-core (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-draw (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-emailmerge (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-gnome (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-gtk (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-impress (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-math (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-style-human (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
openoffice.org-writer (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
python-apport (versión1.0-0ubuntu5.2) será actualizado a la versión 1.0-0ubuntu5.4
python-problem-report (versión1.0-0ubuntu5.2) será actualizado a la versión 1.0-0ubuntu5.4
python-uno (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
samba (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2
samba-common (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2
smbclient (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2
ttf-opensymbol (versión1:3.0.1-9ubuntu3) será actualizado a la versión 1:3.0.1-9ubuntu3.1
uno-libs3 (versión1.4.1+OOo3.0.1-9ubuntu3) será actualizado a la versión 1.4.1+OOo3.0.1-9ubuntu3.1
ure (versión1.4.1+OOo3.0.1-9ubuntu3) será actualizado a la versión 1.4.1+OOo3.0.1-9ubuntu3.1
winbind (versión2:3.3.2-1ubuntu3.1) será actualizado a la versión 2:3.3.2-1ubuntu3.2

---

### Post by guillermolisi on 2009-10-02
No veo nada fuera de lugar. Es mas, esta muy bien mantenido, sin cosas raras (solo el repo para el aMSN).

En el directorio sources.list.d no deberia haber archivos ni directorios ocultos, asi que si no ves nada es porque no hay nada.

Yo probaria de actualizar en un horario no pico, madrugada por ejemplo, porque los mismos paquetes los actualice hoy y tarde como si tuviera dial up, tanto en casa como en mi oficina (2MbFibertel, 2Mb Global Crossing) asi que el problema esta del lado de los servers en mi opinion.

Te animas a intentarlo en un horario no central a ver que pasa y nos comentas ?

---

### Post by MPx1 on 2009-10-03
Bueno, anoche probe actualizar [a las 2:30 para ser mas preciso] no me apareció la ventana que ven en mi primer post.. y parece ser que todo funciona bien.. todavia me queda la duda de por qué aparació esa ventana.. pero bue,, gracias a todos los que comentaron..

---

### Post by guillermolisi on 2009-10-03
> **MPx1 said:**
> Bueno, anoche probe actualizar [a las 2:30 para ser mas preciso] no me apareció la ventana que ven en mi primer post.. y parece ser que todo funciona bien.. todavia me queda la duda de por qué aparació esa ventana.. pero bue,, gracias a todos los que comentaron..
Si anoche salio todo bien, entonces eso verifica que no pudo obtener la otra parte de las claves de autenticacion por problemas en el enlace y/o respuesta del server que tiene esos repositorios.

Tema resuelto.

---

