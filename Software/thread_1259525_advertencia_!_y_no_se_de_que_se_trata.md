---
title: "advertencia ! y no se de que se trata"
date: 2009-09-06
forum: Software
---

### Post by drazhe on 2009-09-06
Hola, hace un par de dias, me salto la actualizacion de algo en mi ubuntu 9.04, como de costumbre actualice, puse mi pass y todo bien, hasta 1 paquete que me tiro un error de que no podia pasar la comprobacion de origen o algo asi, desde entonces me aparece un triangulito amarillo con la exclamacion ! dentro y cuando le doy click para ver de que se trata, no aparece ninguna actulizacion pendiente ni nada por el estilo... 

que esta ocurriendo y como solucionar el tema?

---

### Post by guillermolisi on 2009-09-06
> **drazhe said:**
> Hola, hace un par de dias, me salto la actualizacion de algo en mi ubuntu 9.04, como de costumbre actualice, puse mi pass y todo bien, hasta 1 paquete que me tiro un error de que no podia pasar la comprobacion de origen o algo asi, desde entonces me aparece un triangulito amarillo con la exclamacion ! dentro y cuando le doy click para ver de que se trata, no aparece ninguna actulizacion pendiente ni nada por el estilo... 

que esta ocurriendo y como solucionar el tema?
Podrias pasarnos informacion mas detallada al respecto para analizarla ?

Contenidos del /etc/apt/sources.list, del /etc/apt/sources.list.d y si hay archivos dentro de este ultimo directorio, sus contenidos.

---

### Post by drazhe on 2009-09-06
> **guillermolisi said:**
> Podrias pasarnos informacion mas detallada al respecto para analizarla ?

Contenidos del /etc/apt/sources.list, del /etc/apt/sources.list.d y si hay archivos dentro de este ultimo directorio, sus contenidos.

y como saco esa información?

---

### Post by josecuervo86 on 2009-09-06
Para el primero:

```
sudo gedit /etc/apt/sources.list
```

Eso te muestra lo que contiene el archivo, copialo y pegalo aca. Para lo segundo andate a /etc/apt/sources.list.d con nautilus y fijate si hay algo adentro

---

### Post by drazhe on 2009-09-06
Contenidos del /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free


Con los datos del segundo, me saltan unas ventanas como las de las actualizaciones... pero no me permite copiar el texto... quieren que les mande capturas de pantalla?

---

### Post by pablo.s on 2009-09-06
> **drazhe said:**
> hasta 1 paquete que me tiro un error de que no podia pasar la comprobacion de origen o algo asi, desde entonces me aparece un triangulito amarillo con la exclamacion ! dentro y cuando le doy click para ver de que se trata, no aparece ninguna actulizacion pendiente ni nada por el estilo... 


Es muy probable que la
"comprobación de origen"
sea una clave de PPA que
te falta. Por lo tanto no va
a bajar paquetes de ese
repositorio hasta que no
consigas la clave y la añadas
a las fuentes autentificadas.
Fijate que PPA pudiste haber
agregado recientemente.

---

### Post by drazhe on 2009-09-07
bueno tengo mi ubuntu prendido desde hace 1 hora y aun no salto esa advertencia, lo raro es que no hice nada mas que buscar los datos que ustedes me pidieron, así que digamos que fue magia, esperemos que se haya solucionado, gracias a todos!

---

### Post by drazhe on 2009-09-10
la mencionada advertencia volvio, pero esta vez pude copiar los mensajes de error, los pongo aqui para que vean si me pueden ayudar.... 

Primero sale un cartel con esta frase

**Informacion de la actualizacion**

Incidencia de autenticación Apt

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".



EJECUTAR AHORA <-(esto seria el boton que me da a elegir)

luego de Ejecutar esa opcion que me da, la unica por cierto, me tira el siguiente error

**Se ha producido un error**

