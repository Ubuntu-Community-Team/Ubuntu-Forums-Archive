---
title: "Ayuda con Repositorios"
date: 2010-05-19
forum: Software
---

### Post by guillermon on 2010-05-19
Hola, nunca aprendo y siempre tengo problemas con los repositorios. Espero esta vez entenderlo... (me ayudan?). 
   Descripción: viene tirando error desde que hice las primeras instalaciones, pero ahora ya no puedo instalar nada. A continuación muestro lo que me dice luego de querer instalar un paquete con synaptic.
```
E: No se pudo tratar el archivo de paquetes /var/lib/apt/lists/mirror.globo.com_ubuntu_archive_dists_lucid_main_i18n_Translation-es (2)
E: No se ha podido bloquear el directorio de descargas

```

 Muestro mi /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.globo.com/ubuntu/archive/ lucid main restricted
deb-src http://mirror.globo.com/ubuntu/archive/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.globo.com/ubuntu/archive/ lucid-updates main restricted
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.globo.com/ubuntu/archive/ lucid universe
deb-src http://mirror.globo.com/ubuntu/archive/ lucid universe
deb http://mirror.globo.com/ubuntu/archive/ lucid-updates universe
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.globo.com/ubuntu/archive/ lucid multiverse
deb-src http://mirror.globo.com/ubuntu/archive/ lucid multiverse
deb http://mirror.globo.com/ubuntu/archive/ lucid-updates multiverse
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-updates multiverse

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
## respective vendors as a service to Ubuntu## Repositorio Medibuntu:
deb http://mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
deb-src http://mirrors.ucr.ac.cr/medibuntu/ lucid free non-free users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.globo.com/ubuntu/archive/ lucid-security main restricted
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-security main restricted
deb http://mirror.globo.com/ubuntu/archive/ lucid-security universe
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-security universe

## Repositorio Medibuntu:
# deb http://mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
# deb-src http://mirrors.ucr.ac.cr/medibuntu/ lucid free non-free
deb http://mirror.globo.com/ubuntu/archive/ lucid-security multiverse
deb-src http://mirror.globo.com/ubuntu/archive/ lucid-security multiverse
```

    Gracias a todos desde ya. Grato saludo..:)

---

### Post by juancarlospaco on 2010-05-19
Cambiar **mirror.globo.com** por **archive.ubuntu.com** en todas las lineas.

---

### Post by guillermolisi on 2010-05-19
Es un bug en Synaptic cuando se usa Ubuntu en Español y se quiere instalar algo utilizando la funcion de busqueda de paquetes.

Si elegis/marcas paquetes para instalar directamente de la lista general, sin usar la funcion de busqueda, deberia trabajar sin ese error.

El mirror de Globo funciona perfecto y en mi humilde opinion nada tiene que ver con el error. De todas formas el mirror central tambien esta funcionando muy bien.

---

### Post by guillermon on 2010-05-19
> **juancarlospaco said:**
> Cambiar **mirror.globo.com** por **archive.ubuntu.com** en todas las lineas.

Hola Juan Carlos, he editado reemplazando todas las líneas (usando la herramienta Reemplazar), y cuando fuí a actualizar me dió el siguiente error:
```
Imposible obtener http://mirrors.ucr.ac.cr/medibuntu/dists/lucid/Release  Unable to find expected entry  users./source/Sources in Meta-index file (malformed Release file?)
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/main/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.45 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.45 80]
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```
Bueno, no tengo idea de qué hacer. Otra sugerencia? Desde ya gracias

---

### Post by alfplayer on 2010-05-20
guillermon: El primer problema es lo que dijo Guillermo. El segundo parece que es porque está mal hecho el reemplazo (el segundo "archive" creo que no debe estar),

---

### Post by guillermon on 2010-05-21
> **alfplayer said:**
> guillermon: El primer problema es lo que dijo Guillermo. El segundo parece que es porque está mal hecho el reemplazo (el segundo "archive" creo que no debe estar),

Hola Alfplayer. Respecto a lo que dice Guillermo, no solo me ocurre en synaptic, sino en actualizaciones del sistema y cuando quiero instalar por consola con apt-get, etc. Digamos, en este momento no solo no puedo actualizar, sino instalar (aún desde el centro de software).
    Hice lo que sugerís, de quitar el segundo "archive". Al darle luego al Centro de Actualizaciones me da el siguiente error (similar cuando quiero instalar algo).
```
Imposible obtener http://mirrors.ucr.ac.cr/medibuntu/dists/lucid/Release  Unable to find expected entry  users./source/Sources in Meta-index file (malformed Release file?)
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/main/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]
Imposible obtener http://archive.ubuntu.com/ubuntu/archive/dists/lucid-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```

   Bueno. Creo que debería empezar de nuevo y agregar los repositorio de Mediubuntu de nuevo... (que por lo que leo los tengo dos veces); cómo se haría algo así?
    Gracias! Espero comentarios...

