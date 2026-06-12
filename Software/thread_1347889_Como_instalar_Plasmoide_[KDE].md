---
title: "Como instalar Plasmoide [KDE]"
date: 2009-12-06
forum: Software
---

### Post by Mustaine666 on 2009-12-06
Bueno les comento.. quiero instalar el Customizable Weather Plasmoid..

desde [http://www.kde-look.org/content/show.php?content=98925&forumpage=15&PHPSESSID=cae](http://www.kde-look.org/content/show.php?content=98925&forumpage=15&PHPSESSID=cae) 

lo que ocurre es que no se como se instala ni que es lo que tengo que descargar.. y buscando por la web no encontre mucho que digamos..

capaz que esto es muy basico.. pero tambien puede ayudaar a otros..

desde ya espero sus respuestas muchas gracias :D :D

---

### Post by alfplayer on 2009-12-06
Si no me equivoco: ```
plasmapkg -i plasmoid.zip (es el archivo que hay que tener)
``` y después se puede agregar gráficamente.

---

### Post by Mustaine666 on 2009-12-06
alfplayer hice lo que me dijiste y me aparece

```

mofle@mofle-desktop:~$ plasmapkg -i plasma-widget cwp_0.9.15~jaunty~ppa1.tar.gz
Falló la instalación de /home/mofle/plasma-widget-cwp_0.9.15~jaunty~ppa1.tar.gz.
```

---

### Post by guillermolisi on 2009-12-06
Lo que te indicaron es valido para archivos con estructura ZIP preparados para ser agregados como plasmoide, no tarball (tar.gz).

Tenes que descomprimir el tarball y leer las instrucciones de instalacion que estan en el archivo README (en Ingles).

Se configura el entorno para luego compilar. Si hay una actualizacion de Qt, tenes que volverlo a instalar.

---

### Post by Mustaine666 on 2009-12-06
siguiendo las instrucciones

```

Installation
============

First, you need a complete build environment. You must install packages cmake, make, gcc, g++, gettext and
KDE development packages. These packages are called differently, depending on your distribution:
kde-devel on Ubuntu, task-kde4-devel on Mandriva, or similar.

mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
make install
kbuildsycoca4


```

instale todos los packages y empeze a escribir los comandos pero..

salto un problema

```
mofle@mofle-desktop:~$ cd ~/clima/build
mofle@mofle-desktop:~/clima/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/mofle/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:5 (find_package)


-- Configuring incomplete, errors occurred!
mofle@mofle-desktop:~/clima/build$ 
```


donde puede estar el error?

---

