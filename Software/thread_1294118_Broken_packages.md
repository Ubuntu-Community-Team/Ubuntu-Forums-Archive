---
title: "Broken packages"
date: 2009-10-17
forum: Software
---

### Post by autusgo on 2009-10-17
Hola a todo el mundo!
Buenas! Soy relativamente nuevo en Linux (si bien vengo probando el sistema operativo desde el 97/98 nunca me había "pasado" en serio). Estoy corriendo Kubuntu 9.04, me las arreglé de alguna manera para instalar KDE 4.3 y tengo el siguiente problema:
Cuando intento instalar CUALQUIER COSA obtengo esto en Adept
 p, li { white-space: pre-wrap; }  [I]
[/I]
[I]Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: [/I]
 [I][FONT=monospace]APT Error. Context:
    Package download failed, 
    Unable to correct problems, you have held broken packages., 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : [/FONT][/I]
Evidentemente tengo "broken packages", y supongo que necesito identificarlos y eliminarlos; y en lo posible saber qué hacer para que no me vuelva a pasar.
En general en los foros te mandan a Synaptic a hacer cosas, pero obviamnete no tengo Synaptic, tengo Adept. He probado varias cosas que he visto en distintos foros y lugares como *sudo apt-get install -f* entre otras.

Si necesitan alguna otra información, haganmeló saber.

Muchas gracias!!

---

### Post by guillermolisi on 2009-10-17
> **autusgo said:**
> Hola a todo el mundo!
Buenas! Soy relativamente nuevo en Linux (si bien vengo probando el sistema operativo desde el 97/98 nunca me había "pasado" en serio). Estoy corriendo Kubuntu 9.04, me las arreglé de alguna manera para instalar KDE 4.3 y tengo el siguiente problema:
Cuando intento instalar CUALQUIER COSA obtengo esto en Adept
 p, li { white-space: pre-wrap; }  
[I]Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: [/I]
 [I][FONT=monospace]APT Error. Context:
    Package download failed, 
    Unable to correct problems, you have held broken packages., 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : [/FONT][/I]
Evidentemente tengo "broken packages", y supongo que necesito identificarlos y eliminarlos; y en lo posible saber qué hacer para que no me vuelva a pasar.
En general en los foros te mandan a Synaptic a hacer cosas, pero obviamnete no tengo Synaptic, tengo Adept. He probado varias cosas que he visto en distintos foros y lugares como *sudo apt-get install -f* entre otras.

Si necesitan alguna otra información, haganmeló saber.

Muchas gracias!!
Adept no existe mas en KDE 4.3, fue reemplazado por KPackageKit.
Proba de resolver los paquetes rotos con este utilitario y si tembien falla podemos seguir con Aptitude o apt-get en consola.

---

