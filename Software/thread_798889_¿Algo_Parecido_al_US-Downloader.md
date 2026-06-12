---
title: "¿Algo Parecido al US-Downloader?"
date: 2008-05-18
forum: Software
---

### Post by pol666 on 2008-05-18
Estoy buscando algun Gestor de Descarga similar al Us-Downloader o al Flash-Get

Necesito algo que descargue cosas de Rapidshare o megaupload y que ejecute automaticamente un .sh que me cambia la IP.

Existe de eso en linux?

---

### Post by valucha on 2008-05-18
[COLOR="DarkOrchid"]Creo que el de Linux se llama FLASHGOT [http://www.ubuntu-es.org/index.php?q=node/13789](http://www.ubuntu-es.org/index.php?q=node/13789)[/COLOR]

---

### Post by rojojuan on 2008-05-18
> **pol666 said:**
> Estoy buscando algun Gestor de Descarga similar al Us-Downloader o al Flash-Get

Necesito algo que descargue cosas de Rapidshare o megaupload y que ejecute automaticamente un .sh que me cambia la IP.

Existe de eso en linux?

Estoy usando una extensión del Firefox que a mi me funciona bien. Se llama Downthemall.

---

### Post by clasificado on 2008-05-19
> **pol666 said:**
> similar al Us-Downloader

Nunca está de mas un poco de wine

clasificado

---

### Post by pol666 on 2008-05-19
La verdad es que no me gusta WINE.... peor supongamos que en este caso lo usara..simplmente NO ANDA.

---

### Post by Mauro22 on 2008-05-19
No lo probe muy a fondo, no se si es lo que buscas:

Downloader 4 X

Esta en los repos.

---

### Post by clasificado on 2008-05-20
> **pol666 said:**
> simplmente NO ANDA.

La vida puede no ser tan simple, amigo pol666 :lolflag:

Según los muchachos de [Wine Appdb - Universal Share Downloader]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10958") la versión número 1.3.4.9 + wine 0.9.53 funciona de toque (platinum).

Además, sin ir tan lejos, mi pc ahora está bajando de megaupload con eso ^^.

El primer consejo que puedo darte es que nos pases una pequeña descripción de la definición de "no anda".

¿Jamás se abre?
¿Jamás se abre pero te devuelve un mensaje de error?
¿Se abre y se cierra?
¿Se abre y no baja nada?
¿Se abre y baja corrupto?

Estamos para ayudar :guitar:

clasificado

---

### Post by aldeby on 2008-08-23
Using USDownloader under linux with Wine I also get a lot of archive corruption problems.

I have found a new downloader client, which perfectly works on either Linux, Windows and Mac: JDownloader [http://jdownloader.org/home_features]("http://jdownloader.org/home_features")

It perfectly supports a lot of file hosting websites and even captcha reading.

---

### Post by luks911 on 2008-08-23
> **aldeby said:**
> Using USDownloader under linux with Wine I also get a lot of archive corruption problems.

I have found a new downloader client, which perfectly works on either Linux, Windows and Mac: JDownloader [http://jdownloader.org/home_features]("http://jdownloader.org/home_features")

It perfectly supports a lot of file hosting websites and even captcha reading.

Antes de terminar de leer también iba a mencionar el Jdownloader, aunque en español :lolflag: Advierto que no lo probé. 
Y en Ubuntu-es dicen que:
> Megaupload-dl permite descargar de forma automática enlaces de Megaupload (usa Tesseract como OCR para contestar al Captcha), aunque sólo funciona desde línea de comandos, no tiene GUI:

[http://code.google.com/p/megaupload-dl/](http://code.google.com/p/megaupload-dl/)

No hay paquete DEB, hay que instalarlo a mano.

Y aquí un script shell para Rapidshare:

[http://code.google.com/p/megaupload-dl/wiki/RapidShare](http://code.google.com/p/megaupload-dl/wiki/RapidShare)

Si probás algo avisá cómo anduvo.
Saludos

---

### Post by juanman on 2008-08-23
El Jdownloader tiene una sola contra: esta hecho en java y consume mucha ram (50mb). Por lo demas es perfecto. Se agregan los links, espera los 40 seg, salta el captcha, descarga (no necesita cuenta premium), si es un rar, lo descomprime y borra los partx.rar
Es GPL3 y se actualiza rapido, directamente desde el programa. Si rapidshare o megaupload cambian el captcha, es probable q a las pocas horas haya una actualizacion q lo soluciona...

---

### Post by guisheca on 2008-08-23
Pol666 lo que buscas se llama Jdownloader y por estar escrito en java es multiplataforma. Yo lo uso a diario y es excelente. Además es software libre.
Saludos.

---

### Post by gefarion on 2008-08-25
Yo uso el USD con wine 1.0 y me anda perfecto.
Saludos.

---

### Post by pol666 on 2008-08-25
Si al final ahora anda pero desde hace unos dias que no me responde los link de rapidshare se quedan en buscando enlace :S alguien sabe?

---

### Post by pol666 on 2008-08-25
Uh que bien que anda el JDownloader, Gracias me hiciste conocer un nuevo amigo

---

### Post by sdm_cacto on 2008-08-27
Gwget es la posta para mi, q soy ex usuario ed Flashget.
Liviano, estable y con todo lo necesario.

Y por supuesto el cliente es nativo en linux

---

### Post by faktorqm on 2008-08-28
Hola, probe el Jdownloader y anda... pero gigasize no soporta :( 
la cosa es que no es que anda lento, tiene latencia muy alta, al menos en mi compu, desde que apreto un boton hasta que hace lo que hace el boton, trascurren entre 2 o 3 segundos. si minimizo y maximizo, los cambios en la ventana tardan entre 3 y 4 segundos para refrescarse. No me pasa con NINGUN programa esto, asi que queria saber que onda con otro programa. Ese Gwget es GTK? Salu2!!

---

### Post by crosssover on 2008-08-28
Yo Uso la Extension RDown para Firefox y funca a las mil maravillas, lo malo es que solo funciona con links de rapidshare

---

### Post by faktorqm on 2008-08-28
Bueno, dejo acá un mini how to de lo que tuve que hacer para compilar gwet por que no tiene paquete .deb y las bibliotecas que necesitaba para compilar no las tenia y me costo un poco encontrarlas.

bajamos el fuente de [http://ftp.gnome.org/pub/GNOME/sources/gwget/0.98/gwget-0.98.2.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/gwget/0.98/gwget-0.98.2.tar.gz) cuando termina click derecho -> extraer aqui y abrimos una consola y nos movemos a la carpeta.

Particularmente, lo que yo tuve que hacer para compilar es:

```
sudo apt-get install libgnomeui-dev libgtk2.0-dev libglade2-dev

```

luego ```
./configure
```
luego ```
make
```
luego ```
sudo make install
```

vamos a aplicaciones -> internet -> gwet download manager y listo!!

Adjunto salida de terminal:

```
[COLOR="Red"]faktorqm@the-edge:~/Escritorio/gwget-0.98.2$ sudo apt-get install libgnomeui-dev libgtk2.0-dev libglade2-dev[/COLOR]
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  openoffice.org-hyphenation-en-us dh-make
Utilice «apt-get autoremove» para eliminarlos.
Se instalarán los siguientes paquetes extras:
  libart-2.0-dev libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev
  libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgail-dev libgconf2-dev libgcrypt11-dev libglib2.0-dev libgnome-keyring-dev libgnome2-dev
  libgnomecanvas2-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev libice-dev libidl-dev libjpeg62-dev liblzo2-dev libopencdk10-dev liborbit2-dev
  libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev libsm-dev libtasn1-3-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev x11proto-composite-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
Paquetes sugeridos:
  libcairo2-doc libgail-doc libgcrypt11-doc glade glade-gnome libglib2.0-doc libgnome2-doc libgnomecanvas2-doc libgnomeui-doc gnutls-bin gnutls-doc libgtk2.0-doc
  imagemagick libpango1.0-doc
Paquetes recomendados
  orbit2
Se instalarán los siguientes paquetes NUEVOS:
  libart-2.0-dev libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev
  libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgail-dev libgconf2-dev libgcrypt11-dev libglade2-dev libglib2.0-dev libgnome-keyring-dev
  libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev libgtk2.0-dev libice-dev libidl-dev libjpeg62-dev
  liblzo2-dev libopencdk10-dev liborbit2-dev libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev libsm-dev libtasn1-3-dev
  libxcomposite-dev libxcursor-dev libxdamage-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev
  x11proto-composite-dev x11proto-damage-dev x11proto-fixes-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
0 actualizados, 61 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 12,6MB de archivos.
Se utilizarán 50,4MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Des:1 http://ar.archive.ubuntu.com hardy/main libice-dev 2:1.0.4-1 [56,0kB]
Des:2 http://ar.archive.ubuntu.com hardy/main libsm-dev 2:1.0.3-1 [24,3kB]
Des:3 http://ar.archive.ubuntu.com hardy/main x11proto-xext-dev 7.0.2-5ubuntu1 [42,2kB]
Des:4 http://ar.archive.ubuntu.com hardy/main x11proto-fixes-dev 1:4.0-2ubuntu1 [6172B]
Des:5 http://ar.archive.ubuntu.com hardy/main libxfixes-dev 1:4.0.3-2 [12,1kB]
Des:6 http://ar.archive.ubuntu.com hardy/main x11proto-composite-dev 1:0.4-2 [12,4kB]
Des:7 http://ar.archive.ubuntu.com hardy/main libxcomposite-dev 1:0.4.0-1 [14,3kB]
Des:8 http://ar.archive.ubuntu.com hardy/main x11proto-render-dev 2:0.9.3-2 [7096B]
Des:9 http://ar.archive.ubuntu.com hardy/main libxrender-dev 1:0.9.4-1 [28,5kB]
Des:10 http://ar.archive.ubuntu.com hardy/main libxcursor-dev 1:1.1.9-1 [31,0kB]                                                                                      
Des:11 http://ar.archive.ubuntu.com hardy/main x11proto-damage-dev 1:1.1.0-2build1 [9292B]                                                                            
Des:12 http://ar.archive.ubuntu.com hardy/main libxdamage-dev 1:1.1.1-3 [9682B]                                                                                       
Des:13 http://ar.archive.ubuntu.com hardy/main libxext-dev 2:1.0.3-2build1 [81,6kB]                                                                                   
Des:14 http://ar.archive.ubuntu.com hardy/main libexpat1-dev 2.0.1-0ubuntu1 [134kB]                                                                                   
Des:15 http://ar.archive.ubuntu.com hardy/main zlib1g-dev 1:1.2.3.3.dfsg-7ubuntu1 [160kB]                                                                             
Des:16 http://ar.archive.ubuntu.com hardy/main libfreetype6-dev 2.3.5-1ubuntu4 [664kB]                                                                                
Des:17 http://ar.archive.ubuntu.com hardy/main libfontconfig1-dev 2.5.0-2ubuntu3 [572kB]                                                                              
Des:18 http://ar.archive.ubuntu.com hardy/main libxft-dev 2.1.12-2ubuntu5 [60,8kB]                                                                                    
Des:19 http://ar.archive.ubuntu.com hardy/main libxi-dev 2:1.1.3-1 [69,3kB]                                                                                           
Des:20 http://ar.archive.ubuntu.com hardy/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]                                                                           
Des:21 http://ar.archive.ubuntu.com hardy/main libxinerama-dev 2:1.0.2-1build1 [10,9kB]                                                                               
Des:22 http://ar.archive.ubuntu.com hardy/main x11proto-randr-dev 1.2.1-2 [28,6kB]                                                                                    
Des:23 http://ar.archive.ubuntu.com hardy/main libxrandr-dev 2:1.2.2-1 [27,8kB]                                                                                       
Des:24 http://ar.archive.ubuntu.com hardy/main libart-2.0-dev 2.3.20-1 [64,5kB]                                                                                       
Des:25 http://ar.archive.ubuntu.com hardy-updates/main libglib2.0-dev 2.16.4-0ubuntu2 [871kB]                                                                         
Des:26 http://ar.archive.ubuntu.com hardy/main libatk1.0-dev 1.22.0-0ubuntu1 [75,4kB]                                                                                 
Des:27 http://ar.archive.ubuntu.com hardy/main libaudiofile-dev 0.2.6-7ubuntu1 [120kB]                                                                                
Des:28 http://ar.archive.ubuntu.com hardy/main libavahi-common-dev 0.6.22-2ubuntu4 [65,3kB]                                                                           
Des:29 http://ar.archive.ubuntu.com hardy-updates/main libdbus-1-dev 1.1.20-1ubuntu2 [169kB]                                                                          
Des:30 http://ar.archive.ubuntu.com hardy/main libavahi-client-dev 0.6.22-2ubuntu4 [37,2kB]                                                                           
Des:31 http://ar.archive.ubuntu.com hardy/main libavahi-glib-dev 0.6.22-2ubuntu4 [9564B]                                                                              
Des:32 http://ar.archive.ubuntu.com hardy/main libidl-dev 0.8.10-0.1 [83,8kB]                                                                                         
Des:33 http://ar.archive.ubuntu.com hardy/main liborbit2-dev 1:2.14.12-0.1 [375kB]                                                                                    
Des:34 http://ar.archive.ubuntu.com hardy/main libpopt-dev 1.10-3build1 [38,3kB]                                                                                      
Des:35 http://ar.archive.ubuntu.com hardy/main libbonobo2-dev 2.22.0-0ubuntu1 [651kB]                                                                                 
Des:36 http://ar.archive.ubuntu.com hardy/main libpixman-1-dev 0.10.0-0ubuntu1 [86,1kB]                                                                               
Des:37 http://ar.archive.ubuntu.com hardy/main libpng12-dev 1.2.15~beta5-3 [171kB]                                                                                    
Des:38 http://ar.archive.ubuntu.com hardy-updates/main libcairo2-dev 1.6.0-0ubuntu2 [592kB]                                                                           
Des:39 http://ar.archive.ubuntu.com hardy-updates/main libpango1.0-dev 1.20.5-0ubuntu1 [348kB]                                                                        
Des:40 http://ar.archive.ubuntu.com hardy-updates/main libgtk2.0-dev 2.12.9-3ubuntu4 [2781kB]                                                                         
Des:41 http://ar.archive.ubuntu.com hardy/main libxml2-dev 2.6.31.dfsg-2ubuntu1 [676kB]                                                                               
Des:42 http://ar.archive.ubuntu.com hardy/main libglade2-dev 1:2.6.2-1 [130kB]                                                                                        
Des:43 http://ar.archive.ubuntu.com hardy/main libesd0-dev 0.2.38-0ubuntu9 [22,8kB]                                                                                   
Des:44 http://ar.archive.ubuntu.com hardy/main libgconf2-dev 2.22.0-0ubuntu3 [209kB]                                                                                  
Des:45 http://ar.archive.ubuntu.com hardy/main libgpg-error-dev 1.4-2ubuntu7 [35,1kB]                                                                                 
Des:46 http://ar.archive.ubuntu.com hardy/main libgcrypt11-dev 1.2.4-2ubuntu7 [215kB]                                                                                 
Des:47 http://ar.archive.ubuntu.com hardy-updates/main libgnutlsxx13 2.0.4-1ubuntu2.1 [31,4kB]                                                                        
Des:48 http://ar.archive.ubuntu.com hardy/main liblzo2-dev 2.02-3 [139kB]                                                                                             
Des:49 http://ar.archive.ubuntu.com hardy/main libopencdk10-dev 0.6.6-1ubuntu1 [106kB]                                                                                
Des:50 http://ar.archive.ubuntu.com hardy/main libtasn1-3-dev 1.1-1 [367kB]                                                                                           
Des:51 http://ar.archive.ubuntu.com hardy-updates/main libgnutls-dev 2.0.4-1ubuntu2.1 [345kB]                                                                         
Des:52 http://ar.archive.ubuntu.com hardy/main libsepol1-dev 2.0.20-0ubuntu3 [151kB]                                                                                  
Des:53 http://ar.archive.ubuntu.com hardy/main libselinux1-dev 2.0.55-0ubuntu4 [112kB]                                                                                
Des:54 http://ar.archive.ubuntu.com hardy/main libgnomevfs2-dev 1:2.22.0-2ubuntu1 [458kB]                                                                             
Des:55 http://ar.archive.ubuntu.com hardy/main libgnome2-dev 2.22.0-0ubuntu1 [64,9kB]                                                                                 
Des:56 http://ar.archive.ubuntu.com hardy/main libgail-dev 1.22.1-0ubuntu1 [4944B]                                                                                    
Des:57 http://ar.archive.ubuntu.com hardy/main libgnomecanvas2-dev 2.20.1.1-1 [118kB]                                                                                 
Des:58 http://ar.archive.ubuntu.com hardy/main libbonoboui2-dev 2.21.90-1 [227kB]                                                                                     
Des:59 http://ar.archive.ubuntu.com hardy-updates/main libgnome-keyring-dev 2.22.2-0ubuntu1 [70,2kB]                                                                  
Des:60 http://ar.archive.ubuntu.com hardy/main libjpeg62-dev 6b-14 [188kB]                                                                                            
Des:61 http://ar.archive.ubuntu.com hardy-updates/main libgnomeui-dev 2.22.1.0-0ubuntu2 [324kB]                                                                       
Descargados 12,6MB en 2min31s (83,2kB/s)                                                                                                                              
Extrayendo plantillas para los paquetes: 100%
Seleccionando el paquete libice-dev previamente no seleccionado.
(Leyendo la base de datos ...  
90995 ficheros y directorios instalados actualmente.)
Desempaquetando libice-dev (de .../libice-dev_2%3a1.0.4-1_i386.deb) ...
Seleccionando el paquete libsm-dev previamente no seleccionado.
Desempaquetando libsm-dev (de .../libsm-dev_2%3a1.0.3-1_i386.deb) ...
Seleccionando el paquete x11proto-xext-dev previamente no seleccionado.
Desempaquetando x11proto-xext-dev (de .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Seleccionando el paquete x11proto-fixes-dev previamente no seleccionado.
Desempaquetando x11proto-fixes-dev (de .../x11proto-fixes-dev_1%3a4.0-2ubuntu1_all.deb) ...
Seleccionando el paquete libxfixes-dev previamente no seleccionado.
Desempaquetando libxfixes-dev (de .../libxfixes-dev_1%3a4.0.3-2_i386.deb) ...
Seleccionando el paquete x11proto-composite-dev previamente no seleccionado.
Desempaquetando x11proto-composite-dev (de .../x11proto-composite-dev_1%3a0.4-2_all.deb) ...
Seleccionando el paquete libxcomposite-dev previamente no seleccionado.
Desempaquetando libxcomposite-dev (de .../libxcomposite-dev_1%3a0.4.0-1_i386.deb) ...
Seleccionando el paquete x11proto-render-dev previamente no seleccionado.
Desempaquetando x11proto-render-dev (de .../x11proto-render-dev_2%3a0.9.3-2_all.deb) ...
Seleccionando el paquete libxrender-dev previamente no seleccionado.
Desempaquetando libxrender-dev (de .../libxrender-dev_1%3a0.9.4-1_i386.deb) ...
Seleccionando el paquete libxcursor-dev previamente no seleccionado.
Desempaquetando libxcursor-dev (de .../libxcursor-dev_1%3a1.1.9-1_i386.deb) ...
Seleccionando el paquete x11proto-damage-dev previamente no seleccionado.
Desempaquetando x11proto-damage-dev (de .../x11proto-damage-dev_1%3a1.1.0-2build1_all.deb) ...
Seleccionando el paquete libxdamage-dev previamente no seleccionado.
Desempaquetando libxdamage-dev (de .../libxdamage-dev_1%3a1.1.1-3_i386.deb) ...
Seleccionando el paquete libxext-dev previamente no seleccionado.
Desempaquetando libxext-dev (de .../libxext-dev_2%3a1.0.3-2build1_i386.deb) ...
Seleccionando el paquete libexpat1-dev previamente no seleccionado.
Desempaquetando libexpat1-dev (de .../libexpat1-dev_2.0.1-0ubuntu1_i386.deb) ...
Seleccionando el paquete zlib1g-dev previamente no seleccionado.
Desempaquetando zlib1g-dev (de .../zlib1g-dev_1%3a1.2.3.3.dfsg-7ubuntu1_i386.deb) ...
Seleccionando el paquete libfreetype6-dev previamente no seleccionado.
Desempaquetando libfreetype6-dev (de .../libfreetype6-dev_2.3.5-1ubuntu4_i386.deb) ...
Seleccionando el paquete libfontconfig1-dev previamente no seleccionado.
Desempaquetando libfontconfig1-dev (de .../libfontconfig1-dev_2.5.0-2ubuntu3_i386.deb) ...
Seleccionando el paquete libxft-dev previamente no seleccionado.
Desempaquetando libxft-dev (de .../libxft-dev_2.1.12-2ubuntu5_i386.deb) ...
Seleccionando el paquete libxi-dev previamente no seleccionado.
Desempaquetando libxi-dev (de .../libxi-dev_2%3a1.1.3-1_i386.deb) ...
Seleccionando el paquete x11proto-xinerama-dev previamente no seleccionado.
Desempaquetando x11proto-xinerama-dev (de .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Seleccionando el paquete libxinerama-dev previamente no seleccionado.
Desempaquetando libxinerama-dev (de .../libxinerama-dev_2%3a1.0.2-1build1_i386.deb) ...
Seleccionando el paquete x11proto-randr-dev previamente no seleccionado.
Desempaquetando x11proto-randr-dev (de .../x11proto-randr-dev_1.2.1-2_all.deb) ...
Seleccionando el paquete libxrandr-dev previamente no seleccionado.
Desempaquetando libxrandr-dev (de .../libxrandr-dev_2%3a1.2.2-1_i386.deb) ...
Seleccionando el paquete libart-2.0-dev previamente no seleccionado.
Desempaquetando libart-2.0-dev (de .../libart-2.0-dev_2.3.20-1_i386.deb) ...
Seleccionando el paquete libglib2.0-dev previamente no seleccionado.
Desempaquetando libglib2.0-dev (de .../libglib2.0-dev_2.16.4-0ubuntu2_i386.deb) ...
Seleccionando el paquete libatk1.0-dev previamente no seleccionado.
Desempaquetando libatk1.0-dev (de .../libatk1.0-dev_1.22.0-0ubuntu1_i386.deb) ...
Seleccionando el paquete libaudiofile-dev previamente no seleccionado.
Desempaquetando libaudiofile-dev (de .../libaudiofile-dev_0.2.6-7ubuntu1_i386.deb) ...
Seleccionando el paquete libavahi-common-dev previamente no seleccionado.
Desempaquetando libavahi-common-dev (de .../libavahi-common-dev_0.6.22-2ubuntu4_i386.deb) ...
Seleccionando el paquete libdbus-1-dev previamente no seleccionado.
Desempaquetando libdbus-1-dev (de .../libdbus-1-dev_1.1.20-1ubuntu2_i386.deb) ...
Seleccionando el paquete libavahi-client-dev previamente no seleccionado.
Desempaquetando libavahi-client-dev (de .../libavahi-client-dev_0.6.22-2ubuntu4_i386.deb) ...
Seleccionando el paquete libavahi-glib-dev previamente no seleccionado.
Desempaquetando libavahi-glib-dev (de .../libavahi-glib-dev_0.6.22-2ubuntu4_i386.deb) ...
Seleccionando el paquete libidl-dev previamente no seleccionado.
Desempaquetando libidl-dev (de .../libidl-dev_0.8.10-0.1_i386.deb) ...
Seleccionando el paquete liborbit2-dev previamente no seleccionado.
Desempaquetando liborbit2-dev (de .../liborbit2-dev_1%3a2.14.12-0.1_i386.deb) ...
Seleccionando el paquete libpopt-dev previamente no seleccionado.
Desempaquetando libpopt-dev (de .../libpopt-dev_1.10-3build1_i386.deb) ...
Seleccionando el paquete libbonobo2-dev previamente no seleccionado.
Desempaquetando libbonobo2-dev (de .../libbonobo2-dev_2.22.0-0ubuntu1_i386.deb) ...
Seleccionando el paquete libpixman-1-dev previamente no seleccionado.
Desempaquetando libpixman-1-dev (de .../libpixman-1-dev_0.10.0-0ubuntu1_i386.deb) ...
Seleccionando el paquete libpng12-dev previamente no seleccionado.
Desempaquetando libpng12-dev (de .../libpng12-dev_1.2.15~beta5-3_i386.deb) ...
Seleccionando el paquete libcairo2-dev previamente no seleccionado.
Desempaquetando libcairo2-dev (de .../libcairo2-dev_1.6.0-0ubuntu2_i386.deb) ...
Seleccionando el paquete libpango1.0-dev previamente no seleccionado.
Desempaquetando libpango1.0-dev (de .../libpango1.0-dev_1.20.5-0ubuntu1_i386.deb) ...
Seleccionando el paquete libgtk2.0-dev previamente no seleccionado.
Desempaquetando libgtk2.0-dev (de .../libgtk2.0-dev_2.12.9-3ubuntu4_i386.deb) ...
Seleccionando el paquete libxml2-dev previamente no seleccionado.
Desempaquetando libxml2-dev (de .../libxml2-dev_2.6.31.dfsg-2ubuntu1_i386.deb) ...
Seleccionando el paquete libglade2-dev previamente no seleccionado.
Desempaquetando libglade2-dev (de .../libglade2-dev_1%3a2.6.2-1_i386.deb) ...
Seleccionando el paquete libesd0-dev previamente no seleccionado.
Desempaquetando libesd0-dev (de .../libesd0-dev_0.2.38-0ubuntu9_i386.deb) ...
Seleccionando el paquete libgconf2-dev previamente no seleccionado.
Desempaquetando libgconf2-dev (de .../libgconf2-dev_2.22.0-0ubuntu3_i386.deb) ...
Seleccionando el paquete libgpg-error-dev previamente no seleccionado.
Desempaquetando libgpg-error-dev (de .../libgpg-error-dev_1.4-2ubuntu7_i386.deb) ...
Seleccionando el paquete libgcrypt11-dev previamente no seleccionado.
Desempaquetando libgcrypt11-dev (de .../libgcrypt11-dev_1.2.4-2ubuntu7_i386.deb) ...
Seleccionando el paquete libgnutlsxx13 previamente no seleccionado.
Desempaquetando libgnutlsxx13 (de .../libgnutlsxx13_2.0.4-1ubuntu2.1_i386.deb) ...
Seleccionando el paquete liblzo2-dev previamente no seleccionado.
Desempaquetando liblzo2-dev (de .../liblzo2-dev_2.02-3_i386.deb) ...
Seleccionando el paquete libopencdk10-dev previamente no seleccionado.
Desempaquetando libopencdk10-dev (de .../libopencdk10-dev_0.6.6-1ubuntu1_i386.deb) ...
Seleccionando el paquete libtasn1-3-dev previamente no seleccionado.
Desempaquetando libtasn1-3-dev (de .../libtasn1-3-dev_1.1-1_i386.deb) ...
Seleccionando el paquete libgnutls-dev previamente no seleccionado.
Desempaquetando libgnutls-dev (de .../libgnutls-dev_2.0.4-1ubuntu2.1_i386.deb) ...
Seleccionando el paquete libsepol1-dev previamente no seleccionado.
Desempaquetando libsepol1-dev (de .../libsepol1-dev_2.0.20-0ubuntu3_i386.deb) ...
Seleccionando el paquete libselinux1-dev previamente no seleccionado.
Desempaquetando libselinux1-dev (de .../libselinux1-dev_2.0.55-0ubuntu4_i386.deb) ...
Seleccionando el paquete libgnomevfs2-dev previamente no seleccionado.
Desempaquetando libgnomevfs2-dev (de .../libgnomevfs2-dev_1%3a2.22.0-2ubuntu1_i386.deb) ...
Seleccionando el paquete libgnome2-dev previamente no seleccionado.
Desempaquetando libgnome2-dev (de .../libgnome2-dev_2.22.0-0ubuntu1_i386.deb) ...
Seleccionando el paquete libgail-dev previamente no seleccionado.
Desempaquetando libgail-dev (de .../libgail-dev_1.22.1-0ubuntu1_i386.deb) ...
Seleccionando el paquete libgnomecanvas2-dev previamente no seleccionado.
Desempaquetando libgnomecanvas2-dev (de .../libgnomecanvas2-dev_2.20.1.1-1_i386.deb) ...
Seleccionando el paquete libbonoboui2-dev previamente no seleccionado.
Desempaquetando libbonoboui2-dev (de .../libbonoboui2-dev_2.21.90-1_i386.deb) ...
Seleccionando el paquete libgnome-keyring-dev previamente no seleccionado.
Desempaquetando libgnome-keyring-dev (de .../libgnome-keyring-dev_2.22.2-0ubuntu1_i386.deb) ...
Seleccionando el paquete libjpeg62-dev previamente no seleccionado.
Desempaquetando libjpeg62-dev (de .../libjpeg62-dev_6b-14_i386.deb) ...
Seleccionando el paquete libgnomeui-dev previamente no seleccionado.
Desempaquetando libgnomeui-dev (de .../libgnomeui-dev_2.22.1.0-0ubuntu2_i386.deb) ...
Configurando libice-dev (2:1.0.4-1) ...
Configurando libsm-dev (2:1.0.3-1) ...
Configurando x11proto-xext-dev (7.0.2-5ubuntu1) ...
Configurando x11proto-fixes-dev (1:4.0-2ubuntu1) ...
Configurando libxfixes-dev (1:4.0.3-2) ...
Configurando x11proto-composite-dev (1:0.4-2) ...
Configurando libxcomposite-dev (1:0.4.0-1) ...
Configurando x11proto-render-dev (2:0.9.3-2) ...
Configurando libxrender-dev (1:0.9.4-1) ...
Configurando libxcursor-dev (1:1.1.9-1) ...
Configurando x11proto-damage-dev (1:1.1.0-2build1) ...
Configurando libxdamage-dev (1:1.1.1-3) ...
Configurando libxext-dev (2:1.0.3-2build1) ...
Configurando libexpat1-dev (2.0.1-0ubuntu1) ...

Configurando zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Configurando libfreetype6-dev (2.3.5-1ubuntu4) ...

Configurando libfontconfig1-dev (2.5.0-2ubuntu3) ...

Configurando libxft-dev (2.1.12-2ubuntu5) ...
Configurando libxi-dev (2:1.1.3-1) ...
Configurando x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Configurando libxinerama-dev (2:1.0.2-1build1) ...
Configurando x11proto-randr-dev (1.2.1-2) ...
Configurando libxrandr-dev (2:1.2.2-1) ...
Configurando libart-2.0-dev (2.3.20-1) ...
Configurando libglib2.0-dev (2.16.4-0ubuntu2) ...
Configurando libatk1.0-dev (1.22.0-0ubuntu1) ...
Configurando libaudiofile-dev (0.2.6-7ubuntu1) ...
Configurando libavahi-common-dev (0.6.22-2ubuntu4) ...
Configurando libdbus-1-dev (1.1.20-1ubuntu2) ...
Configurando libavahi-client-dev (0.6.22-2ubuntu4) ...
Configurando libavahi-glib-dev (0.6.22-2ubuntu4) ...
Configurando libidl-dev (0.8.10-0.1) ...
Configurando liborbit2-dev (1:2.14.12-0.1) ...
Configurando libpopt-dev (1.10-3build1) ...
Configurando libbonobo2-dev (2.22.0-0ubuntu1) ...
Configurando libpixman-1-dev (0.10.0-0ubuntu1) ...
Configurando libpng12-dev (1.2.15~beta5-3) ...
Configurando libcairo2-dev (1.6.0-0ubuntu2) ...
Configurando libpango1.0-dev (1.20.5-0ubuntu1) ...
Configurando libgtk2.0-dev (2.12.9-3ubuntu4) ...
Configurando libxml2-dev (2.6.31.dfsg-2ubuntu1) ...
Configurando libglade2-dev (1:2.6.2-1) ...

Configurando libesd0-dev (0.2.38-0ubuntu9) ...
Configurando libgconf2-dev (2.22.0-0ubuntu3) ...

Configurando libgpg-error-dev (1.4-2ubuntu7) ...
Configurando libgcrypt11-dev (1.2.4-2ubuntu7) ...
Configurando libgnutlsxx13 (2.0.4-1ubuntu2.1) ...

Configurando liblzo2-dev (2.02-3) ...
Configurando libopencdk10-dev (0.6.6-1ubuntu1) ...

Configurando libtasn1-3-dev (1.1-1) ...

Configurando libgnutls-dev (2.0.4-1ubuntu2.1) ...
Configurando libsepol1-dev (2.0.20-0ubuntu3) ...
Configurando libselinux1-dev (2.0.55-0ubuntu4) ...
Configurando libgnomevfs2-dev (1:2.22.0-2ubuntu1) ...
Configurando libgnome2-dev (2.22.0-0ubuntu1) ...
Configurando libgail-dev (1.22.1-0ubuntu1) ...
Configurando libgnomecanvas2-dev (2.20.1.1-1) ...
Configurando libbonoboui2-dev (2.21.90-1) ...
Configurando libgnome-keyring-dev (2.22.2-0ubuntu1) ...
Configurando libjpeg62-dev (6b-14) ...
Configurando libgnomeui-dev (2.22.1.0-0ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[COLOR="Red"]faktorqm@the-edge:~/Escritorio/gwget-0.98.2$ ./configure[/COLOR]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.29... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... yes
checking for DBUS... configure: WARNING: DBUS support is disabled since dbus 0.33 or higher was not found
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ar bg ca cs da de el en_CA en_GB es eu fi fr hu it ja lt mk ne nl pa pl pt pt_BR ro ru rw sk sq sv tr uk vi zh_CN zh_HK zh_TW
checking which epiphany to use... no epiphany installed
checking for NOTIFY... checking for glib-genmarshal... /usr/bin/glib-genmarshal
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating pixmaps/Makefile
config.status: creating data/Makefile
config.status: creating gwget.desktop
config.status: creating epiphany-extension/Makefile
config.status: creating config.h
config.status: executing intltool commands
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
[COLOR="Red"]faktorqm@the-edge:~/Escritorio/gwget-0.98.2$ make[/COLOR]
make  all-recursive
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
Making all in po
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file ar.po
file=`echo bg | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file bg.po
file=`echo ca | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file ca.po
file=`echo cs | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file cs.po
file=`echo da | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file da.po
file=`echo de | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file de.po
file=`echo el | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file el.po
file=`echo en_CA | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file en_CA.po
file=`echo en_GB | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file en_GB.po
file=`echo es | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo eu | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file eu.po
file=`echo fi | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file fi.po
file=`echo fr | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file fr.po
file=`echo hu | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file hu.po
file=`echo it | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file it.po
file=`echo ja | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file ja.po
file=`echo lt | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file lt.po
file=`echo mk | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file mk.po
file=`echo ne | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file ne.po
file=`echo nl | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file nl.po
file=`echo pa | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file pa.po
file=`echo pl | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file pl.po
file=`echo pt | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file pt.po
file=`echo pt_BR | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file pt_BR.po
file=`echo ro | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file ro.po
file=`echo ru | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file ru.po
file=`echo rw | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file rw.po
file=`echo sk | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file sk.po
file=`echo sq | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file sq.po
file=`echo sv | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file sv.po
file=`echo tr | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file tr.po
file=`echo uk | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file uk.po
file=`echo vi | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file vi.po
file=`echo zh_CN | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file zh_CN.po
file=`echo zh_HK | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file zh_HK.po
file=`echo zh_TW | sed 's,.*/,,'`.gmo \
	  && rm -f $file && /usr/bin/msgfmt -o $file zh_TW.po
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/po'
Making all in include
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/include'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/include'
Making all in src
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
make  all-am
make[3]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" \
	  -c -o main.o `test -f 'main.c' || echo './'`main.c; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
	else rm -f ".deps/main.Tpo"; exit 1; \
	fi
./../include/main_window.h:58: aviso: se definió &#8216;dragtypes&#8217; pero no se usa
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT main_window.o -MD -MP -MF ".deps/main_window.Tpo" \
	  -c -o main_window.o `test -f 'main_window.c' || echo './'`main_window.c; \
	then mv -f ".deps/main_window.Tpo" ".deps/main_window.Po"; \
	else rm -f ".deps/main_window.Tpo"; exit 1; \
	fi
main_window.c: En la función &#8216;on_gwget_drag_received&#8217;:
main_window.c:539: aviso: el puntero que apunta en el paso del argumento 1 de &#8216;gnome_vfs_uri_list_parse&#8217; difiere en signo
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT main_window_cb.o -MD -MP -MF ".deps/main_window_cb.Tpo" \
	  -c -o main_window_cb.o `test -f 'main_window_cb.c' || echo './'`main_window_cb.c; \
	then mv -f ".deps/main_window_cb.Tpo" ".deps/main_window_cb.Po"; \
	else rm -f ".deps/main_window_cb.Tpo"; exit 1; \
	fi
./../include/main_window.h:58: aviso: se definió &#8216;dragtypes&#8217; pero no se usa
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT gwget_data.o -MD -MP -MF ".deps/gwget_data.Tpo" \
	  -c -o gwget_data.o `test -f 'gwget_data.c' || echo './'`gwget_data.c; \
	then mv -f ".deps/gwget_data.Tpo" ".deps/gwget_data.Po"; \
	else rm -f ".deps/gwget_data.Tpo"; exit 1; \
	fi
./../include/main_window.h:58: aviso: se definió &#8216;dragtypes&#8217; pero no se usa
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT wget-log.o -MD -MP -MF ".deps/wget-log.Tpo" \
	  -c -o wget-log.o `test -f 'wget-log.c' || echo './'`wget-log.c; \
	then mv -f ".deps/wget-log.Tpo" ".deps/wget-log.Po"; \
	else rm -f ".deps/wget-log.Tpo"; exit 1; \
	fi
./../include/main_window.h:58: aviso: se definió &#8216;dragtypes&#8217; pero no se usa
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" \
	  -c -o utils.o `test -f 'utils.c' || echo './'`utils.c; \
	then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; \
	else rm -f ".deps/utils.Tpo"; exit 1; \
	fi
./../include/main_window.h:58: aviso: se definió &#8216;dragtypes&#8217; pero no se usa
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT custom-cell-renderer-progressbar.o -MD -MP -MF ".deps/custom-cell-renderer-progressbar.Tpo" \
	  -c -o custom-cell-renderer-progressbar.o `test -f 'custom-cell-renderer-progressbar.c' || echo './'`custom-cell-renderer-progressbar.c; \
	then mv -f ".deps/custom-cell-renderer-progressbar.Tpo" ".deps/custom-cell-renderer-progressbar.Po"; \
	else rm -f ".deps/custom-cell-renderer-progressbar.Tpo"; exit 1; \
	fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT new_window.o -MD -MP -MF ".deps/new_window.Tpo" \
	  -c -o new_window.o `test -f 'new_window.c' || echo './'`new_window.c; \
	then mv -f ".deps/new_window.Tpo" ".deps/new_window.Po"; \
	else rm -f ".deps/new_window.Tpo"; exit 1; \
	fi
./../include/main_window.h:58: aviso: se definió &#8216;dragtypes&#8217; pero no se usa
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT eggtrayicon.o -MD -MP -MF ".deps/eggtrayicon.Tpo" \
	  -c -o eggtrayicon.o `test -f 'eggtrayicon.c' || echo './'`eggtrayicon.c; \
	then mv -f ".deps/eggtrayicon.Tpo" ".deps/eggtrayicon.Po"; \
	else rm -f ".deps/eggtrayicon.Tpo"; exit 1; \
	fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT systray.o -MD -MP -MF ".deps/systray.Tpo" \
	  -c -o systray.o `test -f 'systray.c' || echo './'`systray.c; \
	then mv -f ".deps/systray.Tpo" ".deps/systray.Po"; \
	else rm -f ".deps/systray.Tpo"; exit 1; \
	fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DGNOME_GWGET_LOCALEDIR=\""/usr/local/share/locale"\" -DDATADIR=\""/usr/local/share/gwget/"\" -I./../include    -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/libglade-2.0 -I/usr/include/gnome-vfs-module-2.0     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -MT gwget-application.o -MD -MP -MF ".deps/gwget-application.Tpo" \
	  -c -o gwget-application.o `test -f 'gwget-application.c' || echo './'`gwget-application.c; \
	then mv -f ".deps/gwget-application.Tpo" ".deps/gwget-application.Po"; \
	else rm -f ".deps/gwget-application.Tpo"; exit 1; \
	fi
/bin/bash ../libtool --mode=link gcc -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2   -o gwget   main.o main_window.o main_window_cb.o gwget_data.o wget-log.o utils.o custom-cell-renderer-progressbar.o new_window.o eggtrayicon.o systray.o gwget-application.o -lz  -pthread -Wl,--export-dynamic -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgnomevfs-2 -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0   
mkdir .libs
gcc -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes -O1 -g -g -O2 -o gwget main.o main_window.o main_window_cb.o gwget_data.o wget-log.o utils.o custom-cell-renderer-progressbar.o new_window.o eggtrayicon.o systray.o gwget-application.o -pthread -Wl,--export-dynamic  -lz /usr/lib/libgnomeui-2.so -lSM -lICE /usr/lib/libbonoboui-2.so /usr/lib/libgnomecanvas-2.so /usr/lib/libgnome-2.so /usr/lib/libpopt.so /usr/lib/libbonobo-2.so /usr/lib/libbonobo-activation.so /usr/lib/libORBit-2.so /usr/lib/libart_lgpl_2.so /usr/lib/libglade-2.0.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libxml2.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgnomevfs-2.so /usr/lib/libgconf-2.so /usr/lib/libgthread-2.0.so -lrt /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so
make[3]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
Making all in pixmaps
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/pixmaps'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/pixmaps'
Making all in data
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/data'
LC_ALL=C ../intltool-merge -s -u -c ../po/.intltool-merge-cache ../po gwget.schemas.in gwget.schemas
Generating and caching the translation database
Merging translations into gwget.schemas.
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/data'
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
[COLOR="Red"]faktorqm@the-edge:~/Escritorio/gwget-0.98.2$ sudo make install[/COLOR]
[sudo] password for faktorqm: 
Making install in po
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/po'
/home/faktorqm/Escritorio/gwget-0.98.2/install-sh -d /usr/local/share/locale
if test -n ""; then \
	  linguas=""; \
	else \
	  linguas="ar bg ca cs da de el en_CA en_GB es eu fi fr hu it ja lt mk ne nl pa pl pt pt_BR ro ru rw sk sq sv tr uk vi zh_CN zh_HK zh_TW"; \
	fi; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /home/faktorqm/Escritorio/gwget-0.98.2/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/gwget.mo; \
	    echo "installing $lang.gmo as $dir/gwget.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/gwget.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/gwget.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/gwget.mo.m; \
	    echo "installing $lang.gmo.m as $dir/gwget.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/gwget.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/gwget.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
installing ar.gmo as /usr/local/share/locale/ar/LC_MESSAGES/gwget.mo
installing bg.gmo as /usr/local/share/locale/bg/LC_MESSAGES/gwget.mo
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/gwget.mo
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/gwget.mo
installing da.gmo as /usr/local/share/locale/da/LC_MESSAGES/gwget.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gwget.mo
installing el.gmo as /usr/local/share/locale/el/LC_MESSAGES/gwget.mo
installing en_CA.gmo as /usr/local/share/locale/en_CA/LC_MESSAGES/gwget.mo
installing en_GB.gmo as /usr/local/share/locale/en_GB/LC_MESSAGES/gwget.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/gwget.mo
installing eu.gmo as /usr/local/share/locale/eu/LC_MESSAGES/gwget.mo
installing fi.gmo as /usr/local/share/locale/fi/LC_MESSAGES/gwget.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gwget.mo
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/gwget.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/gwget.mo
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/gwget.mo
installing lt.gmo as /usr/local/share/locale/lt/LC_MESSAGES/gwget.mo
installing mk.gmo as /usr/local/share/locale/mk/LC_MESSAGES/gwget.mo
installing ne.gmo as /usr/local/share/locale/ne/LC_MESSAGES/gwget.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/gwget.mo
installing pa.gmo as /usr/local/share/locale/pa/LC_MESSAGES/gwget.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/gwget.mo
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/gwget.mo
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/gwget.mo
installing ro.gmo as /usr/local/share/locale/ro/LC_MESSAGES/gwget.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/gwget.mo
installing rw.gmo as /usr/local/share/locale/rw/LC_MESSAGES/gwget.mo
installing sk.gmo as /usr/local/share/locale/sk/LC_MESSAGES/gwget.mo
installing sq.gmo as /usr/local/share/locale/sq/LC_MESSAGES/gwget.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gwget.mo
installing tr.gmo as /usr/local/share/locale/tr/LC_MESSAGES/gwget.mo
installing uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/gwget.mo
installing vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/gwget.mo
installing zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/gwget.mo
installing zh_HK.gmo as /usr/local/share/locale/zh_HK/LC_MESSAGES/gwget.mo
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/gwget.mo
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/po'
Making install in include
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/include'
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/include'
make[2]: No se hace nada para `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/local/include/gwget
mkdir -p -- /usr/local/include/gwget
 /usr/bin/install -c -m 644 main_window.h /usr/local/include/gwget/main_window.h
 /usr/bin/install -c -m 644 main_window_cb.h /usr/local/include/gwget/main_window_cb.h
 /usr/bin/install -c -m 644 gwget_data.h /usr/local/include/gwget/gwget_data.h
 /usr/bin/install -c -m 644 wget-log.h /usr/local/include/gwget/wget-log.h
 /usr/bin/install -c -m 644 utils.h /usr/local/include/gwget/utils.h
 /usr/bin/install -c -m 644 custom-cell-renderer-progressbar.h /usr/local/include/gwget/custom-cell-renderer-progressbar.h
 /usr/bin/install -c -m 644 new_window.h /usr/local/include/gwget/new_window.h
 /usr/bin/install -c -m 644 eggtrayicon.h /usr/local/include/gwget/eggtrayicon.h
 /usr/bin/install -c -m 644 systray.h /usr/local/include/gwget/systray.h
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/include'
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/include'
Making install in src
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
make  install-am
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
make[3]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
/bin/bash ../mkinstalldirs /usr/local/bin
  /bin/bash ../libtool --mode=install /usr/bin/install -c gwget /usr/local/bin/gwget
/usr/bin/install -c gwget /usr/local/bin/gwget
make[3]: No se hace nada para `install-data-am'.
make[3]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/src'
Making install in pixmaps
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/pixmaps'
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/pixmaps'
make[2]: No se hace nada para `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/local/share/gwget
mkdir -p -- /usr/local/share/gwget
 /usr/bin/install -c -m 644 gwget.xpm /usr/local/share/gwget/gwget.xpm
 /usr/bin/install -c -m 644 gwget.png /usr/local/share/gwget/gwget.png
 /usr/bin/install -c -m 644 gwget-off.png /usr/local/share/gwget/gwget-off.png
 /usr/bin/install -c -m 644 gwget-large.png /usr/local/share/gwget/gwget-large.png
 /usr/bin/install -c -m 644 downloading.png /usr/local/share/gwget/downloading.png
 /usr/bin/install -c -m 644 newdownload.png /usr/local/share/gwget/newdownload.png
/bin/bash ../mkinstalldirs /usr/local/share/pixmaps
mkdir -p -- /usr/local/share/pixmaps
 /usr/bin/install -c -m 644 gwget.png /usr/local/share/pixmaps/gwget.png
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/pixmaps'
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/pixmaps'
Making install in data
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/data'
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2/data'
make[2]: No se hace nada para `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule gwget.schemas
Esquema «/schemas/apps/gwget2/convert_links» adjuntado a la clave «/apps/gwget2/convert_links»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/convert_links» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/default_height» adjuntado a la clave «/apps/gwget2/default_height»
Instalado el esquema «/schemas/apps/gwget2/default_height» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/default_width» adjuntado a la clave «/apps/gwget2/default_width»
Instalado el esquema «/schemas/apps/gwget2/default_width» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/dl_page_requisites» adjuntado a la clave «/apps/gwget2/dl_page_requisites»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/dl_page_requisites» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/download_dir» adjuntado a la clave «/apps/gwget2/download_dir»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/download_dir» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/ask_save_each_dl» adjuntado a la clave «/apps/gwget2/ask_save_each_dl»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/ask_save_each_dl» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/follow_relative» adjuntado a la clave «/apps/gwget2/follow_relative»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/follow_relative» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/limit_speed» adjuntado a la clave «/apps/gwget2/limit_speed»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/limit_speed» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» adjuntado a la clave «/apps/gwget2/limit_simultaneousdownloads»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/limit_simultaneousdownloads» para la configuración regional «sv»
Esquema «/schemas/apps/gwget2/max_depth» adjuntado a la clave «/apps/gwget2/max_depth»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/max_depth» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/max_speed» adjuntado a la clave «/apps/gwget2/max_speed»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/max_speed» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/max_simultaneousdownloads» adjuntado a la clave «/apps/gwget2/max_simultaneousdownloads»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/max_simultaneousdownloads» para la configuración regional «sv»
Esquema «/schemas/apps/gwget2/n_downloads» adjuntado a la clave «/apps/gwget2/n_downloads»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/n_downloads» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/no_create_directories» adjuntado a la clave «/apps/gwget2/no_create_directories»
Instalado el esquema «/schemas/apps/gwget2/no_create_directories» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/num_retrys» adjuntado a la clave «/apps/gwget2/num_retrys»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/num_retrys» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/position_x» adjuntado a la clave «/apps/gwget2/position_x»
Instalado el esquema «/schemas/apps/gwget2/position_x» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/position_y» adjuntado a la clave «/apps/gwget2/position_y»
Instalado el esquema «/schemas/apps/gwget2/position_y» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/resume_at_start» adjuntado a la clave «/apps/gwget2/resume_at_start»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/resume_at_start» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/open_after_dl» adjuntado a la clave «/apps/gwget2/open_after_dl»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/open_after_dl» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/view_actual_size» adjuntado a la clave «/apps/gwget2/view_actual_size»
Instalado el esquema «/schemas/apps/gwget2/view_actual_size» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/view_down_speed» adjuntado a la clave «/apps/gwget2/view_down_speed»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/view_down_speed» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/view_elapse_time» adjuntado a la clave «/apps/gwget2/view_elapse_time»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/view_elapse_time» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/view_percentage» adjuntado a la clave «/apps/gwget2/view_percentage»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/view_percentage» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/view_rem_time» adjuntado a la clave «/apps/gwget2/view_rem_time»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/view_rem_time» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/view_toolbar» adjuntado a la clave «/apps/gwget2/view_toolbar»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/view_toolbar» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/view_statusbar» adjuntado a la clave «/apps/gwget2/view_statusbar»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_statusbar» para la configuración regional «sv»
Esquema «/schemas/apps/gwget2/view_total_size» adjuntado a la clave «/apps/gwget2/view_total_size»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «de»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «fi»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «zh_TW»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «C»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «es»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «vi»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «zh_HK»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «en_CA»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «ne»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «eu»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «zh_CN»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «sq»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «cs»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «el»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «it»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «pl»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «uk»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «bg»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «en_GB»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «pt_BR»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «da»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «ar»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «hu»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «ca»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «fr»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «nl»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «sk»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «sv»
Instalado el esquema «/schemas/apps/gwget2/view_total_size» para la configuración regional «lt»
Esquema «/schemas/apps/gwget2/network_mode» adjuntado a la clave «/apps/gwget2/network_mode»
Instalado el esquema «/schemas/apps/gwget2/network_mode» para la configuración regional «C»
Esquema «/schemas/apps/gwget2/http_proxy» adjuntado a la clave «/apps/gwget2/http_proxy»
Instalado el esquema «/schemas/apps/gwget2/http_proxy» para la configuración regional «c»
Esquema «/schemas/apps/gwget2/http_proxy_port» adjuntado a la clave «/apps/gwget2/http_proxy_port»
Instalado el esquema «/schemas/apps/gwget2/http_proxy_port» para la configuración regional «c»
Esquema «/schemas/apps/gwget2/proxy_uses_auth» adjuntado a la clave «/apps/gwget2/proxy_uses_auth»
Instalado el esquema «/schemas/apps/gwget2/proxy_uses_auth» para la configuración regional «c»
Esquema «/schemas/apps/gwget2/proxy_user» adjuntado a la clave «/apps/gwget2/proxy_user»
Instalado el esquema «/schemas/apps/gwget2/proxy_user» para la configuración regional «c»
Esquema «/schemas/apps/gwget2/proxy_password» adjuntado a la clave «/apps/gwget2/proxy_password»
Instalado el esquema «/schemas/apps/gwget2/proxy_password» para la configuración regional «c»
/bin/bash ../mkinstalldirs /usr/local/share/gwget
 /usr/bin/install -c -m 644 about.glade /usr/local/share/gwget/about.glade
 /usr/bin/install -c -m 644 newdownload.glade /usr/local/share/gwget/newdownload.glade
 /usr/bin/install -c -m 644 preferences.glade /usr/local/share/gwget/preferences.glade
 /usr/bin/install -c -m 644 gwget.glade /usr/local/share/gwget/gwget.glade
/bin/bash ../mkinstalldirs /usr/local/etc/gconf/schemas
mkdir -p -- /usr/local/etc/gconf/schemas
 /usr/bin/install -c -m 644 gwget.schemas /usr/local/etc/gconf/schemas/gwget.schemas
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/data'
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2/data'
make[1]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
make[2]: se ingresa al directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
make[2]: No se hace nada para `install-exec-am'.
/bin/bash ./mkinstalldirs /usr/local/share/applications
 /usr/bin/install -c -m 644 gwget.desktop /usr/local/share/applications/gwget.desktop
make[2]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
make[1]: se sale del directorio `/home/faktorqm/Escritorio/gwget-0.98.2'
[COLOR="Red"]faktorqm@the-edge:~/Escritorio/gwget-0.98.2$[/COLOR]
```

Espero que les haya servido. Salu2!

---

### Post by guisheca on 2008-08-29
Perdón si me perdí de algo, pero apostaría una fuerte suma de dinero a que Gwget se encuentra en los repositorios de ubuntu, no se con que objetivo se dan las instrucciones para compilarlo mas arriba. Es un GUI para el querido y poderoso wget y no creo que sirva para lo que pide pol666, que al parecer necesita algo para descargar de forma automática desde servicios de hosting.

---

### Post by faktorqm on 2008-08-29
Si yo pense que no estaba pero esta en los repos...

sdm_cacto: por que recomendaste ese programa si no tiene nada que ver con el tema del post original? Salu2!

---

