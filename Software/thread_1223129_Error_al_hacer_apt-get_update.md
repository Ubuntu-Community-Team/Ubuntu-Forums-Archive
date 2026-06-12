---
title: "Error al hacer apt-get update"
date: 2009-07-25
forum: Software
---

### Post by Fisaulerod on 2009-07-25
Hola, sucede que cuando hago apt-get update, al final me sale esto:

W: Error de GPG: [http://deb.opera.com](http://deb.opera.com) etch Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 033431536A423791

Este es mi Sources.list:

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cl.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

¿Cómo lo soluciono? Gracias de antemano.

---

### Post by aledruetta on 2009-07-25
No entiendo, está pidiendo la llave para el repositorio de Opera, pero el repositorio no está en el sources.list

---

### Post by aledruetta on 2009-07-25
Creo que para agregar la llave es:
```
sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

---

### Post by felipeleven on 2009-07-26
¿ Por casualidad instalaste opera a través de un .deb desde la página oficial de opera?

Te lo pregunto porque yo lo hice así y al buscar actualizaciones me ocurrió algo así. Lo que hice fue desinstalar el opera a través de synaptic y automaticamente desaparecieron los repositorios de opera que ese paquete .deb había agregado.

No se si tendrá que ver, pero dejo mi experiencia.

Saludos

---

### Post by aledruetta on 2009-07-26
> **felipeleven said:**
>  y automaticamente desaparecieron los repositorios de opera que ese paquete .deb había agregado.

Lo que no consigo ver en el sources.list son justamente los repositorios de Opera que estarían pidiendo la llave ¿no deberían estar ahí?

Yo intentaría incorporar la llave y ver qué pasa.

---

### Post by felipeleven on 2009-07-26
Los repositorios que opera había agregado lo vi vía synaptic, en la sección de origenes de software.
Ahora como Aledruetta dice, una buena opción es agregar la llave, con eso ubuntu debería actualizar normalmente.

Saludos!

---

### Post by Fisaulerod on 2009-07-26
Hola, agregué la llave y ahora sale esto:

W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 5A9BF3BB4E5E17B5

---

### Post by aledruetta on 2009-07-26
En varios sitios recomiendan hacer lo siguiente:
```
Este es un error típico despues de añadir un nuevo repositorio a nuestra lista de repositorios de paquetes. **W: Error de GPG: http://ppa.launchpad.net intrepid Release. Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY E9E8FF4F73AB42F2**
 Para agregar la clave o la keyserver de este y otros servidores hay que teclear un comando indicando el último número de el error anterior. Para solucionar el error anterior el comando sería:
 **sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys 5A9BF3BB4E5E17B5**
 Como norma general el comando es:
 **sudo apt-key adv &#8211;keyserver keyserver.ubuntu.com &#8211;recv-keys ****[el codigo del NO_PUBKEY]**
 

```[http://elblogdepablo.wordpress.com/category/software-libre/](http://elblogdepablo.wordpress.com/category/software-libre/)

Para tu caso el número sería: 5A9BF3BB4E5E17B5

Espero que eso solucione tu problema, sino, seguimos intentando,
Saludos.

---

### Post by EnriqueK on 2009-07-27
La tendencia actual es crear la lista de fuentes de terceros en archivos diferentes al sources.list , estos se ubican dentro de la carpeta **/etc/apt/sources.list.d**
Los errores de llave pública los resulvo poniedo en terminal lo siguiente
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys         1CD52D7BAAFE086A
gpg --export --armor         1CD52D7BAAFE086A | sudo apt-key add -
```
Allí la sentencia es para 1CD52D7BAAFE086A , por lo que debes reenplazar este valor por el que te indica en el mensaje de alerta.

---

### Post by aledruetta on 2009-07-27
Encontré un sitio para generar interactivamente un sources.list on-line. Véanlo a ver qué les parece.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Fisaulerod on 2009-07-27
> **EnriqueK said:**
> La tendencia actual es crear la lista de fuentes de terceros en archivos diferentes al sources.list , estos se ubican dentro de la carpeta **/etc/apt/sources.list.d**
Los errores de llave pública los resulvo poniedo en terminal lo siguiente
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys         1CD52D7BAAFE086A
gpg --export --armor         1CD52D7BAAFE086A | sudo apt-key add -
```Allí la sentencia es para 1CD52D7BAAFE086A , por lo que debes reenplazar este valor por el que te indica en el mensaje de alerta.

gracias, hice eso y funciono :P.

---