### Post by autusgo on 2009-10-18
No sabía nada que Adept no existía en KDE 4.3, KPackageKit lo us{e un par de veces, pero pensé que era para updates nada más. Ahora estoy tratando de instalar Amarok y está como medio colgado en "Querying" hace como 5 minutos, así que calculo que las cosas no están funcionando como quisiera...

En terminal probé algunas cosas de aptitud y apt-get pero no pasó nada. Igualmente puedo volver a probarlas y poster que es lo que me aparece.

Gracias por la ayuda!

---

### Post by guillermolisi on 2009-10-18
> **autusgo said:**
> No sabía nada que Adept no existía en KDE 4.3, KPackageKit lo us{e un par de veces, pero pensé que era para updates nada más. Ahora estoy tratando de instalar Amarok y está como medio colgado en "Querying" hace como 5 minutos, así que calculo que las cosas no están funcionando como quisiera...

En terminal probé algunas cosas de aptitud y apt-get pero no pasó nada. Igualmente puedo volver a probarlas y poster que es lo que me aparece.

Gracias por la ayuda!
Para hacer las cosas sabiendo como es el contexto, deberiamos empezar por mostrar el contenido de /etc/apt/sources.list y, por las dudas, si hay algun archivo en /etc/apt/sources.list.d, tambien.

Cuando inicias Aptitude hay una funcion que te muestra los paquetes rotos (Search-Find Broken), lo mismo sucede con apt-get pero me parece que Aptitude te resultara mas amigable.

Que version de Ubuntu estas usando ?
Como esta tu conexion a Internet ?

---

### Post by autusgo on 2009-10-18
Esto es lo que hay en /etc/apt/sources.list:

[HTML]# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu karmic main
deb-src http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu karmic main
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main[/HTML]

Y en /etc/apt/sources.list.d hay 3 archivos de lyriczilla, que de paso nunca logré que funcione bien. Si necesitás los nombres de esos archivos o algo, avisame.

La verdad es que no sé como usar Aptitude necesitaría que me guies un poco más con esa función para mostrar los paquetes rotos.
Estoy usando Kubuntu 9.04 (hasta que llegue la 9.10) y mi conexión a internet es por ADLS telefónica (Arnet) a través de un router.

---

### Post by guillermolisi on 2009-10-18
> **autusgo said:**
> Esto es lo que hay en /etc/apt/sources.list:

[html]# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu karmic main
deb-src http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu karmic main
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main[/html]Y en /etc/apt/sources.list.d hay 3 archivos de lyriczilla, que de paso nunca logré que funcione bien. Si necesitás los nombres de esos archivos o algo, avisame.

La verdad es que no sé como usar Aptitude necesitaría que me guies un poco más con esa función para mostrar los paquetes rotos.
Estoy usando Kubuntu 9.04 (hasta que llegue la 9.10) y mi conexión a internet es por ADLS telefónica (Arnet) a través de un router.
> [COLOR=Blue]deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main[/COLOR]
[COLOR=Red]deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) karmic main[/COLOR]

Los repositorios que marque en rojo no deberian estar junto con los de Jaunty. O tenes todo Jaunty o tenes todo Karmic.

Si queres usar KDE 4.3 deberias usar el ppa de KDE 4.3 para Jaunty (marcado con azul) o decidir si queres pasarte definitivamente a Karmic que trae por defecto KDE 4.3 para Kubuntu (que aun esta en beta).

---

### Post by autusgo on 2009-10-18
> **guillermolisi said:**
> Los repositorios que marque en rojo no deberian estar junto con los de Jaunty. O tenes todo Jaunty o tenes todo Karmic.

Si queres usar KDE 4.3 deberias usar el ppa de KDE 4.3 para Jaunty (marcado con azul) o decidir si queres pasarte definitivamente a Karmic que trae por defecto KDE 4.3 para Kubuntu (que aun esta en beta).

OK creo que entendí cual puede ser el problema. Yo me quise apasar a KDE 4.3 y debo haber hecho macana (por no decir otra cosa).

Qué me recomendás? Me pasó directamente a Karmic? Espero que salga de Beta? O uso el ppa de KDE 4.3 de Jaunty? (que no tengo la menor idea como se hace).

Gracias!

---

### Post by guillermolisi on 2009-10-18
> **autusgo said:**
> OK creo que entendí cual puede ser el problema. Yo me quise apasar a KDE 4.3 y debo haber hecho macana (por no decir otra cosa).

Qué me recomendás? Me pasó directamente a Karmic? Espero que salga de Beta? O uso el ppa de KDE 4.3 de Jaunty? (que no tengo la menor idea como se hace).

Gracias!
Faltando menos de dos semanas para que este disponible la version final de KK, espera y comenta/desactiva los repositorios que hacen mencion a esa version (aun en beta).

El repo ppa de KDE4.3 ya lo tenes, es el que indique en azul.

Mi recomendacion es que estabilices la instalacion que tenes ahora con vista a que puedas hacer una actualizacion sin problemas cuando se libere la 9.10.

Edit: revisa estas lineas que no se si las tenes mal o fue una cuestion de transcripcion:
> # deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

Te deberian quedar asi
```
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```

---

### Post by EnriqueK on 2009-10-18
Nunca lo hice, pero creo recordar que iniciando el Grub en Recovery Mode, se tiene una opci&#7765;n para reparar paquetes rotos.
Cuando repares los paquetes rotos, recomiendo  que instales el festor de paquetes Synaptic

---

### Post by guillermolisi on 2009-10-18
> **EnriqueK said:**
> Nunca lo hice, pero creo recordar que iniciando el Grub en Recovery Mode, se tiene una opci&#7765;n para reparar paquetes rotos.
Cuando repares los paquetes rotos, recomiendo  que instales el festor de paquetes Synaptic
Por mas que tenga el software que sea, si los repositorios no estan en orden seguira con problemas.

---

### Post by autusgo on 2009-10-19
> **guillermolisi said:**
> Faltando menos de dos semanas para que este disponible la version final de KK, espera y comenta/desactiva los repositorios que hacen mencion a esa version (aun en beta).

El repo ppa de KDE4.3 ya lo tenes, es el que indique en azul.

Mi recomendacion es que estabilices la instalacion que tenes ahora con vista a que puedas hacer una actualizacion sin problemas cuando se libere la 9.10.

Edit: revisa estas lineas que no se si las tenes mal o fue una cuestion de transcripcion:


Te deberian quedar asi
```
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```

Intenté modificar el archivo source.list pero no me deja guardarlo. De dónde se puede editar sino?

Gracias!

---

### Post by guillermolisi on 2009-10-19
> **autusgo said:**
> Intenté modificar el archivo source.list pero no me deja guardarlo. De dónde se puede editar sino?

Gracias!
Para editarlo y guardarlo sin problemas ```
sudo <tu_editor_preferido> /etc/apt/sources.list
```

---

### Post by autusgo on 2009-10-19
Buenísimo! Ya está. Ahora está así:

[HTML]# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main 
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main[/HTML]

Sigo sin poder instalar nada, pero supongo que eso se solucionará cuando haga el upgrade a 9.10. Igualmente cuando vuelva del trabajo voy a probar arreglar los paquetes rotos con el Recovery Mode a ver que pasa. Posteo los resultados.

Gracias!

---

### Post by guillermolisi on 2009-10-19
> **autusgo said:**
> Buenísimo! Ya está. Ahora está así:

[html]# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
# deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main 
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main[/html]Sigo sin poder instalar nada, pero supongo que eso se solucionará cuando haga el upgrade a 9.10. Igualmente cuando vuelva del trabajo voy a probar arreglar los paquetes rotos con el Recovery Mode a ver que pasa. Posteo los resultados.

Gracias!
Aun tenes repositorios que no corresponden a la version que estas usando:
> deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/)[COLOR=Red] intrepid[/COLOR]-backports main restricted universe multiverse


