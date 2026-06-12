---
title: "¿ Como Configurar e instalar stereophonic-to-binaural DSP (plugin para Qmmp?"
date: 2010-10-04
forum: Software
---

### Post by facucampeon on 2010-10-04
[SIZE=4]He instalado el reproductor de música Qmmp (que es similar al Winamp de windows) y funciona excelente. Pero no se como instalar el DSP que figura en el titulo del post y otros plugins. [/SIZE]


En la captura de la página de internet esta habilitado.

[IMG]http://qmmp.ylsoftware.com/images/qmmp_settings_full.png[/IMG]


[http://sourceforge.net/projects/bs2b/](http://sourceforge.net/projects/bs2b/)

[http://qmmp.ylsoftware.com/index_en.php](http://qmmp.ylsoftware.com/index_en.php)

---

### Post by sys.adm.og on 2010-10-05
Buenas como estas! Como realizaste tu instalación?
En que distro de ubuntu lo has hecho?:P

---

### Post by facucampeon on 2010-10-05
hola, para instalarlo use ubuntu 10.04 lucid lynx y instale la nueva versión 0.4.2 actualizandolo desde synaptic agregando las fuentes
[COLOR=Red]
**[http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu](http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu)**
**[COLOR=Blue]http://ppa.launchpad.net/stiff.ru/qmmp-svn/ubuntu[/COLOR]**[/COLOR]

, ahí me aparecio para habilitar el plugin en el programa. 

luego de que se instalo apareció este error y el plug in no aparece.
También me gustaría que me dijeras como instalar farsight para amsn

---

### Post by sys.adm.og on 2010-10-05
Justamente ahi en tu imagen si te fijas en la linea donde dice:
```

dpkg: problemas de dependencias impiden la configuracion de libqmm-misc:
libqmmp-misc depende de libbs2b3; sin embargo
El paquete `libbs2b3' no esta instalado
```
Eso quiere decir que no se puede instalar porque le falta una dependencia al paquete.

Yo hice la prueba pero yo me baje el tarball de los links que diste. 
Yo lo hice desde una terminal. Te recomiendo que la uses:guitar:

El problema que se me presentó cuando intente instalar en mi ubuntu 10.04 fue el siguiente: 
Cuando descomprimes la libreria libbs2b-3.1.0.tar.gz ```
tar vfxz libbs2b-3.1.0.tar.gz  
```
Luego al ingresar a la carpeta descompresa
```
cd libbs2b-3.1.0
./configure
``` **configure** este script se encarga de configurar y verificar las dependencias de un paquete para su instalación correcta y **./** es para ejecutarlo, al ejecutarlo en la ultima linea presenta este error

```
configure: error: Please install libsndfile.
```

entonces busque la libreria que me faltaba ```
aptitude search libsndfile
```

```
root@osmarpc28:/home/osmar/Documentos/paquetes/probar/qmmp/libbs2b-3.1.0# aptitude search libsndfile
v libsndfiledev                                                       
i libsndfile1          - Biblioteca para leer/escribir archivos de audio    
**p libsndfile1-dev      - Archivos de desarrollo para libsndfile**
p mffm-libsndfilew-dev 
```
OBS: '**i**' significa que esta instalado el paquete y '**p**' que no esta instalado

Instalé la librería libsndfile1-dev ```
apt-get install libsndfile1-dev
```


Al finalizar la instalación, ya podrás proseguir normalmente. A no ser que te necesites otra librería mas entonces debes instalarla hasta que no te genere errores.
```
./configure
make
make install
```

Aclaro que no justamente a ti te faltaría la misma librería pero usualmente los problemas suelen ser por eso. Por falta de alguna libreria! :D

Si necesitas ayuda para la instalacion, no dudes en pedir!

---

### Post by facucampeon on 2010-10-06
hola, gracias ya solucione el problema. 

facundo@facundo-desktop:~$```
[COLOR=Red] sudo gedit /etc/apt/sources.list[/COLOR]
```agregue estas lineas y volví a instalar el qmmp. Anduvo el plug in
```

[B][COLOR=Red]deb [http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu](http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu) lucid main

deb-src [http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu](http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu) lucid main[/COLOR][/B]

```Ahora el problema que tengo es al instalar farsight para el Amsn, no me deja. A la instalacion la hice como dice este tutorial [http://infoinf.wordpress.com/2009/04/15/howto-amsn-con-plugins-videollamada-y-extras-en-deb/](http://infoinf.wordpress.com/2009/04/15/howto-amsn-con-plugins-videollamada-y-extras-en-deb/) y al ejecutar el comando:

```
[COLOR=Lime]**sudo apt-get install build-essential libgstreamer0.10-0  gstreamer0.10-plugins-base gstreamer0.10-plugins-good  gstreamer0.10-plugins-bad gstreamer0.10-plugins-farsight  gstreamer0.10-tools gstreamer0.10-alsa libnice0 libnice-dev  libgstfarsight0.10-0 libgstfarsight0.10-dev**[/COLOR]
```me dio este error:

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
fijado build-essential como instalado manualmente.
libgstreamer0.10-0 ya está en su versión más reciente.
gstreamer0.10-plugins-base ya está en su versión más reciente.
gstreamer0.10-tools ya está en su versión más reciente.
gstreamer0.10-alsa ya está en su versión más reciente.
libnice0 ya está en su versión más reciente.
libnice-dev ya está en su versión más reciente.
libgstfarsight0.10-0 ya está en su versión más reciente.
libgstfarsight0.10-dev ya está en su versión más reciente.
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  gstreamer0.10-plugins-bad: Entra en conflicto: gstreamer0.10-plugins-farsight
  gstreamer0.10-plugins-farsight: Depende: libjinglebase0.3-0 pero no es instalable
                                  Depende: libjinglep2p0.3-0 pero no es instalable
E: Paquetes rotos


```

---

### Post by sys.adm.og on 2010-10-06
Te consulto algo te agregó la clave gpg?

---

### Post by facucampeon on 2010-10-06
despues de actualizar me dijo esto, pero no se si tendra que ver:

> 
Descargados 317B en 3s (79B/s)
Leyendo lista de paquetes... Hecho
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY F64E8F960C48D1BF

---

### Post by sys.adm.og on 2010-10-07
Visita esta pagina alli encontraras un toturial acerca de las claves GPG [URL="http://www.ubuntu-es.org/index.php?q=node/109882"]http://www.ubuntu-es.org/index.php?q=node/109882
[/URL]

Despues de conseguir la clave GPG prueba a ver si puedes o no instalar!

Avisanos si te funciona!:)

---

### Post by facucampeon on 2010-10-07
no lo pude instalar pero instale las dependencias y me dio este error

> No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
**[COLOR=Red]  gstreamer0.10-plugins-bad: Entra en conflicto: gstreamer0.10-plugins-farsight[/COLOR]**
E: Paquetes rotos


---

### Post by sys.adm.og on 2010-10-08
Primero prueba escribiendo en tu terminal lo siguiente

```
sudo apt-get -f install
```
Esto intenta cumplir las dependencias icumplidas en el sistema sino te instala asi proba con esto.

Instalando este primero y despues el otro paquete
gstreamer0.10-plugins-bad

gstreamer0.10-plugins-farsight

Dime que resultado te da!

---

### Post by facucampeon on 2010-10-08
hola, se instalaron los paquetes pero el plugin no funciona me dice esto:

[[img]http://b.imagehost.org/t/0816/Pantallazo-Asistente_de_audio_y_v_deo.jpg[/img]](http://b.imagehost.org/view/0816/Pantallazo-Asistente_de_audio_y_v_deo)

---

### Post by sys.adm.og on 2010-10-09
Y recordaste pasarle esta instruccion luego de instalarlo
```
sudo apt-get build-dep gstreamer0.10-plugins-farsight
```

---

### Post by facucampeon on 2010-10-10
```
> facundo@facundo-desktop:~$ sudo apt-get build-dep gstreamer0.10-plugins-farsight[sudo] password for facundo: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar un paquete de fuentes para gstreamer0.10-plugins-farsight

```

pase esta instrucción después de instalar los paquetes y me dio ese error. A vos te anduvo?.:confused::confused::confused:

---

### Post by sys.adm.og on 2010-10-10
Recuerdas que ese paquete no se podia instalar por falta de dependencias?
```
apt-get build-dep <paquete>
```
No instala el paquete sino sus dependencias!!!!
Una consulta solo ese paquete te falta instalar no?

Si ya instalaste todos los demas te paso el link para que descargues el paquete gstreamer-plugis-farsight

[http://py.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-farsight/gstreamer0.10-plugins-farsight_0.12.10-2_i386.deb](http://py.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-farsight/gstreamer0.10-plugins-farsight_0.12.10-2_i386.deb)

y si tenes amd

[http://py.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-farsight/gstreamer0.10-plugins-farsight_0.12.10-2_amd64.deb](http://py.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-farsight/gstreamer0.10-plugins-farsight_0.12.10-2_amd64.deb)

---

### Post by facucampeon on 2010-10-11
los ejecute y me da error con las dependencias:confused:

---

### Post by sys.adm.og on 2010-10-12
Como te habia preguntado ese era el unico paquete que te falta no?

Hagamos lo siguiente:
Primero tu procesador es intel o amd?
Bueno digamos que es intel vamos a usar [http://py.archive.ubuntu.com/ubuntu/....10-2_i386.deb](http://py.archive.ubuntu.com/ubuntu/....10-2_i386.deb)

lo descargar y lo guardaste en tu escritorio.
Entra a una terminal y has lo siguiente:
```
cd /home/$USER/Escritorio/
sudo dpkg -i gstreamer0.10-plugins-farsight_0.12.10-2_i386.deb
```

Como resultado va dar error por falta de dependencias y a continuacion has esto:
```
sudo apt-get -f install
```
y ahi ya tendria que estar instalandote el paquete y sus dependencias.

Avisa que resultado da y trata de copiar el contenido de la terminal en el caso de error  para ver cual seria el problema!

---

