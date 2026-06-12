---
title: "Problema con gestor de software en Kubuntu"
date: 2010-03-18
forum: Software
---

### Post by matias_tati on 2010-03-18
Hola bueno es la 1era vez que lo instalo y me aparece esto cuando entro al gestor de software kde
[[img]http://b.imagehost.org/t/0597/instant_nea1.jpg[/img]](http://b.imagehost.org/view/0597/instant_nea1)

---

### Post by guillermolisi on 2010-03-18
Proba en una consola/terminal ```
sudo apt-get update
``` a ver si funciona o te da error.

---

### Post by matias_tati on 2010-03-18
```
matias@PCmatias:~$ sudo apt-get update
[sudo] password for matias:
E: Línea 5 mal formada en lista de fuentes /etc/apt/sources.list (análisis de URI)
matias@PCmatias:~$

```

---

### Post by guillermolisi on 2010-03-18
Mostranos el contenido de ese archivo, por favor.

En la imagen que pasaste lo tenias en edicion con Kate, lo abriste antes o despues de lanzar el KapackageKit ?

---

### Post by matias_tati on 2010-03-19
Lo abri despues igual lo quise modificar y no me dejo por consola y graficamente no tengo los permisos
```
# deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb karmic main restricted
deb-src karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb karmic-updates main restricted
deb-src karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb karmic universe
deb-src karmic universe
deb karmic-updates universe
deb-src karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb karmic multiverse
deb-src karmic multiverse
deb karmic-updates multiverse
deb-src karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb karmic-security main restricted
deb-src karmic-security main restricted
deb karmic-security universe
deb-src karmic-security universe
deb karmic-security multiverse
deb-src karmic-security multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse #Added by software-properties

```

---

### Post by guillermolisi on 2010-03-19
De que mirror estas tomando los repositorios ?

Como los de Argentina (patan y el nuevo que aun estan terminando de poner a punto) estan con problemas de conectividad cambie a uno en Brasil. Te pregunto porque me parece que el tema viene por el lado que como no puede conectar con el que tenes definido no resuelve bien las URL de cada uno.

Fijate en el ejemplo las diferencias entre lo que tengo y lo que tenes:
```
# deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sft.if.usp.br/ubuntu/ karmic main restricted
deb-src http://sft.if.usp.br/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sft.if.usp.br/ubuntu/ karmic-updates main restricted
deb-src http://sft.if.usp.br/ubuntu/ karmic-updates main restricted
```
como en tu caso las URL no esta resueltas te da error cuando lee el sources.list

---

### Post by matias_tati on 2010-03-19
Te referis a esto?

[[img]http://e.imagehost.org/t/0824/instant_nea2.jpg[/img]](http://e.imagehost.org/view/0824/instant_nea2)

---

### Post by leonardomdq on 2010-03-19
Matias probaste activando los repositorios main, restricted y universe?

---

### Post by juancarlospaco on 2010-03-20
*Veo un sources.list nuevo en tu futuro...*

---

### Post by matias_tati on 2010-03-20
Yo tambien. Como lo hago? No recuerdo bien como hacerlo, por consola no pude y graficamnte no se como acceder con los permisos necesarios.

---

### Post by guillermolisi on 2010-03-20
Matias

Esa opcion que marcaste con el cursor en la imagen es la indicada para cambiar de mirror y elegir, por ejemplo, uno de Brasil (como te mostre en mi ejemplo).

Luego, marca (en los chekboxes) los repositorios que indico con su pregunta Leonardomdq. Proba de actualizar el cache (Recargar/Reload) y contanos como resulto.

Hacer un sources.list nuevo es tan complicado como copiar y pegar partiendo de uno que este funcionando bien, asi que no te compliques con eso, por ahora.

---

### Post by matias_tati on 2010-03-20
Si selecciono la opcion otro no me da la opcion de elegir el de Brasil, no me da ninguna opcion en realidad.

---

### Post by alfplayer on 2010-03-20
No aparece algo así?

[IMG]http://www.linuxmint.com/pictures/screenshots/helena/mintupdate-software-sources-mirrors.png[/IMG]

---

### Post by matias_tati on 2010-03-20
No. selecciono "otro" y no se me abre ninguna ventana.

---

### Post by alfplayer on 2010-03-20
El problema principal es que están faltando las URL después de deb y deb-src (deben estar como mostró Guillermo [http://.](http://.)..). Si el archivo de backup /etc/apt/sources.list.save existe y no está corrupto como el que está en uso se puede restaurar.

Para estar seguro que no interfieran dejar cerrados los programas y ventanas de administración de paquetes como los anteriores. Se podría restaurar ejecutando:

```
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
```

Después habría que reactualizar el índice para que tome el nuevo archivo, y después sí se podría volver a usar el sistema de administración de paquetes normalmente (instalar, eliminar paquetes, etc.).

---

### Post by matias_tati on 2010-03-20
```
matias@PCmatias:~$ sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
[sudo] password for matias:
matias@PCmatias:~$ sudo apt-get update
E: Línea 5 mal formada en lista de fuentes /etc/apt/sources.list (análisis de URI)
matias@PCmatias:~$

```

---

### Post by alfplayer on 2010-03-20
> **matias_tati said:**
> ```
matias@PCmatias:~$ sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
[sudo] password for matias:
matias@PCmatias:~$ sudo apt-get update
E: Línea 5 mal formada en lista de fuentes /etc/apt/sources.list (análisis de URI)
matias@PCmatias:~$

```

Esto debe ser porque el archivo automático de backup también está dañado. Podés probar con el siguiente (el programa que para editarlo debe ser abierto con permisos de root), p.e.:

```
kdesudo kate /etc/apt/sources.list
```("kdesudo" es para ejecutar kate con permisos de root, desde un terminal se puede usar "sudo")

```
deb-src http://mirror.anl.gov/pub/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ karmic main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ karmic multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ karmic-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ karmic universe
deb http://mirror.anl.gov/pub/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ karmic multiverse
deb http://mirror.anl.gov/pub/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mirror.anl.gov/pub/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://mirror.anl.gov/pub/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://mirror.anl.gov/pub/ubuntu/ karmic-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://mirror.anl.gov/pub/ubuntu/ karmic-security universe
deb http://mirror.anl.gov/pub/ubuntu/ karmic-security multiverse
```

---

### Post by matias_tati on 2010-03-21
Reemplaze mi source.list por el tuyo y ahora me tira esto: 

[[img]http://b.imagehost.org/t/0398/instant_nea3.jpg[/img]](http://b.imagehost.org/view/0398/instant_nea3)

---

### Post by alfplayer on 2010-03-21
Lo que dice esa ventana es que hay dependencias rotas. Había problemas para instalar y remover paquetes antes de usar KPackageKit ? Como sugiere el texto, se puede intentar resolver con Synaptic o aptitude. Con Synaptic está la opción en "Editar" --> "Reparar paquetes rotos".

---

### Post by matias_tati on 2010-03-21
Donde c..... esta synaptic en KDE??? estoy re perdido

---

### Post by alfplayer on 2010-03-21
Se puede ejecutar "synaptic" desde terminal. Si no está instalado se puede instalar primero.

---

### Post by guillermolisi on 2010-03-21
Synaptic no se instala por defecto en KDE. Se instala por demanda.

Podria usarse tambien Aptitude que se instala siempre y tambien posee resolucion de paquetes rotos.
No es tan intuitivo como Synaptci, tampoco grafico ya que se invoca en una consola/terminal, pero funciona muy bien siempre y es muy potente.

---

### Post by matias_tati on 2010-03-21
Gracias.

---