---

### Post by guillermolisi on 2009-10-20
> **autusgo said:**
> Listo!
Borré esa linea, supongo que lo único que me queda es esperar.

Ahora sí... Bootié en Recovery Mode arreglé los paquetes rotos (o eso creo), pero ahora cuando reinicié tengo la PC en 800x600 y no pude cambiarlo. Alguna pista? Supongo que desconfiguraron los dirvers de la placa de video o algo... Pero la resolución más alta que me ofrece es 800x600 cuando tengo un monitor de 22'' con DVI... Un desperdicio jeje.
Estuve mirando cosas en internet y tratando de toquetear en System Settings, pero hasta ahora no lo pude cambiar. Cuando vuelva del trabajo sigo probando. Cualquier ayuda es bienvenida.

Gracias!
Va en [thread aparte]("http://ubuntuforums.org/showthread.php?t=1296366") porque ya no tiene que ver con los paquetes sino con la puesta a punto de la resolucion de video.

---

### Post by autusgo on 2009-10-21
> **guillermolisi said:**
> Va en [thread aparte]("http://ubuntuforums.org/showthread.php?t=1296366") porque ya no tiene que ver con los paquetes sino con la puesta a punto de la resolucion de video.

Sisi ya sé. Lo comenté para que sepan que después de arreglar los paquetes rotos con el Recovery Mode puede pasar esto. Ya está solucionado.

Sigo esperando al Karmic para poder instalar algo... Faltan 8 días!

Gracias a todos por la ayuda!

---

### Post by autusgo on 2009-10-31
Bien, con el upgrade a Karmic Koala se terminaron los problemas con los repositorios, aparentemente.Ya pude instalar varias cosas y quise esperar un par de días para postearlo para estar seguro.

Gracias por la ayuda!

---

### Post by guillermolisi on 2009-10-31
> **autusgo said:**
> Bien, con el upgrade a Karmic Koala se terminaron los problemas con los repositorios, aparentemente.Ya pude instalar varias cosas y quise esperar un par de días para postearlo para estar seguro.

Gracias por la ayuda!
Moraleja: No tocar la lista de repositorios si no se sabe a ciencia cierta que se esta haciendo al agregar o quitar uno. Siempre uno puede beneficiarse con la alternativa de preguntar antes que hacer (medicina preventina :) )

---

