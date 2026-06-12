---
title: "Actualizar versión de VLC en Ubuntu 10.04"
date: 2011-04-01
forum: Software
---

### Post by mecdem on 2011-04-01
Equipo: Toshiba Satellite A105-S4384
Sistema: Ubuntu 10.04 (32 bits)
__________

Hola amigos.

Previo
No pude hacer que el botón "Check if Already Posted" me hiciera caso. Si lo que consulto está ya en otro hilo, por favor dejarme el enlace.
__________

Consulta
Al querer actualizar, una ventana me informa esto:
[I]
Imposible obtener [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/I]

Me dispuse a buscar algún howto como ayuda pero antes revisé la URL indicada en el aviso, comenzando por [http://ppa.launchpad.net/](http://ppa.launchpad.net/)
En el directorio c-korn, que en la URL está seguido por /vlc, no hay un subdirectorio con ese nombre, y sí dos denominados
/ppa
/ubuntu

No sé cómo seguir.
¿Me guían, por favor?

Gracias y saludos.
MEC

---

### Post by guillermolisi on 2011-04-01
MEC

Cambio la estructura del ppa y, ademas, no posee paquetes para VLC.
Si queres confirmarlo por tu propia cuenta, apunta a [http://ppa.launchpad.net/c-korn/ubuntu/dists/lucid/main/binary-i386/](http://ppa.launchpad.net/c-korn/ubuntu/dists/lucid/main/binary-i386/) (fijate que no esta mas el subdirectorio VLC que existia antes. El archivo Packages posee la lista de paquetes incluidos en el repo).

Para actualizar VLC y otros paquetes, para MM, utilizo los de [GetDeb]("http://www.getdeb.net/updates/Ubuntu/10.10#how_to_install")

Tambien hay para Lucid, pero no se si incluyen VLC.

---

### Post by mecdem on 2011-04-10
Hola Guillermo.
Mil disculpas por mi tardanza en informarte cómo me fue con tu respuesta y agradecerte tu ayuda.

No dije en el inicio de la consulta -porque quería despejar las cosas de a una por vez- que a lo que quería llegar era a una nueva instalación del VLC instalado, versión 1.0.6, que estaba con problemas hasta hace poco inéditos (es un fierro ese programita).

Seguí las instrucciones, con GetDeb volví a instalar VLC... y todo siguió igual. ¿Qué pasaba? Que GetDeb me instalaba la misma versión que tenía antes, 1.0.6, la que al parecer es la que se instala por defecto sobre Ubuntu 10.04. Y no hay manera de actualizar la versión desde los repositorios.

Haciendo algunas búsquedas llegué a [http://www.ubuntugeek.com/how-to-install-vlc-1-1-4-in-ubuntu-10-04-new-ppa.html]("http://www.ubuntugeek.com/how-to-install-vlc-1-1-4-in-ubuntu-10-04-new-ppa.html") que me ofreció el titulito *"Install VLC 1.1.4 in ubuntu 10.04"*.

Las instrucciones fueron:
Open the terminal and run the following commands
sudo add-apt-repository ppa:lucid-bleed/ppa
sudo apt-get update
sudo apt-get install vlc

Ejecuté estas líneas y ¡voilá!
Pero, además, con un valor agregado:
Synaptics me informa que la versión instalada es 1.1.8-2
Y está funcionando perfecta.
__________

En cuanto al mensaje que mencioné en el primer post de la consulta -que seguía apareciendo-, fuí a Sistema>Administración>Orígenes del Software, solapa Otro Software y quité la línea molesta.
__________

Antes de poner el "Solved" te pregunto:
En realidad el título de esta consulta termina no siendo indicativo del contenido, o sea que alguien con un problema similar no la va a encontrar. Sería mejor "Actualizar versión de VLC en Ubuntu 10.04"
¿Se puede cambiar el título?

---

### Post by guillermolisi on 2011-04-10
Hechos los cambios en el thread.

Me alegro que tengas el tema resuelto :)

---

### Post by biale on 2011-04-10
En tren de probar novedades, comento que hay un VLC (dev) 1.2.0

Lo interesante es (1) que es una aplicación "portable", no se instala. Solamente se baja y se ejecuta desde una consola. Y no afecta al resto del sistema, que seguira con el 1.1.8-2 que ya esta instalado.

y (2) que se trata de uns aplicación "portable/Linux" y NO una aplicación "portable/Windows/wine".

Hasta ahora y bajo Lucid, esta funcionando bien. La idea salio desde aqui:
[http://elsoftwarelibre.wordpress.com/2010/10/18/vlc-1-2-0-dev-portable-listo-para-probar/](http://elsoftwarelibre.wordpress.com/2010/10/18/vlc-1-2-0-dev-portable-listo-para-probar/)

---

