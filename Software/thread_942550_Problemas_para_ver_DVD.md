---
title: "Problemas para ver DVD"
date: 2008-10-09
forum: Software
---

### Post by arysar on 2008-10-09
Hola

Siguiendo la guia para Instalar codecs multimedia que esta en guia-ubuntu, he instalado los codecs para usar el totem/gstreamer para ver formatos VCD y DVDs. 
Los DVD se ven pero con rayas oblicuas los VCD no se ven, sale un mensaje que no se puede reproducir VCD. 
Instalo VLC y tengo el mismo problema con los DVD no asi con el VCD.

Mi idea era probar con XINE, la pregunta es si tengo que desinstalar totem/gstreamer para poder instalar totem/xine

Gracias!

---

### Post by Mauro22 on 2008-10-09
Podes instarlo sin tener que desinstalar nada..


Podes probar xine o mplayer...


Bajaste el ubuntu-restricted-extras ??

---

### Post by guisheca on 2008-10-09
Yo creo que no, igual, cuando intentes instalarlo el mismo método que uses para hacerlo te va a decir si es necesario desinstalarlo o no.
De todas formas te recomiendo el mplayer o el xine-ui para reproducción de dvds, yo nunca pude ver un dvd en totem no se por qué.
Lo raro es que no te reproduzca en el VLC que es un buen programa. Te instalaste todos los codecs necesarios??.

---

### Post by feche_mza on 2008-10-09
***ahh es todo un tema ver dvds en ubuntu, si ya instalaste todos los plugins gstreamer vas a poder verlos con totem, pero totem no es compatible con los los menus de los dvds, es mejor usar totem xine, pero de todas formas esta bueno instalar un par de cosas que ahora te digo, por que a los dvds con derechos de autor no los vas a poder reproducir asi nomas,***

***primero: desde terminal escribis***
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
***eso te agrega el repositorio a la sources.list***

***segundo: tambien en terminal pones esto***> 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
***eso te agrega la llave publica para que te ande joya y te actualiza la lista de repositorios***

***tercero:siempre en terminal pones***
> sudo apt-get install w32codecs
***con ese instalas los codescs para los archivos privativos***

***y para ir terminando:***
> sudo apt-get install libdvdcss2[B][I]
con ese supuestamente vas a poder ver dvds tanto truchos como originales (que siempre vienen bloqueados por derechos de autor) sino mira el nombre lib_dvd_css2

ahh como un bono extra tambien instalate los restricted extras
> sudo apt-get install ubuntu-restricted-extras
esos van a tardar un rato en bajarce, pero estan re buenos por que te complementan los codecs para un monton de formatos, ademas de instalarte un par de tipografias o otras cosas nativas en win (como la comic sans)

con todo eso deberias poder ver dvds, vcs, rmvb, entre otros, de hecho yo hice todo esto para ver rmvb pero tambien sirve para eso que vos necesitas y siempre usa el xine para los dvds , yo hago asi para los dvds el xine y para los videos comunes el totem[/I][/B]

---