W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: [http://deb.opera.com](http://deb.opera.com) lenny Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F9A2F76A9D1A0061

W: Imposible obtener cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Imposible obtener cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Imposible obtener [http://deb.opera.com/opera/dists/lenny/Release](http://deb.opera.com/opera/dists/lenny/Release)  

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.



ACEPTAR <-(nuevamente esto seria el boton)

pero despues de realizar todo lo que me dice, me sigue apareciendo la advertencia !, inclusive ejecutandola a mano (alt+f2) update manager y todo eso, no me marca ninguna actualizacion pendiente....

---

### Post by pablo.s on 2009-09-10
> **drazhe said:**
> 
**Se ha producido un error**

W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: [http://deb.opera.com](http://deb.opera.com) lenny Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F9A2F76A9D1A0061

W: Imposible obtener cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Imposible obtener cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs

W: Imposible obtener [http://deb.opera.com/opera/dists/lenny/Release](http://deb.opera.com/opera/dists/lenny/Release)  

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar..

Tendrías que leer obligadamente
[este post]("http://ubuntuforums.org/showthread.php?t=1174296"), o te va a volver a pasar
lo mismo otra vez.
Por la parte del CDROM de Jaunty
que te solicita, tenés que desmarcarlo
en Synaptic, en el menú Preferencias ->
Repositorios.

---

### Post by drazhe on 2009-09-11
gracias Pablo.s pero no entendí nada del tutorial que me pasaste.. además no recuerdo haber instalado nada antes que me pase el error, solo que salto la actualización, le di aceptar y cuando estaba descargando comenzó a tirar el error y desde entonces hay veces que salta la advertencia y oras que no....

---

### Post by pablo.s on 2009-09-11
Vamos de a poco:

Por una parte, en deb.opera.com
dice lo siguiente:

**```
The Opera .deb Repository**

  This repository contains Opera packages for the i386, sparc, and powerpc architectures.
  [/opera/]("http://deb.opera.com/opera/")
 [/opera-beta/]("http://deb.opera.com/opera-beta/")
   
### Example apt source configuration (uncomment the version you want)

# Opera Browser - Production release
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) potato non-free
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) woody non-free
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sarge non-free
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-free

# Opera Browser - Beta release
#deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) potato non-free
#deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) woody non-free
#deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) sarge non-free
#deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) etch non-free
#deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) lenny non-free
#deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) sid non-free



 **The archive gpg fingerprint**

 pub   1024D/9D1A0061 2009-08-31 [expires: 2011-01-23]
      Key fingerprint = 8526 E45F AF83 DE2F 634C  1909 F9A2 F76A 9D1A 0061
uid                  Opera Software Archive Automatic Signing Key 2010 
sub   4096g/87DEACAE 2009-08-31 [expires: 2011-01-23]
 **To install the key on your host, do something like this:**

  **Debian user**

 wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | apt-key add -
 **Ubuntu users**

 **[COLOR=Red]wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -[/COLOR]**
 **Or snarf this one**

 -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.1 (GNU/Linux)

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
=wGGg
-----END PGP PUBLIC KEY BLOCK-----
 Perhaps it IS a good day to die! I say we ship it!
				-- Klingon Programmer
**
```**

   Tenés que copiar la linea que he
resaltado en color rojo. Luego vas a
una terminal, presionas CTRL+Shift+V
y presionas enter.
Dejas que busque la clave (puede que te
solicite la contraseña) y vuelves a Synaptic
donde le das al primer botón grande que
dice "Recargar", son dos flechas azules.

---

### Post by drazhe on 2009-09-11
bien, hice lo que me dijiste, y ahora me tiro esto...



No se pudieron descargar todos los índices de los repositorios

El repositorio quizá no esté disponible o no se pudo contactar con él por problemas en la red. Si hay disponible una versión más antigua del índice que falló, se usará esa versión. En caso contrario el repositorio se ignorará. Compruebe su conexión de red y que la dirección del repositorio esté escrita correctamente en las preferencias.


Imposible obtener cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Imposible obtener cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Por favor utilice apt-cdrom para hacer que APT reconozca este CD. apt-get update  no se puede usar para agregar nuevos CDs
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.



Hago lo mismo que la anterior con estas direcciones?

---

### Post by pablo.s on 2009-09-11
No, ahi tenés que ir a Synaptic
->Preferencias (o Settings) ->
Repositorios.
Se abre una ventanita con solapitas
que dice Fuentes de Software. Abajo
dice "A instalar desde CDROM" y hay
dos items con cuadraditos a la izquierda,
los debes desmarcar. Luego presionas
sobre "Cerrar" y otra vez en el icono
de arriba a la izquierda que dice Recargar.

---

### Post by drazhe on 2009-09-11
lo mas parecido que encontre a lo que decis, es ORIGENES DEL SOFTWARE y me aparecen 7 lineas con sus respectivos cuadraditos... 

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (codigo fuente)
[B][http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) main
[http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) main (codigo fuente)
[http://deb.opera.com/opera](http://deb.opera.com/opera) lenny non-free
medibuntu - ubuntu 9.04 jaunty jackalope free non free
[/B]medibuntu (source) ubuntu 9.04 jaunty jackalope free non free (codigo fuente)

lo que aparece en negrita esta tildado, lo demas no...

---

### Post by pablo.s on 2009-09-11
[ATTACH]128218[/ATTACH]

Fijate en esta captura.

---

### Post by drazhe on 2009-09-11
> **pablo.s said:**
> [ATTACH]128218[/ATTACH]

Fijate en esta captura.


muchas gracias pablo.s ahora parece haberse solucionado... ya no me tiro el error... voy a dejarlo toda la noche hoy para ver si vuelve a saltar, pero por lo menos pude actualizar sin que me saltara las advertencias...

---

