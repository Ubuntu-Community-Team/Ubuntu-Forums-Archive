---
title: "Problemas con Smile"
date: 2010-01-04
forum: Software
---

### Post by Chogogo on 2010-01-04
Hola

Estoy usando ubuntu 9.04. Estuve usando Smile hasta hace algunos dias sin problemas. Depronto simplemente se cerraba luego de 3 segundos de abrirlo. Probe Instalarlo de de nuevo, probe instalandolo bajo el escritorio KDE...con el mismo resultado. Luego probe instalando una nueva version y la misma cosa.

Esta es la salida cuando lo corro desde terminal:

omar@Hogar:~$ smile

YOUR LANGUAGE : "es_ES"
LOCALE : "es"
"LOADING LANGUAGE ... smile_es"
SYSTEM OVERLAY : false
DIRECT RENDERING : TRUE
DOUBLE BUFFERING : TRUE
OPENGL SUPPORT : TRUE
OPENGL VERSION : 4223
Exepción de coma flotante
omar@Hogar:~$


Alguna idea de que puede estar pasando, les agradezco cualquier información o recomendación,  pues he buscado por todas partes y no h encontrado nada  y de verdad decesito ese programa.
Saludos y que Dios los bendiga

---

### Post by moreback on 2010-01-04
La verdad es que desconozco ese programa. ¿Podrías explicarnos que hace como para saber a qué nos enfrentamos?

Saludos.

---

### Post by Chogogo on 2010-01-04
Smile es un programa para generar pases de imagenes (Slideshow), lo baje desde este repositorio : [http://ppa.launchpad.net/gaspa/ppa/ubuntu](http://ppa.launchpad.net/gaspa/ppa/ubuntu)

Esta es su pagina Web: [http://smile.tuxfamily.org/](http://smile.tuxfamily.org/)

Gracias de antemano por su colaboración

Saludos y que Dios los bendiga

---

### Post by quitus on 2010-01-04
Instalaste un .deb o compilaste el programa? he leido que el archivo.deb daba algún error, a mi no me permitía seleccionar distintas transiciones, recomiendan compilar el programa, te dejo el enlace.
[http://www.kde-apps.org/content/show.php/SMILE?content=83276]("http://www.kde-apps.org/content/show.php/SMILE?content=83276")


salut

---

### Post by Chogogo on 2010-01-05
Instalé un .deb. a mediante  Synaptic.

el asunto es que he tratado de compilar un .tar.gz pero no he podido
Me podrian decir como se hace? (o indicarme en donde, en el link arriba no dice como, ni tampoco en la propia pagina web del programa)

Gracias, Saludos y que Dios los bendiga

---

### Post by Chogogo on 2010-01-05
Hola de nuevo.
Encontré como instalarlo manualmente y la instalacion funcionó sin ningún problema, pero sigo teniendo el mismo problema. El programa se cierra despues de 4 o 5 segundos de iniciado y me saca el mismo mensaje: "Exepcion de coma flotante". no se porque pero sospecho que es algo con el OPENGL, pues es la última linea que sale por terminal antes de botar el error. 

Espero que esta información les sea útil para tratar de decifrar este problemita...

Les agradezco de antemano

Saludos y Que Dios les bendiga.

---

### Post by quitus on 2010-01-06
cuando yo lanzo smile desde el terminal la version de opengl que aparece es la 3.1
YOUR LANGUAGE :  "ca_ES" 
LOCALE :  "ca" 
"LOADING LANGUAGE ... smile_ca" 
SYSTEM OVERLAY :  false 
DIRECT RENDERING : TRUE 
DOUBLE BUFFERING : TRUE 
OPENGL SUPPORT : TRUE 
OPENGL VERSION :  31

en la web de opengl aparece la version 3.2 como la ultima instalable, tu OPENGL VERSION : 4223 parece extraña. Prueba esto "dpkg-query -l libqt4-opengl"
A mi me resulta:     libqt4-opengl  4.5.3really4.5 Qt 4 OpenGL module


salut

---

### Post by Chogogo on 2010-01-07
Hola

Esta es la version que me sale a mi:

libqt4-opengl  4.5.0-0ubuntu4 Qt 4 OpenGL module

Será necesario cambiarlo??...de ser así ...como se hace??, porque cuando uno trata de desinstalarlo, dice que hay que desinstalar una cantidad de programas y por eso no lo he hecho. Que se puede hacer para remplazar este paquete por otra versión? ...a lo mejor ese es el culpable

Saludos y Que Dios los bendiga

---

### Post by quitus on 2010-01-07
no parece ser incorrecto, ya que yo uso karmic koala, por eso me aparece una version mas moderna, ademas la linea del opengl se mantiene siempre como la ultima linea, podria no ser un error de opengl. Lamentandolo mucho se acabaron mis conocimientos quizas en la web que postee anteriormente [http://www.kde-apps.org/content/show.php/SMILE?content=83276]("http://www.kde-apps.org/content/show.php/SMILE?content=83276") puedas recibir mas indicaciones.

salut

---

