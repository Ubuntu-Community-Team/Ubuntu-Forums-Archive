---
title: "Ayudaaaaa - Bajar programas desde windows y copiarlos en un pen drive"
date: 2009-01-22
forum: Software
---

### Post by joe_mza04 on 2009-01-22
Hola soy nuevo en ubuntu y no tengo internet. Y queria saber si hay alguna forma de bajar los programas completos con sus dependencias a un pendrive desde una maquina con windows y luego intalarlo en mi pc con ubuntu.



Gracias

---

### Post by Hei Ku on 2009-01-22
te podes bajar los .deb desde getdeb.net y despues instalarlo haciendo doble click.

Consejo: si solo pones ayuda en el titulo sin especificar que problema tenes, mucha gente ni se va a tomar la molestia de leer el mensaje.

---

### Post by EnriqueK on 2009-01-22
Si se puede, pero primero tenés que clonar los archivos índices o índices de repositorios de otro equipo que los tenga actualizados o también puede ser que uses el Live CD de instalación en un equipo que tenga conexión a internet y allí creas un sources.list , haces sudo apt-update y esta operación te va a generar los índices que se ubicarán en la carpeta lists situada en /var/lib/apt, los pasos serían los siguientes 
1.- ponés **sudo nautilus /etc/apt ** y de allí copías la carpeta **sources.list.d ** y el archivo **sources.list**
2.- Ponés **sudo nautilus /var/lib/apt**  y de allí copías la carpeta **lists**
3.- Llevás esos datos a tu PC sin conexión usando por ej un pendrive y empleas el mismo procedimiento para poner esos elementos, reemplazado los existentes
4.- En tu PC sin conexión hacés **sudo apt-get update** y ya tenés clonados los índices.

Ahora toca aprir Synaptic , pulsas el botón Estado --> Instalados (actualizables) , aparecen todas las actualizaciones , luego Menú Editar-->marcarcar todas las actualizaciones , aceptá , seguidamente Menú Archivo --> Generar un Script de descargas de paquetes , le pones un nombre y se genera el Script en la carpeta de usuario . Este Script es básicamente un listado de las URLs de los paquetes a descargar que podés usar en cualquier plataforma para descargarlos y lo podés abrir con editor de textos.
Una vez has descargado todos los paquetes, los ponés en una carpeta , luego lo grabás en un pendrive y lo llevás a tu equipo , luego en este, abrís nuevamente Synaptic -->Archivo-->Añadir paquetes descargados , marcás la carpeta de los paquetes (un click- no sirve hacer doble click), luego pulsa el botón Abrir , aceptá todo y comienza la instalación de todos los paquetes y no para hasta terminar.
El proceso para instalar paquetes de programas es muy similar, solo difiere en que en Synaptic buscas y marcas todos los paquetes que querés instalar y cuando terminés este paso, recién generás el Script de descargas.
Si leiste hasta acá y entendiste lo que quise poner, te darás cuenta que la gran dificultad radica en clonar los índices de repositorios, inclusive alguien de este foro te los podría subir a Rapidshare (son unos 10 megas comprimidos), yo te los podría subir, pero uso Intrepid 64 bits , si te sirven te los subo.

Un forma práctica de descargar los paquetes que indica el Script, es usar un pendrive y allí instalas Firefox Portable y además las extensiones** DownThemAll** (gestor de descargas) y** Linkification ** (convierte texto plano en Link , entoces en la PC de descargas como ser un Xp , corres el Firefox Portable y en una ventana abierta del mismo le arrastras el Script esta operación abrirá el contenido del Script y por acción de la extensin Linkification, se marcarán todos las URLs de descargas, solo queda usar DownThemAll para proceder a las descargas.

---

### Post by gmunioz on 2009-01-24
Hola joe...:
En el ordenador que tiene conexión a Internet:
Inicia el Live CD. 
Una vez cargado el sistema, ejecuta Synaptic.
Activa todos los repositorios.
Recarga.
Instala solo una aplicación de las que requieras, con la opción solo descargar archivos, no instalar, a fin de ahorrar tiempo.
Navega con nautilus con permisos temporarios de administrador, en una terminal ejecutas:
sudo nautilus
hasta el directorio /var/cache/apt/archives
Los archivos alli existentes son los de la aplicación que instalaste y sus dependencias.
Muévelas a una memoria USB
Repite el procedimiento con todo lo que necesites, baja tambien dpkg-dev

En el ordenador con Ubuntu sin internet coloca todos archivos en un directorio para crear tu repositorio personal, siguiendo estos pasos:
Crea el directorio con nautilus o ejecutando en consola:
mkdir /home/tuusuario/repositorio
copia todos los archivos a ese directorio
No hace falta sudo, pues estas en tu directorio personal.
Crea un script, archivo de texto ejecutable, que le permitirá a los archivos .deb ser leídos por las aplicaciones de instalación, ejecuta en consola, ahora con permisos temporarios de administrador
sudo gedit /bin/autorepo
En el archivo que se abre pega este contenido:

#!/bin/bash
sudo dpkg-scanpackages repositorio /dev/null | gzip -9c> repositorio/Packages.gz
sudo dpkg-scansources repositorio /dev/null | gzip -9c> repositorio/Sources.gz

Guarda el archivo y lo conviertes en ejecutable, ejecutando:
sudo chmod +x autorepo
Este script se debe ejecutar un nivel antes del directorio repositorio, es decir estando en /home/tuusuario y no en /home/tuusuario/repositorio
ejecutas:
cd /home/tusuario/
autorepo
No hace falta aqui anteponer sudo
Con la ejecución de este script verás una salida con el listado del contenido del directorio del repositorio y crearas dos archivos dentro de ese directorio, llamados Packages.gz y Sources.gz que son los permiten la utilización de los archivos por las aplicaciones de instalación.
Este script deberás ejecutarlo cada vez que agregues archivos nuevos al directorio, en caso de nuevas versiones no hace falta borrar los antiguos, tomará los nuevos por si mismo.
A continuación solo te hace falta editar el archivo sources.list para agregar tu repositorio:
sudo gedit /etc/apt/sources.list
Agregas las líneas:

## Repositorio personal
## entre la última barra / y el nombre del directorio
## que actua como repositorio debe ir un espacio en blanco

deb file:///home/tuusuario/   repositorio/

Guarda el archivo.
Cierra gedit y la consola.
Inicia synaptic, recarga y tendrás disponibles las aplicaciones para instalar
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu ***Mad Jaunty User*

---

### Post by hatteras22 on 2009-01-27
> **joe_mza04 said:**
> Hola soy nuevo en ubuntu y no tengo internet. Y queria saber si hay alguna forma de bajar los programas completos con sus dependencias a un pendrive desde una maquina con windows y luego intalarlo en mi pc con ubuntu.



Gracias

Con AptOnCd puedes crear un cd/dvd con los paquetes y sus dependencias y poner luego añadirlo a synaptic como fuente de programa. 
Lo explico en [http://hatteras.wordpress.com/2009/01/24/](http://hatteras.wordpress.com/2009/01/24/)

---

