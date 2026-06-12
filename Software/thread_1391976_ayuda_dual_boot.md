---
title: "ayuda dual boot"
date: 2010-01-27
forum: Software
---

### Post by jorgtledo on 2010-01-27
_Mi problema es el siguiente:_

Tenia una sola particion con xp pro sp3, despues instalo el karmic dejando a windows y me crea otra particion, en total tengo dos. Cuando booteaba andava todo bien se iniciaban ambos sistemas, despues debido a algunos problemas reinstalo ubuntu y borro los archivos de xp solo dejando en esa particion una carpeta llamada bak con todos los archivos q no quiero perder en la particion ntfs de windows; cuando instalo de nuevo el karmic formateando la particion ext4 de ubuntu previamente creada, bueno hasta entonces no habia problema, pero, instalo de nuevo windows en la otra particion(la mas grande) y supuestamente copia todos los archivos, es mas, los puedo ver al montar esa particon desde linux pero no la bootea :(, updatee el boot y me salen ambos sistemas, ubuntu que es el que funciona y xp sp3... pero al seleccionar xp se queda la pantalla en negro y no arranca mas, que tendria q hacer borrar todas las particiones? y empezar de nuevo? pero no quiero perder los datos q tengo en la particion 1 que tiene como 200gb de archivos, que me recomiendan? 
ya se que es un foro de ubuntu pero los problemas empezaron desde que lo instale, capaz que es alguna config en la instalacion de ubuntu o algo :???: pero lo mas raro es que esa particion la veo desde ubuntu y parece todo bien, estan las respectivas path de windows y los archivos pero no se porque no arranca.

Gracias por responder...

---

### Post by Tosh78 on 2010-01-27
No se como instalaste Windows y podes seguir teniendo las opciones de los sistemas operativos. Windows tiene la "particularidad" de que sobreescribe la parte en la que se instala grub. En criollo: otros sistemas operativos pueden instalarse y "ver" que Windows esta instalado, pero Windows no.
Probablmente lo que paso es que la parte del disco donde Windows escribio los datos para bootear no esta accesible para el.
Yo no la tengo muy clara, pero quizas alguno de los chicos que sabe mas puede aportar mas luz sobre el tema.

---

