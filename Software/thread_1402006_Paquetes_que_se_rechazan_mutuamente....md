---
title: "Paquetes que se rechazan mutuamente..."
date: 2010-02-08
forum: Software
---

### Post by aledruetta on 2010-02-08
Hola Comunidad!

Creo que fue a partir de agregar los repositorios de Medibuntu a Karmic que en alguna actualización empezó este problema.

Cuando hago sudo apt-get dist-upgrade sale esto:
```

Los siguientes paquetes se ELIMINARÁN:
  devede dvd95 ffmpeg libpostproc-extra-51
Se instalarán los siguientes paquetes NUEVOS:
  libopencore-amrnb0 libopencore-amrwb0 libpostproc51
Los siguientes paquetes se han retenido:
  libavdevice52 libavfilter0
```
El problema es que no quiero que me elimine Devede y ffmpeg.

¿Qué se puede hacer al respecto?

---

### Post by guillermolisi on 2010-02-08
Podrias mostrarnos el contenido de /etc/apt/sources.list y de /etc/apt/sources.list.d/*.list ?

---

### Post by aledruetta on 2010-02-09
> **guillermolisi said:**
> Podrias mostrarnos el contenido de /etc/apt/sources.list y de /etc/apt/sources.list.d/*.list ?

Sí, claro, ahí van:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://br.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://br.archive.ubuntu.com/ubuntu/ karmic universe
deb http://br.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://br.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://br.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```

```
deb http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu karmic main #Nautilus Elementary
deb http://ppa.launchpad.net/docky-core/ppa/ubuntu karmic main #Docky
deb http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu karmic main #Elementary Desktop PPA
deb http://ppa.launchpad.net/elementaryart/ppa/ubuntu karmic main #PPA for Elementary Art
deb http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu karmic main #GDM2Setup
deb http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu karmic main #Gloobus Preview
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main #Ubuntu Tweak Stable Source
deb http://download.virtualbox.org/virtualbox/debian karmic non-free #VirtualBox Offical Source

```

Como verán, saqué los repositorios de Medibuntu y ahora no tengo problemas, están instalados Devede, Pitivi, ffmpeg, Dvd95 y Dvd::rip, que daban problemas. También quité los ubuntu-restricted-extras.

Hasta el momento, todo bien, salvo que no puedo activar Medibuntu ni los ubuntu-restricted-extras, porque ahí es donde comienzan los problemas con los paquetes que mencioné.

---

### Post by guillermolisi on 2010-02-09
La idea era ver la referencia a los repos de Medibuntu en busca de algun posible error.
Yo los estoy usando y son estos en /etc/apt/sources.list.d:
```
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
```
con el siguiente contenido en medibuntu.list:
```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
# deb-src http://packages.medibuntu.org/ karmic free non-free #Medibuntu (source) - Ubuntu 9.10 "karmic koala"
```

---

### Post by juancarlospaco on 2010-02-09
Que los desinstale, despues podrias volver a instalarlos creo...

---

### Post by aledruetta on 2010-02-09
> **juancarlospaco said:**
> Que los desinstale, despues podrias volver a instalarlos creo...

Sí, intenté hacer eso antes de quitar los repositorios de Medibuntu y los ubuntu-restricted-extra, pero después cuando los quería instalar (me refiero a las aplicaciones) el problema volvía a empezar: para instalarlos pedía desinstalar paquetes, y cuando hacía una actualización (upgrade) me decía que había paquetes retenidos, y después, cuando hacia una dist-upgrade, me pedía desinstalar esas aplicaciones.

¿Alguien sabe si hay alguna incompatibilidad entre los paquetes multimedia de Medibuntu y ubuntu-restricted-extras? Porque ahora que no los tengo a ninguno de los dos, aparentemente, no hay conflicto.
¿será eso?

---

### Post by guillermolisi on 2010-02-09
> **aledruetta said:**
> ¿Alguien sabe si hay alguna incompatibilidad entre los paquetes multimedia de Medibuntu y ubuntu-restricted-extras? Porque ahora que no los tengo a ninguno de los dos, aparentemente, no hay conflicto.
¿será eso?
Si utilizas Aptitude o Synaptic al marcar paquetes te indicaran si hay conflicto entre ellos para que vos resuelvas con cual te quedas.

---

