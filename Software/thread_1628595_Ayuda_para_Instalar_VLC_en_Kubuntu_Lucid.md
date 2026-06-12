---
title: "Ayuda para Instalar VLC en Kubuntu Lucid"
date: 2010-11-22
forum: Software
---

### Post by matias_tati on 2010-11-22
Hola instento agregar el repositorio de VLC siguiendo la guia en su pagina web pero al momento de instalar tengo dependencias que no puedo encontrar en synaptic.
Este es el link de su web

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Y esto es lo que me tira la terminal:

```
Los siguientes paquetes tienen dependencias incumplidas:
  mozilla-plugin-vlc: Depende: vlc-nox (= 1.1.5-1ubuntu2~ppa1~lucid1) pero no va a instalarse
  vlc: Depende: vlc-nox (= 1.1.5-1ubuntu2~ppa1~lucid1) pero no va a instalarse
       Recomienda: vlc-plugin-notify (= 1.1.5-1ubuntu2~ppa1~lucid1) pero no va a instalarse
  vlc-plugin-pulse: Depende: vlc-nox (= 1.1.5-1ubuntu2~ppa1~lucid1) pero no va a instalarse
E: Paquetes rotos
matias@Matias:~$ 

```

Y esto es lo que me tira synaptic cuando intento instalar el paquete vlc-nox

[[img]http://b.imagehost.org/t/0298/instant_nea3.jpg[/img]](http://b.imagehost.org/view/0298/instant_nea3)

Y dicho paquete no lo encuentro en Synaptic

Gracias!!!

---

### Post by guillermolisi on 2010-11-23
Por que no instalas la version de VLC que esta en los repos de Kubuntu ?

---

### Post by matias_tati on 2010-11-23
[[img]http://d.imagehost.org/t/0931/Kubuntu_Lucid_Linux_1.jpg[/img]](http://d.imagehost.org/view/0931/Kubuntu_Lucid_Linux_1)

---

### Post by guillermolisi on 2010-11-23
Proba con apt-get y/o Aptitude y/o Synaptics. KpackageKit tiene algunos comportamientos que no llego a entender (de hecho no suelo usarlo por eso).

Esto siempre que tu lista de repositorios este correcta.

Uso VLC con Kubuntu desde el 2007, versiones de los repos, y nunca tuve ese problema.

---

### Post by matias_tati on 2010-11-23
Desde synaptic me pide las mismas dependencias, por eso busque en la web.

---

### Post by juancarlospaco on 2010-11-23
Hay un PPA que esta fallando alli...

*hay que ver el sources.list*

---

### Post by guillermolisi on 2010-11-23
> **juancarlospaco said:**
> Hay un PPA que esta fallando alli...

*hay que ver el sources.list*
y, por las dudas, tambien el /etc/apt/sources.list.d. Si hay alguna mencion al ppa de VLC u otro vinculado, exhibir su contenido.

---

### Post by matias_tati on 2010-11-23
Tirenme los comandos muchachos no la tengo tan clara con la terminal. Por favor.

---

### Post by guillermolisi on 2010-11-23
> **matias_tati said:**
> Tirenme los comandos muchachos no la tengo tan clara con la terminal. Por favor.
```
less /etc/apt/sources.list
```copias y pegas aqui la salida asi la vemos

```
ls -al /etc/apt/sources.list.d
```y copias y pegas lo que te aparece. Si hay algun archivo que denote alguna relacion con el ppa de VLC lo lees con "less" y copias y pegas a aqui lo que te muestre.

---

### Post by matias_tati on 2010-11-24
less /etc/apt/sources.list

```
# deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ar.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
~
~
(END) 

```

---

### Post by matias_tati on 2010-11-24
Este es el comando:
ls -al /etc/apt/sources.list.d
```
matias@Matias:~$ ls -al /etc/apt/sources.list.d
total 32
drwxr-xr-x 2 root root 4096 2010-11-22 23:02 .
drwxr-xr-x 6 root root 4096 2010-11-21 17:05 ..
-rw-r--r-- 1 root root  176 2010-11-22 23:02 google-chrome.list
-rw-r--r-- 1 root root  176 2010-11-22 23:02 google-chrome.list.save
-rw-r--r-- 1 root root   63 2010-11-22 23:02 lucid-bleed-ppa-lucid.list
-rw-r--r-- 1 root root   63 2010-11-22 23:02 lucid-bleed-ppa-lucid.list.save
-rw-r--r-- 1 root root  416 2010-11-22 23:02 opera.list
-rw-r--r-- 1 root root  416 2010-11-22 23:02 opera.list.save
matias@Matias:~$ 


```

---

### Post by matias_tati on 2010-11-24
Yo tambien creo que viene por ahi la mano

---

### Post by guillermolisi on 2010-11-24
Por lo pronto desactiva el lucid-bleed-ppa-lucid ya que por lo que pudes leer esta en etapa experimental.

Luego, podrias probar cambiando de mirror ? En lugar de usar un mirror de Argentina usa uno de Brasil o los centrales de USA.

Tanto la desactivacion del ppa como el cambio de mirror lo podes gestionar desde Synaptics.

Comenta que tal te va con cada cambio.

---

### Post by matias_tati on 2010-11-24
Hice las dos cosas pero todo igual

---

### Post by guillermolisi on 2010-11-26
Probaste si instala sin el Mozilla-plugin-vlc, que es el que pareceria requiere esas version de nox que no se encuentra ?

---

### Post by marcelo_bur on 2010-11-26
Hola. No estoy seguro de que esto sea útil, pero revisando por curiosidad Synaptic en mi máquina y la última versión de vlc-nox que me aparece, luego de recargar la iformación por las dudas, no es la misma. De todas formas, y tal como se ve en la captura de pantalla, yo no he instalado el programa.
Saludos

---

### Post by matias_tati on 2010-11-26
Listo no habia desactivado el repo. Muchas gracias!!!!

---

