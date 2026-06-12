---
title: "[SOLVED] Paquete ipppd - error 127 -"
date: 2009-08-17
forum: Software
---

### Post by RENGOdeDIA on 2009-08-17
Hola a todos, me sale este error cada vez que instalo algo nuevo, no genera problema alguno ya que la aplicación que instalo funciona bien pero siempre me aparece el mismo error.
Busque en el foro y googlee un poco pero me trabe y necesito una mano por que no se por donde empezar. 
Muchas gracias
Slds

---

### Post by guillermolisi on 2009-08-17
Esto resulta usando apt-get o Synaptic ?

Si es asi, revisaste el contenido de /etc/apt/sources.list y /etc/apt/sources.list.d ?

---

### Post by RENGOdeDIA on 2009-08-17
Si pasa con ambos, revise el /etc/apt/sources.list y no encontre nada raro pero aclaro que soy algo nuevo en esto, que es lo que tengo que mirar especificamente?
/etc/apt/sources.list.d es una carpeta y esta vacía, acá puede haber algo mal?
gracias por responder

---

### Post by guillermolisi on 2009-08-17
No, puede estar vacio el sources.list.d. Solo lo mencione por las dudas porque hay paquetes que instalas que guardan informacion ahi.

Mostranos el contenido de /etc/apt/sources.list a ver si encontramos algo raro y te lo marcamos.

De paso, que version de Ubuntu estas usando ? JJ u otra ?

---

### Post by Fak89 on 2009-08-17
Con todo tipo de paquetes?
Aca tenes un post donde pasaba lo mismo y fue solucionado, fijate si te sirve..
[http://ubuntuforums.org/showthread.php?p=7494054#post7494054](http://ubuntuforums.org/showthread.php?p=7494054#post7494054)

---

### Post by RENGOdeDIA on 2009-08-17
Uso Ubuntu 9.04 con gnome

este es el source.list
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

# deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main #avant-window-navigator
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main #compiz-fusion
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main #gnome-globalmenu
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main #gnome-do
deb http://dl.google.com/linux/deb/ stable non-free #google
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main #ubuntu-tweak
deb http://wine.budgetdedicated.com/apt jaunty main #wine
deb http://packages.medibuntu.org/ jaunty free non-free #medibuntu
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #Ubuntu X
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #OpenOffice.org
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu jaunty main #Gnome Colors
deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu jaunty main #Transmission (Stable Version)
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main #Reproductor multimedia VLC
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

```

a modo de consulta:
que función cumple el paquete ipppd? sabes que significa ese código de eror?


Slds

---

### Post by pablo.s on 2009-08-18
[Acá explican]("http://hatteras.wordpress.com/2008/07/23/error-127-en-synaptic-solucionado/") cómo solucionar
el error 127 de apt.

---

### Post by RENGOdeDIA on 2009-08-18
> **pablo.s said:**
> [Acá explican]("http://hatteras.wordpress.com/2008/07/23/error-127-en-synaptic-solucionado/") cómo solucionar
el error 127 de apt.
Acá explican como solucionarlo cuando el problema es desinstalando un paquete, yo no tengo errores cuando desinstalo, sino cuando instalo. La solución es la misma?


Recien termina de actualizar el sistema y me apareció 
```

E: ipppd: el subproceso post-installation script devolvió el código de salida de error 127

```

---

### Post by Fak89 on 2009-08-18
Intentaste con esto..?

> **Fak89 said:**
> Con todo tipo de paquetes?
Aca tenes un post donde pasaba lo mismo y fue solucionado, fijate si te sirve..
[http://ubuntuforums.org/showthread.php?p=7494054#post7494054](http://ubuntuforums.org/showthread.php?p=7494054#post7494054)

---

### Post by pablo.s on 2009-08-18
> **RENGOdeDIA said:**
> Acá explican como solucionarlo cuando el problema es desinstalando un paquete, yo no tengo errores cuando desinstalo, sino cuando instalo. La solución es la misma?

Si, porque el conflicto está con
el paquete en particular.

---

### Post by RENGOdeDIA on 2009-08-18
Bueno, haciendo lo que recomienda pablo.s pude desinstalar el paquete ipppd y por ahora no marcó mas error. Cualquier novedad comento...

---

