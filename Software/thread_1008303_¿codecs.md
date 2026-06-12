---
title: "¿codecs?"
date: 2008-12-11
forum: Software
---

### Post by persalbe on 2008-12-11
Hola, 

Soy nuevo en linux y hace poco instalé Ubuntu 8.10.

He estado tratando de instalar los codecs que me permitiesen habilitar la máquina para navegar correctamente por internet, ver videos, escuchar mp3, etc., pero no he podido. 

Probé con las maneras sugeridas: 
 
a) por "Agregar/Quitar Programas", ubuntu-restricted-extras 
b) por la terminal, sudo apt-get install ubuntu-restricted-extras 

La respuesta que tuve es que no se puede acceder a los servidores.* Por otra parte, la navegación por internet en Ubuntu 8.10, así como en las otras distros Linux (excepto Mandriva), es mala:* hay muchas páginas que no pueden ser accedidas; no puedo ingresar siquiera a la propia Ubuntu Home Page.* 
¿Alguien conoce alguna manera de instalar los codecs esenciales que no sea a través de internet? 

Desde ya, muchas gracias a quien me pueda dar una mano. 

persalbe

---

### Post by luks911 on 2008-12-11
Bienvenido. 
En cuanto a los codecs, mi idea es que podés bajar los debs de Ubuntu Packages en otra máquina, llevártelos en un pendrive o similar e instalarlos a mano (bah, con un doble click por cada uno). [Acá]("http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras")[0] está el listado de los paquetes que se instalan al instalar ubuntu-restrited-extras, click en cada uno, baja´s hasta Download, elegís el que corresponde a tu arquitectura (386 ó 64), otra vez click y lo bajás de alguno de los mirrors que te ofrece.
No obstante, la navegación no debería ser más lenta que con otros sistemas. Si es eso lo que te pasa, se me ocurre que podés necesitar otros drivers a los que tenés instalados para tu placa de red/wifi o lo que uses para conectarte.
Ejecuta en una terminal
```
lspci 
```
y pegá acá el resultado. Eso va a listar los dispositivos conectados y se puede ver si hace falta un driver.

Tal vez haya alguna otra idea.

Saludos

[0] [http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

---

### Post by MeduZa on 2008-12-11
> **persalbe said:**
> Hola, 

Soy nuevo en linux y hace poco instalé Ubuntu 8.10.

He estado tratando de instalar los codecs que me permitiesen habilitar la máquina para navegar correctamente por internet, ver videos, escuchar mp3, etc., pero no he podido. 

Probé con las maneras sugeridas: 
 
a) por "Agregar/Quitar Programas", ubuntu-restricted-extras 
b) por la terminal, sudo apt-get install ubuntu-restricted-extras 

La respuesta que tuve es que no se puede acceder a los servidores.* Por otra parte, la navegación por internet en Ubuntu 8.10, así como en las otras distros Linux (excepto Mandriva), es mala:* hay muchas páginas que no pueden ser accedidas; no puedo ingresar siquiera a la propia Ubuntu Home Page.* 
¿Alguien conoce alguna manera de instalar los codecs esenciales que no sea a través de internet? 

Desde ya, muchas gracias a quien me pueda dar una mano. 

persalbe

te faltan pasos ahi:

sub a) agregar los repositorios de ubuntu media:
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

a)
b)
c) instalar mejores visualizadores:
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
y
sudo apt-get install gnome-mplayer gecko-mediaplayer

---

### Post by 2hot6ft2 on 2008-12-11
[http://quekabeza.blogspot.com/2008/08/gua-multimedia-en-ubuntu.html](http://quekabeza.blogspot.com/2008/08/gua-multimedia-en-ubuntu.html)

---

### Post by majatu on 2008-12-12
En aplicaciones/ Añadir y Quitar..., en "mostrar" selecciona "todas las aplicaciones disponibles".

Busca ahora ahi mismo "gstreamer" e instala todos los complementos y extras que te aparezcan.

Reinicia la pc y listo, con eso ya tendrias drivers para audio, video, flash y demas para internet.

De ultima si lo necesitas instala el ultimo paquete de Java porque algunas webs lo piden.



Esa es la manera mas fácil para mi, sin tener que usar consola ni editar nada.
Espero te ayude, saludos! ;)

---

