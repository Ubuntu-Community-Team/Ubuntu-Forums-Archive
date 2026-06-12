---
title: "Problema con GTK en Kubuntu"
date: 2008-04-26
forum: Software
---

### Post by _kAz_ on 2008-04-26
Primero me presento ya que hace poco me registre: me llamo Lucas, tengo 23 años, soy de Córdoba Capital, futuro periodista y locutor (si todo sale bien, jeje) y orgulloso usuario de software libre desde hace 4 meses.

Vengo a plantearles un problema que lamentablemente se me ha vuelto recurrente, el cual no me ha permitido funcionar **ni Wine-Doors ni Emesene**.

Supongo que tiene que ver con problemas de librerias. Cada vez que quiero ejecutar Emesene me sale el siguiente error (sucede casi identico con Wine -Doors):

[I][INDENT]Traceback (most recent call last):
  File "/usr/share/emesene/emesene_launcher", line 31, in ?
    import Controller
  File "/usr/share/emesene/Controller.py", line 21, in ?
    import gtk
ImportError: No module named gtk[/INDENT][/I]

Que puedo hacer??? Por ahora estoy utilizando Kubuntu, pero en vistas de estos conflictos de librerías, la proxima distro va a ser Ubuntu.

---

### Post by beuno on 2008-04-26
sudo aptitude install python-gtk2

---

### Post by _kAz_ on 2008-04-26
> sudo aptitude install python-gtk2

Luego de un "analisis" que hizo me salio esto:

[INDENT][I]0 paquetes actualizados, 0 nuevos instalados, 38 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 76,4MB.
¿Quiere continuar? [Y/n/?][/I][/INDENT]

Le di que si... Desinstalo varias librerias gtk aparentemente (creía que iba a hacer lo contrario :S).

Sin embargo sigue saliendo el mismo error cuando intento ingresar a Emesene o Wine-Doors:

[I][INDENT]Traceback (most recent call last):
  File "/usr/share/emesene/emesene_launcher", line 31, in ?
    import Controller
  File "/usr/share/emesene/Controller.py", line 21, in ?
    import gtk
ImportError: No module named gtk
[/INDENT][/I]

---

### Post by Hei Ku on 2008-04-27
hace lo siguiente:

sudo apt-get update
sudo apt-get --reinstall python-gtk

---

### Post by Hei Ku on 2008-04-27
Borrar -> doble post. estos foros nuevos apestan.

---

### Post by _kAz_ on 2008-04-27
> **Hei Ku said:**
> hace lo siguiente:

sudo apt-get update
**sudo apt-get --reinstall python-gtk**

Al hacer eso me sale 
[I][INDENT]Lucas@ljd-desktop:~$ sudo apt-get --reinstall python-gtk
E: Operación inválida: python-gtk
[/INDENT][/I]

Intente con:

*[INDENT]sudo aptitude reinstall python-gtk2[/INDENT]*

Reinstalo el paquete, lo mismo hice con python-cairo. Sin embargo siguen saliendo los mismos mensajes de error:

[I][INDENT]Lucas@ljd-desktop:~$ emesene
Traceback (most recent call last):
  File "/usr/share/emesene/emesene_launcher", line 31, in ?
    import Controller
  File "/usr/share/emesene/Controller.py", line 21, in ?
    import gtk
ImportError: No module named gtk[/INDENT][/I]

Y en el caso de Wine Doors:
[I][INDENT]Lucas@ljd-desktop:~$ wine-doors
Started logging session
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 21, in ?
    from wine import wine
  File "/usr/share/wine-doors/src/wine.py", line 14, in ?
    from utils import GetCDMountPoint
  File "/usr/share/wine-doors/src/utils.py", line 2, in ?
    import gtk, gobject, gtk.glade
ImportError: No module named gtk[/INDENT][/I]

---

### Post by Hei Ku on 2008-04-27
tenes instalado los paquetes principales de gtk? porque eso puede ser el problema.
supongo que deben ser algo como libgtk o algo asi. basicamente, como usas kubuntu, las bibliotecas y paquetes de gtk no vienen instalados asi que quizas te falta toda esa base.

---

### Post by _kAz_ on 2008-04-27
Si bien ya tenía instalados los paquetes bases de gtk, abri adept y empece a instalar todo lo que me pareciera relativamente relacionado (libgtkperl, libgtkruby y cosas asi), en resumen 14mb de descarga y 39 de instalación. Resultado:

[I][INDENT]Lucas@ljd-desktop:~$ emesene
Traceback (most recent call last):
  File "/usr/share/emesene/emesene_launcher", line 31, in ?
    import Controller
  File "/usr/share/emesene/Controller.py", line 21, in ?
    import gtk
ImportError: No module named gtk[/INDENT][/I]

NO CAMBIO NADA!!!!!
:cry: :cry: :cry: :cry: :cry: :cry: :cry:

Ya fue... mañana mismo instalo Windows :lolflag:

---

### Post by Hei Ku on 2008-04-27
Como instalaste el emesene y el wine-doors? Porque el problema puede venir por ahi, sobre todo si no los instalaste desde el repositorio, que en ese caso deberían haber bajado todas las dependencias, y si no, hay que reportarlo a Launchpad para que lo arreglen.

---

### Post by _kAz_ on 2008-04-27
Emesene lo baje desde adept luego de agregar los repositorios oficiales. A Wine-Doors lo instale desde un .tar y desde un .deb, ninguno de los dos funciono (desde repositorios no se podía porque me decía que no había "candidato").

De todas formas, es más que obvio que el problema es la incompatibilidad de librerías o algo así. Quiero suponer que le pasa a todos los usuarios de Kubuntu y no sólo a mí.

Una lastima, me hubiese sido muy útil sobre todo Wine Doors, esperare hasta instalar el Ubuntu 8.04, espero que ahí sí funcione.

---

### Post by _kAz_ on 2008-04-28
Es INCREIBLE que en todos los lugares donde busqué NO ENCONTRARON LA SOLUCION a este problema.

¿Cómo puede ser? No es un inconveniente de Kubuntu Hardy que podría ser comprensible, viene de hace rato, pero nadie sabe cómo solucionarlo. Miles de foros leyendo problemas similares (import: no module named gtk), pero siempre queda el problema planteado y a otra cosa mariposa. :(

---

### Post by ames89 on 2009-06-15
si asi es y no solo en kubuntu, desde debian squeezy y kde es lo mismo! de repente instale el python compilado desde la pagina de python y dejo de funcionar al dia siguiente, puede ser un problema entre las librerias del python al actualizar un modulo y el resto falla por incompatibilidad, es lo que YO creo

---

