---
title: "problemas luego de actualizar"
date: 2009-07-01
forum: Software
---

### Post by goldenfox on 2009-07-01
bueno hace poco instale muchas actualizaciones y entre ellas benia un nuevo kernel
pues luego de actualizar y de quitar unos programas me encuentro que este kernel nuevo no me funciona 
y el otro problema es que se produjo un error en el programa de actualizaciones y en cualquier programa que use para instalar o quitar soft

aquí el error que me tira el update-manager

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E: Problem parsing dependency Replaces, E: Ocurrió un error mientras se procesaba libwpd8c2a (NewVersion1), E: Problem with MergeList /var/lib/dpkg/status, E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

---

### Post by pablo.s on 2009-07-01
Verifica si hace lo mismo
luego de hacer

```
sudo apt-get update
```

---

### Post by goldenfox on 2009-07-01
sigue asiendo lo mismos :(

---

### Post by pablo.s on 2009-07-01
A ver, probá con

```
sudo apt-get install libwpd8c2a
```

---

### Post by goldenfox on 2009-07-01
```
Leyendo lista de paquetes... ¡Error!
E: Problem parsing dependency Replaces
E: Ocurrió un error mientras se procesaba libwpd8c2a (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.

```

---

### Post by pablo.s on 2009-07-01
Podés abrir Synaptic?

Podés reparar paquetes rotos?

Ahi el paquete que te señalé
está roto y provoca el error.
Sino abre Synaptic probá con
esto: 

```
sudo apt-get remove libwpd8c2a
```

---

### Post by guillermolisi on 2009-07-01
> bueno hace poco instale muchas actualizaciones y entre ellas benia un nuevo kernel
pues luego de actualizar y **de quitar unos programas**
Que programas quitaste ? Como ?

---

### Post by goldenfox on 2009-07-02
quite el cairo composite manager por completo y lo instales denuevo es que daba unos problemas raro luego de actualisar por el nuevo driber para placas intel :S

pd si inicio el snaptic me salta el error ese y al darle a ok se cierra

---

### Post by guillermolisi on 2009-07-02
> **goldenfox said:**
> quite el cairo composite manager por completo y lo instales denuevo es que daba unos problemas raro luego de actualisar por el nuevo driber para placas intel :S

pd si inicio el snaptic me salta el error ese y al darle a ok se cierra
Te fijaste que otros paquetes serian desinstalados cuando removiste cairo composite ?

---

### Post by goldenfox on 2009-07-03
no no quito nada mas solo el cairo composite manager y el de los agregados :S

---

### Post by guillermolisi on 2009-07-03
> **goldenfox said:**
> no no quito nada mas solo el cairo composite manager y el de los agregados :S
Podrias mostrar el contenido del archivo /etc/apt/sources.list ?

---

### Post by goldenfox on 2009-07-07
perdon por no pasarme es que estube con otras cosas

aca esta el contenido de mi source.list

```
 deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu intrepid main
deb http://security.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe
# deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu intrepid main

deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb http://mirrors.kernel.org/ubuntu/pool/universe/k/kdebindings/python-dcop_3.5.9-0ubuntu1_i386.deb hardy main universe

deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# cairo composite manager:
deb http://ppa.launchpad.net/gandalfn/ubuntu intrepid main
# EMESENE CRAIZY 
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
# TOR Y LOS PROGRAMAS NECESARIOS PARA QUE CORRA
deb http://mirror.noreply.org/pub/tor jaunty main
#deb-src http://mirror.noreply.org/pub/tor jaunty main
##Themes du ZgegBlog
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu intrepid main
```

espero poder arreglar esto porque es desesperante el no poder instalar un .deb de ningun lado :S

---

### Post by guillermolisi on 2009-07-07
> **goldenfox said:**
> perdon por no pasarme es que estube con otras cosas

aca esta el contenido de mi source.list

```
 deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu intrepid main
deb http://security.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe
# deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu intrepid main

deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb http://mirrors.kernel.org/ubuntu/pool/universe/k/kdebindings/python-dcop_3.5.9-0ubuntu1_i386.deb hardy main universe

deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# cairo composite manager:
deb http://ppa.launchpad.net/gandalfn/ubuntu intrepid main
# EMESENE CRAIZY 
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
# TOR Y LOS PROGRAMAS NECESARIOS PARA QUE CORRA
deb http://mirror.noreply.org/pub/tor jaunty main
#deb-src http://mirror.noreply.org/pub/tor jaunty main
##Themes du ZgegBlog
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu intrepid main
```espero poder arreglar esto porque es desesperante el no poder instalar un .deb de ningun lado :S
Si no entendi mal, estas usando JJ, por lo tanto probaria una actualizacion para verificar que la cosa se normalizo comentando las siguientes lineas que corresponden a repositorios fuera de version (algunas son de HH y otras de II):

```
deb http://mirrors.kernel.org/ubuntu/pool/universe/k/kdebindings/python-dcop_3.5.9-0ubuntu1_i386.deb **hardy** main universe
deb http://ppa.launchpad.net/gandalfn/ubuntu **intrepid** main
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu **intrepid** main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu **intrepid** main
```

Una vez comentadas (con el signo # en la primer columna/posicion de cada linea) proba de actualizar el cache de repositorios de la maquina y comenta como te fue.

---

### Post by goldenfox on 2009-07-09
bien lo ise y sigue con el error 

aca les dejo contextualmente lo que sale del cartel del abiso de error

"Error: Abriendo la caché (E: Problem parsing dependency Replaces, E: Error ocurred while processing libwpd8c2a (new vercion1), E: Problem with mergerlist /var/lib/dpkg/status, E: The package list or status file could not be parsed or opened.)""normalmente, esto significa que ha instalado paquetes cuyas dependencias no se han podido sastifacer"

---

### Post by goldenfox on 2009-07-13
ninguna ayuda?
es que esto se empieza a poner grabe necesito hacer cosas y no puedo instalar nada :S

---

### Post by Hei Ku on 2009-07-13
el error ese te aparece despues de hacer qué exactamente?

---

### Post by goldenfox on 2009-07-13
apares luego del inicio del sistema porque tenia actualizaciones pendientes
cada ves que abro un programa que tenga que ver con instalar soft me tira el error

actualizaciones
synaptic
y desde la consola :(

---

### Post by Hei Ku on 2009-07-13
cuando haces sudo apt-get update te tira este error? O cuando queres hacer un upgrade?

---

### Post by goldenfox on 2009-07-14
cuando hago sudo apt-get update no tira ningun error 
al hacer sudo apt-get upgrade si

---

### Post by Hei Ku on 2009-07-14
Ok.
Probá esto:
```

sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get dist-upgrade

```

Y posteá lo que te tira.
Y también posteá cómo te quedó el archivo /etc/apt/sources.list.

---

### Post by goldenfox on 2009-07-14
goldenfox@ubuntu:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... ¡Error!
E: Problem parsing dependency Replaces
E: Ocurrió un error mientras se procesaba libwpd8c2a (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.


sigue con el error despues de probar lo qe me digiste

---

### Post by Hei Ku on 2009-07-14
pone esto:

sudo apt-get install libwpd8c2a

Y posteá el resultado.

Por lo que veo, ese paquete tiene algo que ver con documentos WordPerfect.

---

### Post by goldenfox on 2009-07-14
ejem lo probe
pero tira el error como las veses anteriores
osea no puden instalar el paquete...
cuando lee la lista de paquetes llega al 94 o 95% y lansa el maldito error

---

### Post by Hei Ku on 2009-07-14
Puede ser que sea un problema con uno de los limites de APT.

En una terminal:
```

sudo nano /etc/apt/apt.conf

```
Y agrega esta linea.
```

APT::Cache-Limit 25165824;

```
Grabá y salí. Despues hace un update y volvé a probar el upgrade.

---

### Post by goldenfox on 2009-07-14
sigue con el condenado error :(

---

### Post by Hei Ku on 2009-07-14
Posteá tu archivo /etc/apt/sources.list

---

### Post by goldenfox on 2009-07-16
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
##newer versions of the distribution.

# deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

##Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
##Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
##Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
##Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
##Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
##Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu intrepid main
# deb http://security.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe
# deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu intrepid main
# parte para arreglar las instalaciones

# deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu jaunty main

# deb http://mirrors.kernel.org/ubuntu/pool/universe/k/kdebindings/python-dcop_3.5.9-0ubuntu1_i386.deb hardy main universe

# deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# cairo composite manager:
# deb http://ppa.launchpad.net/gandalfn/ubuntu intrepid main
##EMESENE CRAIZY 
# deb http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu jaunty main
##TOR Y LOS PROGRAMAS NECESARIOS PARA QUE CORRA
# deb http://mirror.noreply.org/pub/tor jaunty main
# deb-src http://mirror.noreply.org/pub/tor jaunty main
##Themes du ZgegBlog
# deb http://ppa.launchpad.net/bisigi/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu intrepid main
```

---

### Post by Hei Ku on 2009-07-16
Estos dos repositorios tienen que estar habilitados:

# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty main restricted

# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

Sacales el # de adelante.

---

### Post by goldenfox on 2009-07-18
ya lo ise pero sigue con el error :S

---

### Post by Hei Ku on 2009-07-18
Probá esto:
```

cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status

sudo apt-get update

```

---

### Post by goldenfox on 2009-07-19
exelente ya se arreglo el problema :)

pueden bloquear el tema gracias :D

---

### Post by Hei Ku on 2009-07-19
Ma que bloquear!! Asi nomas? Despues de todo lo que me hiciste buscar??? Minimo me invitas un cafe!! :lolflag:

Me alegro que ande. Por fin!

---

### Post by goldenfox on 2009-07-19
ps malas noticias denuevo xD

haora no sale el cartel pero no puedo actualizar ni instalar ni nada 
estor en la misma que antes solo que ahora no sale el cartel al inicio del sistema

```
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/available' cerca de la línea 3510 paquete `librecode0':
 el valor para el campo `status' no está permitido en este contexto
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

susede al instalar, remover y actualizar 
y susede en forma grafica y en la consola ...

---

### Post by Hei Ku on 2009-07-19
A ver:

cd /var/lib/dpkg
sudo mv available available-bad
sudo cp available-old available

sudo apt-get update

---

### Post by goldenfox on 2009-07-20
bien ise los comandos que posteaste
desde la consola intente remover un programa

y salto esto

(Leyendo la base de datos ... dpkg: error fatal irrecuperable, abortando:
 files list file for package `cairo-compmgr' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Hei Ku on 2009-07-20
Me podes explicar que hiciste para romperlo de esa manera? Saliste a hacer skate con el disco? :lolflag:

cd /var/lib/dpkg/info/
sudo mv cairo-compmgr.list cairo-compmgr.list old
sudo apt-get update
sudo apt-get remove cairo-compmgr

---

### Post by goldenfox on 2009-07-20
jaja no, solo lo desinstale y lo quise reinstalar un tiempo despues :S

pero bue siguendo con el tema...

mv: el destino, «old», no es un directorio

---

### Post by guillermolisi on 2009-07-20
Falta un punto. Tiene que quedar de la siguiente forma:
```
sudo mv cairo-compmgr.list cairo-compmgr.list.old
```
Volve a probar todo lo que te paso HeiKu con esta modificacion y conta como te fue.

---

