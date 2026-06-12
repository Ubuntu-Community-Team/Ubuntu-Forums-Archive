---
title: "no puedo instalar frets on fire"
date: 2009-07-08
forum: Software
---

### Post by Nutria77 on 2009-07-08
asi es! no puedo instalar el juego frets on fire.

descargue la ultima version de la pagina oficial y se supone que tengo que abrir el archivo ejecutable dentro de la carpeta, pero al hacerle doble clik (setup.py) me sale un mensaje informandome que es un archivo ejecutable y escojo la opcion de ejecutarlo pero no pasa nada.

lo mismo con el archivo FretsOnFire.py de la carpeta /crs

tambien intente instalarlo con el gestorde añadir y quitar aplicaciones, pero solo descarga 2 de los 7 paquetes y obviamente no se instala

---

### Post by radixs on 2009-07-08
> **Nutria77 said:**
> asi es! no puedo instalar el juego frets on fire.

descargue la ultima version de la pagina oficial y se supone que tengo que abrir el archivo ejecutable dentro de la carpeta, pero al hacerle doble clik (setup.py) me sale un mensaje informandome que es un archivo ejecutable y escojo la opcion de ejecutarlo pero no pasa nada.

lo mismo con el archivo FretsOnFire.py de la carpeta /crs

tambien intente instalarlo con el gestorde añadir y quitar aplicaciones, pero solo descarga 2 de los 7 paquetes y obviamente no se instala

en la consola ejecuta:

```
sudo apt-get install fretsonfire
```

---

### Post by kamus on 2009-07-08
> **Nutria77 said:**
> asi es! no puedo instalar el juego frets on fire.

descargue la ultima version de la pagina oficial y se supone que tengo que abrir el archivo ejecutable dentro de la carpeta, pero al hacerle doble clik (setup.py) me sale un mensaje informandome que es un archivo ejecutable y escojo la opcion de ejecutarlo pero no pasa nada.

lo mismo con el archivo FretsOnFire.py de la carpeta /crs

tambien intente instalarlo con el gestorde añadir y quitar aplicaciones, pero solo descarga 2 de los 7 paquetes y obviamente no se instala

Podrias pegar la salida del error que te arroja en pantalla?

No estoy claro si la version que esta en los repo es la ultima disponible, me imagino que necesitas/quieres instalar la mas reciente?, sino podrias instalar la que esta en los repos como te dijo radixs

---

### Post by Nutria77 on 2009-07-09
ingrese el comando en la consola 
sudo apt-get install fretsonfire

pero no pude instalarlo completo
-------------------------------------------------------------------------------------

Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main libsdl-mixer1.2 1.2.6-3
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-setuptools 0.6c6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe python-opengl 3.0.0~a6-4ubuntu1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-imaging 1.1.6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire-game 1.2.451.dfsg-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire 1.2.451.dfsg-1     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb)  404 Not Found
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?
nutria@nutria-desktop:~$ apt-get update
E: No se pudo abrir el fichero de bloqueo '/var/lib/apt/lists/lock' - open (13 Permiso denegado)
E: No se pudo bloquear el directorio de listas
nutria@nutria-desktop:~$ apt-get update
E: No se pudo abrir el fichero de bloqueo '/var/lib/apt/lists/lock' - open (13 Permiso denegado)
E: No se pudo bloquear el directorio de listas
nutria@nutria-desktop:~$ sudo apt-get install fretsonfire
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  fretsonfire-game fretsonfire-songs-sectoid libsdl-image1.2 libsdl-mixer1.2
  python-imaging python-opengl python-pygame python-setuptools
Paquetes sugeridos:
  vorbis-tools python-imaging-doc python-imaging-dbg python-tk python-numpy
Paquetes recomendados
  python-ctypes
Se instalarán los siguientes paquetes NUEVOS:
  fretsonfire fretsonfire-game fretsonfire-songs-sectoid libsdl-image1.2
  libsdl-mixer1.2 python-imaging python-opengl python-pygame python-setuptools
