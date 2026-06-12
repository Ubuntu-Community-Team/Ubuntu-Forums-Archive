---
title: "problemas con update"
date: 2015-06-16
forum: Software
---

### Post by zcorpt on 2015-06-16
Hola! a todos!
Tengo un problema al ejecutar el comando $ sudo apt-get update ya que me muestra lo siguiente:

```

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/trusty/Release  No se pudo encontrar la entrada esperada «restricted/source/Sources» en el archivo Release (entrada incorrecta en sources.list o archivo mal formado)

E: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar

```

este es mi soure.list

```

# deb cdrom:[elementary OS 0.3 _Freya_ - Stable amd64 (20150411)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mx.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://mx.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty universe
deb-src http://archive.ubuntu.com/ubuntu trusty universe
deb http://mx.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://mx.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mx.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.ubuntu.com/ubuntu trusty-updates restricted universe multiverse main
deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse

```

Y no se como solucionarlo, cabe mencionar que soy nuevo en Linux y no se mucho, y la distro que estoy ocupando es Elementary OS Freya.
De antemano muchas gracias por la ayuda que me brinden

---

### Post by euzkoarima on 2015-06-22
Al menos yo no veo nada raro en tu sources.list, parece más bien un problema de conexión.
Como hace unos días que escribiste: se arregló "solo" (entonces era problema de conexión no más).
Avisá si seguis con el problema.

Saludos,
Eduardo

---

