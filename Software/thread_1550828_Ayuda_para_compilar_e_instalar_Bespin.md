---
title: "Ayuda para compilar e instalar Bespin"
date: 2010-08-11
forum: Software
---

### Post by matias_tati on 2010-08-11
Intento instalar y compilar Bespin siguiwndo este tutorial que enmcontre [http://ubuntulife.wordpress.com/2008/12/22/instalando-bespin-kde-theme/](http://ubuntulife.wordpress.com/2008/12/22/instalando-bespin-kde-theme/)
pero me tira el sig error:

```
matias@matias-desktop:~/cloudcity$ ./configure 


==================== Bespin interactive configuration ====================

    Seems you have cmake.
    In addition to the style, you can have a KWin decoration,
    a mac-like menu plasmoid and config plugins IFF you have KDE....

--> Do you want to compile with KDE support? [Y/n]
-- The CXX compiler identification is GNU         
-- Check for working CXX compiler: /usr/bin/c++   
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info                      
-- Detecting CXX compiler ABI info - done               
-- WARNING: *** ARGB windows are experimental, performance might suffer ***
-- Found X11: /usr/lib/libX11.so                                           
-- WARNING: *** KDE4 not found, just the style will be built ***           
-- Looking for Q_WS_X11                                                    
-- Looking for Q_WS_X11 - found                                            
-- Looking for Q_WS_WIN                                                    
-- Looking for Q_WS_WIN - not found.                                       
-- Looking for Q_WS_QWS                                                    
-- Looking for Q_WS_QWS - not found.                                       
-- Looking for Q_WS_MAC                                                    
-- Looking for Q_WS_MAC - not found.                                       
-- Found Qt-Version 4.5.2                                                  
-- INFO: XRender was found - kwin deco & FX via GPU available!             
CMake Error at blib/CMakeLists.txt:42 (install):                           
  install TARGETS given no LIBRARY DESTINATION for shared library target   
  "QtBespin".                                                              


CMake Warning (dev) at config/CMakeLists.txt:12 (add_executable):
  Policy CMP0002 is not set: Logical target names must be globally unique.
  Run "cmake --help-policy CMP0002" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!
matias@matias-desktop:~/cloudcity$ cmake_policy
cmake_policy: command not found
matias@matias-desktop:~/cloudcity$ cmake --help-policy CMP0002
cmake version 2.6-patch 4

```

Gracias

---

### Post by guillermolisi on 2010-08-11
Tenes instalado KDE 4 ?

El primer error, origen de lo que sigue despues, es que estan faltando componentes de KDE 4 que se supone estarian si usas KDE 4. Encuentra Qt 4.5 pero no se si Bespin esta preparado para trabajar con KDE 4.5 (que acaba de salir esta semana en su version final).

---

### Post by pol666 on 2010-08-11
Bespin anda muy bien en KDE 4.5 de hecho la última versión de svn debería andar mejor ahí más que nada.

Tenés que que tener build-essentials, kdebase-dev, kdelibs-dev qmake, cmake, y creo que nada más, yo nunca me acuerdo y estoy un tiempo para compilarlo porque me olvido jaj-

---

### Post by matias_tati on 2010-08-11
[[img]http://j.imagehost.org/t/0490/instant_nea1.jpg[/img]](http://j.imagehost.org/view/0490/instant_nea1)

---

### Post by matias_tati on 2010-08-11
Ahora si ya no me tira error

Pero cuando ingreso make me dice lo siguiente:

```
matias@matias-desktop:~$ cd cloudcity
matias@matias-desktop:~/cloudcity$ ./configure


==================== Bespin interactive configuration ====================

    Seems you have cmake.
    In addition to the style, you can have a KWin decoration,
    a mac-like menu plasmoid and config plugins IFF you have KDE....

--> Do you want to compile with KDE support? [Y/n]
-- Found Qt-Version 4.5.2 (using /usr/bin/qmake)  
-- Found X11: /usr/lib/libX11.so                  
-- Looking for include files CMAKE_HAVE_PTHREAD_H 
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads                
-- Looking for pthread_create in pthreads - not found    
-- Looking for pthread_create in pthread                 
-- Looking for pthread_create in pthread - found         
-- Found Threads: TRUE                                   
-- Found Automoc4: /usr/bin/automoc4                     
-- Found Perl: /usr/bin/perl
-- Phonon Version: 4.3.1
-- Found Phonon: /usr/lib/libphonon.so
-- Found Phonon Includes: /usr/include/qt4/KDE;/usr/include/qt4
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Failed
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.3 include dir: /usr/include
-- Found KDE 4.3 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- WARNING: *** ARGB windows are experimental, performance might suffer ***
-- Found X11: /usr/lib/libX11.so
-- INFO: XRender was found - kwin deco & FX via GPU available!
-- KWin headers found
-- Configuring done
-- Generating done
-- Build files have been written to: /home/matias/cloudcity/build

Configuration succeeded...

--> Do you want to run a cmake GUI to adjust the configuration? [y/N]
./configure: línea 64: ccmake: orden no encontrada


========================= Configuration done ============================

   Ok, now just "cd build", "make" and "sudo make install"...


matias@matias-desktop:~/cloudcity$ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
matias@matias-desktop:~/cloudcity$ sudo make
[sudo] password for matias:
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
matias@matias-desktop:~/cloudcity$

```



Solucionado antes de hacer make hay que entrar en la carpeta build con un

```
cd build 
```

---

