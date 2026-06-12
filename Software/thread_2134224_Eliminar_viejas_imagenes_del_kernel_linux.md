---
title: "Eliminar viejas imagenes del kernel linux"
date: 2013-04-10
forum: Software
---

### Post by drazhe on 2013-04-10
Hola a todos, hoy me dispuse a eliminar viejas imágenes del kernel que se que no voy a volver a utilizar, y al hacer el listado de dichas imágenes, me encuentro con dos que nunca las había visto anteriormente

> linux-image-3.2.0-39-generic-pae
linux-image-3.2.0-40-generic-pae
linux-image-3.5.0-23-generic
linux-image-3.5.0-26-generic
linux-image-3.5.0-27-generic
[SIZE=3][B]linux-image-generic-lts-quantal
linux-image-generic-pae[/B][/SIZE]

Mi pregunta es, si son necesarias o si puedo eliminar las imágenes que están remarcadas.

y otra pregunta, relacionada con las imágenes, yo instalé la versión **12.04 LTS precise de Ubuntu**, pero una de las imágenes dice **quantal**, lo que me hace pensar que está utilizando una imagen del a **versión 12.10 quantal quetzal**.. es así o me estoy equivocando? 

gracias por su atención!

---

### Post by gmunioz on 2013-04-11
Abre una terminal y ejecuta:
> sudo su
uname -r
La salida te dice cual está en uso

---

### Post by drazhe on 2013-05-25
Hola, quisiera saber cual de las imágenes puedo eliminar, ya que con el tiempo se van acumulado y ocupando espacio

tengo instaladas las siguientes
> [B]linux-image-3.5.0-30-generic
linux-image-3.5.0-31-generic
linux-image-generic-lts-quantal
[/B]

y según los comando
> [B]sudo su
uname -r[/B]

estoy utilizando 
> **linux-image-3.5.0-31-generic**

lo que me da un poco de miedo, es eliminar la que dice "lts-quantal" no se si sus componentes son necesarios para el correcto funcionamiento del sistema o si lo puedo eliminar sin problemas... desde ya gracias por su atención!

---

### Post by guillermolisi on 2013-05-26
Si estas usando la imagen de la version de Quantal, 3.5.0-X, y el sistema funciona bien, deja esa como activa y borra las anteriores.
Si queres un nivel adicional de seguridad, deja tambien la mas reciente anterior a la 3.5.0-31, asi si llegas a tener problemas con la ultima en uso podes iniciar la maquina con una imagen anterior.

---

### Post by drazhe on 2013-05-27
guillermolisi, Gracias por tu respuesta!
Siempre dejo la última y la anterior, por las dudas, pero me asustaba un poco que una de las imágenes tuviera un nombre tan diferente de las demás, era por eso que preguntaba!

De nuevo, gracias por la respuesta!

---

### Post by EnriqueK on 2013-05-28
Abre un terminal y pones
gedit ubucleaner
En ese documento vacío que se abre, pegas los siguiente

#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: must be root"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 0
fi

echo -e $YELLOW"Cleaning apt cache..."$ENDCOLOR
apt-get clean

echo -e $YELLOW"Removing old config files..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"Removing old kernels..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Emptying every trashes..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Script Finished!"$ENDCOLOR

grub-mkconfig && grub-install /dev/sdb  && update-grub


Guardas, cierras y cieras terminal. seguidamente abre otro terminal y pones 
sudo bash ubucleaner
Al pulsar Ebter, te hará una limpieza general y eliminará los kernels antiguos

---

### Post by drazhe on 2013-05-31
> **EnriqueK said:**
> Abre un terminal y pones
gedit ubucleaner
En ese documento vacío que se abre, pegas los siguiente

Gracias EnriqueK, pero eliminar los kernels ya lo sabía, lo que me preocupaba era el nombre raro de uno de los kernels...

Desde siempre dejo el último y el anterior por las dudas, y voy eliminando los más viejos a medida que se van actualizando, pero me preocupaba, como dije antes, que uno de los kernels que estaba pensando en eliminar, no tenía un número de versión y sinó que eran todas palabras (lts-quantal)... 

Pero ya loe eliminé y aún no pasó nada, mi máquina sigue funcionando sin problemas. intenté dar por cerrado el post, pero me desaparecieron los controles en las opciones del post

---

### Post by ibjsb4 on 2013-05-31
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by EnriqueK on 2013-05-31
Lo  que te puedo decir es que llevo años borrando todos los kernels anteriores, es mas, lo hago apenas sale uno nuevo y nunca tuve  problemas, los kernels anteriores ni siquiera figuran en repositorios

---