0 actualizados, 9 se instalarán, 0 para eliminar y 282 no actualizados.
Se necesita descargar 6652kB/37,1MB de archivos.
Se utilizarán 48,7MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
AVISO: ¡No se han podido autenticar los siguientes paquetes!
  libsdl-image1.2 libsdl-mixer1.2 python-pygame python-setuptools
  python-opengl python-imaging fretsonfire-game fretsonfire-songs-sectoid
  fretsonfire
¿Instalar estos paquetes sin verificación [s/N]? s
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main libsdl-mixer1.2 1.2.6-3
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-setuptools 0.6c6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe python-opengl 3.0.0~a6-4ubuntu1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-imaging 1.1.6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire-game 1.2.451.dfsg-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire 1.2.451.dfsg-1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb)  404 Not Found
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?

---

### Post by kamus on 2009-07-09
> **Nutria77 said:**
> ingrese el comando en la consola 
sudo apt-get install fretsonfire

pero no pude instalarlo completo
-------------------------------------------------------------------------------------

Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main libsdl-mixer1.2 1.2.6-3
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-setuptools 0.6c6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe python-opengl 3.0.0~a6-4ubuntu1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-imaging 1.1.6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire-game 1.2.451.dfsg-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire 1.2.451.dfsg-1     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb)  404 Not Found
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?
nutria@nutria-desktop:~$ apt-get update
E: No se pudo abrir el fichero de bloqueo '/var/lib/apt/lists/lock' - open (13 Permiso denegado)
E: No se pudo bloquear el directorio de listas
nutria@nutria-desktop:~$ apt-get update
E: No se pudo abrir el fichero de bloqueo '/var/lib/apt/lists/lock' - open (13 Permiso denegado)
E: No se pudo bloquear el directorio de listas
nutria@nutria-desktop:~$ sudo apt-get install fretsonfire
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  fretsonfire-game fretsonfire-songs-sectoid libsdl-image1.2 libsdl-mixer1.2
  python-imaging python-opengl python-pygame python-setuptools
Paquetes sugeridos:
  vorbis-tools python-imaging-doc python-imaging-dbg python-tk python-numpy
Paquetes recomendados
  python-ctypes
Se instalarán los siguientes paquetes NUEVOS:
  fretsonfire fretsonfire-game fretsonfire-songs-sectoid libsdl-image1.2
  libsdl-mixer1.2 python-imaging python-opengl python-pygame python-setuptools
0 actualizados, 9 se instalarán, 0 para eliminar y 282 no actualizados.
Se necesita descargar 6652kB/37,1MB de archivos.
Se utilizarán 48,7MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
AVISO: ¡No se han podido autenticar los siguientes paquetes!
  libsdl-image1.2 libsdl-mixer1.2 python-pygame python-setuptools
  python-opengl python-imaging fretsonfire-game fretsonfire-songs-sectoid
  fretsonfire
¿Instalar estos paquetes sin verificación [s/N]? s
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main libsdl-mixer1.2 1.2.6-3
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-setuptools 0.6c6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe python-opengl 3.0.0~a6-4ubuntu1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main python-imaging 1.1.6-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire-game 1.2.451.dfsg-1
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe fretsonfire 1.2.451.dfsg-1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsdl-image1.2 1.2.5-3ubuntu0.1
  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.6-3_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptools/python-setuptools_0.6c6-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/p/pyopengl/python-opengl_3.0.0~a6-4ubuntu1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb](http://cl.archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.6-1_i386.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire-game_1.2.451.dfsg-1_all.deb)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb](http://cl.archive.ubuntu.com/ubuntu/pool/universe/f/fretsonfire/fretsonfire_1.2.451.dfsg-1_all.deb)  404 Not Found
E: No se pudieron obtener algunos archivos, ¿quizás deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?

Primero debes  actualizar la fuente de tus repositorios por abc motivo puede que se hayan movido algunos paquetes de ubicacion, con sudo apt-get update, si no arroja ningun error lo anterior dale con la instalacion.

---

### Post by radixs on 2009-07-09
Amigo que version de ubuntu tienes? creo que por ahi va el problema

---

### Post by Nutria77 on 2009-07-09
apesar de que aun no eh solucionado el problema, desde ya les agradesco su consideracion para leerme y tenerme pasiencia xD

por cierto mi version de ubuntu es la 7.10 Gutsy Gibbon

intente "sudo apt-get update" y tal como esperabamos ubo un problema xD

luego intente instalar frets on fire denuevo porsiacaso y nada de nada, aqui pego lo que me arojo la consola al intentar usar "sudo apt-get update"

----------------------------------------------------------------------

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-es
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-es
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-es
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-es
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy Release.gpg                             
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main Translation-es                     
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/restricted Translation-es
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe Translation-es
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/multiverse Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-es
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-es
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/restricted Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/universe Translation-es         
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy Release          
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main Packages
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main Sources     
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe Sources 
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
  404 Not Found
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe Packages                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
  404 Not Found
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  404 Not Found
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/restricted Packages             
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/universe Packages               
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/restricted Sources
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/restricted Sources
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/main Sources
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/multiverse Sources
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe Sources
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/universe Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy/multiverse Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/restricted Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/main Sources
  404 Not Found
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) gutsy-updates/restricted Sources
  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found