---

### Post by guillermolisi on 2010-05-22
Synaptic usa apt-get asi que si quedo bloquedo en una tambien lo esta con la otra alternativa.

Podes intentar instalar y desinstalar con Aptitude que se puede usar en modo CLI o con su menu (en consola). Aptitude funciona igual porque no utiliza la misma estructura de cache que apt-get.

Estas modificando el archivo que contiene las referencias a los repositorios editandolo ?
Es mas seguro utilizar la aplicacion Origenes del Software, por lo menos minimiza los errores de tipeo y tratas un repositorio por vez. Ademas para cambiar de mirror es mas sencillo aun.

---

### Post by leonardomdq on 2010-05-22
Cuando salió Lucid tuve un problema parecido al tuyo con los repositorios.

Como te comento Guillermo un par de mensajes más arriba proba cambiando el mirror (desde orígenes de software), estoy usando el mirror central y funciona de maravillas.

Proba usando **aptitude update** (en una terminal) en vez de apt-get update , cuando cambie la forma de actualizar me bajaron cantidad de paquetes que con apt-get no me aparecían.

Después desde el Gestor de Actualizaciones los instale sin problemas.

---

### Post by guillermon on 2010-05-22
> **guillermolisi said:**
> Estas modificando el archivo que contiene las referencias a los repositorios editandolo ?
Es mas seguro utilizar la aplicacion Origenes del Software, por lo menos minimiza los errores de tipeo y tratas un repositorio por vez. Ademas para cambiar de mirror es mas sencillo aun.
Guillermo: he modificado el servidor por el central (cuando lo modifiqué anteriormente lo hice por el de argentina). Cuando actualizó fallaron los que terminaban es -es; y arrojó un texto de error
```
mposible obtener http://mirrors.ucr.ac.cr/medibuntu/dists/lucid/Release  Unable to find expected entry  users./source/Sources in Meta-index file (malformed Release file?)
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
```
 Luego me ha permitido instalar las actualizaciones e instalar desde synaptic.

   Ahora bien, respondiendo a tus comentarios, sí, lo corregí editando con gedit. Añado un pantallazo de mi Orígenes de Soft, a lo mejor me dice qué está mal... Muchas gracias a todos, pues ya está prácticamente todo bien...

Guillermo

---

### Post by leonardomdq on 2010-05-22
> **guillermon said:**
> pues ya está prácticamente todo bien...


Elimina de Origenes del Software los dos primeros de Medibuntu que son los que te traen conflictos. Fijate que lo tenes dos veces agregado.

---

### Post by guillermon on 2010-05-22
> **leonardomdq said:**
> Elimina de Origenes del Software los dos primeros de Medibuntu que son los que te traen conflictos. Fijate que lo tenes dos veces agregado.
Hola Leonardo. Yo había notado que estaba repetido, pero no quería seguir metiendo la pata... Ahora sí! Libre de error... Gracias a todos. Saludos!

Guillermo:popcorn:

---

