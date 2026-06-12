---
title: "jUploadr"
date: 2009-10-13
forum: Software
---

### Post by facurdo on 2009-10-13
Descubri este programita hace poco para subir una buena cantidad de fotos a flickr zoomr y no recuerdo cual mas.

Lo descargue y lo instale, pero al crear un lanzador no me abre :(

Pasos que segui
Descarga
> wget [http://ufpr.dl.sourceforge.net/sourceforge/juploadr/jUploadr-1.1.2-linuxGTK-i386.tar.gz](http://ufpr.dl.sourceforge.net/sourceforge/juploadr/jUploadr-1.1.2-linuxGTK-i386.tar.gz)Extraer
> tar xfv jUploadr-1.1.2-linuxGTK-i386.tar.gzMuevo a la carpets opt
> sudo cp --recursive  jUploadr-1.1.2-linuxGTK-i386 /opt/jUploadrCreo un lanzador en el escritorio y le pongo como nombre  jUploadr y de comando /opt/jUploadr/jUploadr

Despues de ahi intento abrir el lanzador en mi escritorio pero nada.
Me mande una macana en el proceso?

---

### Post by EnriqueK on 2009-10-14
Empecemos de nuevo con otro método
Antes instalá  el paquete **unp **(unpack), de trata de un descompresor que soporta a todos los copresores que tengas instalado.
**sudo apt-get install unp**
Los pasos siguientes serían
1.- Abrí terminal y ponés 
cd /opt
el terminal quedará abierto en /opt
2.- en ese mismo terminal ponés **sudo unp** dejas un espacio, arrastras al terminal el archivo comprimido que has bajado--> Enter y ya tendrás la carpeta del programa descomprimida en el directorioirectorio /opt.
3.- Al programa lo vas a poder ejecutar poiendo en terminal **bash** dejas un espacio , navegás gráficamente y arrastras al terminal el archivo o script jUploadr --> Enter y ya.
4.- Para crear un lanzador, pone como ruta lo que te da el paso anterior antes de pulsar Enter.

---

### Post by ramiro_md on 2009-10-14
Probá haciendo esto (me sirvió con Songbird en Debian):
1)Descromprimimos en /opt:
```
sudo tar -xvzf jUploadr-1.1.2-linuxGTK-i386.tar.gz  -C /opt/ 
```
2)Damos permisos a /opt/jUploadr:
```
sudo chmod -R 777 /opt/jUploadr 
```
3)Agregamos el icono al menú:
```
sudo gedit /usr/share/applications/jUploadr.desktop
``` 
Agregamos esto al archivo en blanco que se abrió:
> [Desktop Entry]
Name=jUploadr
Comment=Gestor de subidas
Exec=/opt/jUploadr/songbird
Icon=/opt/jUploadr/songbird.png
Terminal=false
Type=Application
Categories=Application;Gráficos; 
Guardás y cerrás. 
Con esto debería andar.

NOTA: Puede que la carpeta descomprimida en /opt no se llame "uPloadr"..pero es a modo de ejemplo jeje.

Un saludo y suerte !

---