Imposible obtener [http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://cl.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found
Leyendo lista de paquetes... Hecho
E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

---

### Post by kamus on 2009-07-09
jjeje ya me acorde, amigo lo que pasa es que:
	
	

> End of life date

Ubuntu 7.10
	
Gutsy Gibbon
	

April 18th, 2009

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


Debes actualizar a alguna version mas reciente ;), por eso te enviara error 404 porque ya no existe soporte para esa version de ubuntu y lo mas probable es que los responsables de mantener ese mirror ya no lo hagan pues tampoco tienen obligacion de hacerlo.

---

### Post by radixs on 2009-07-09
> **kamus said:**
> jjeje ya me acorde, amigo lo que pasa es que:
    
     			 				End of life date

Ubuntu 7.10
	
Gutsy Gibbon
	

April 18th, 2009

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)



Debes actualizar a alguna version mas reciente ;), por eso no te enviara error porque ya no existe soporte para esa version de ubuntu.

Por eso lo decia... desde que vi Gutsy en lo repos.... ;)

Nutria77, tienes que pasarte a ubuntu 8.04, 8.10 o 9.04, como dijo Kamus en Abril 18th, 2009. se dijo adios s Ubuntu Gustsy Gibbon

---

### Post by Nutria77 on 2009-07-10
bingo!!! xD

actualize a la version 8.04 y pude intalarlo. lamentablemente me corrio sumamente lento.

volvi a actualizar ahora tengo la 8.10 y me corre un poco mas rapido pero sigue siendo injugable.

por cierto tengo 64 en video y un procesador pentium 4 de 2800, asi que no entiendo por que corre lento

---

### Post by pagondel on 2009-07-11
Haz intentado bajarle la resolucion al juego? desactivar compiz antes de jugar?:

```
metacity --replace
```

y para volver a activarlo:

```
compiz --replace
```

---

### Post by Nutria77 on 2009-07-12
no se de que sirve ese comando..... pero no funciono. por cierto el juego biene con la resolucion minima como pre determinado

---

### Post by radixs on 2009-07-12
> **Nutria77 said:**
> no se de que sirve ese comando..... pero no funciono. por cierto el juego biene con la resolucion minima como pre determinado

Lo que quería decir pagondel, es que si tenias compiz fusion activado realizaras el comando ```
metacity --replace
``` para activar el gestor de ventanas por defecto de Gnome, con respecto a ```
compiz --replace
``` es para volver a activar compiz ;)

---

### Post by Nutria77 on 2009-07-14
ahora entiendo... pero yaa lo habia intentado antes y no funciono.

un amigo me aconsejo que revisara si tengo instalado el driver de video......

podria ser ese el problema?

como reviso los drivers?

---

### Post by Carlos C on 2009-07-15
Escribe en el terminal:
```
lspci |grep VGA
```
Luego copia acá lo que te salga. Así sabremos qué modelo de tarjeta tienes y dependiendo de eso te podemos dar una respuesta.
Saludos.

---

