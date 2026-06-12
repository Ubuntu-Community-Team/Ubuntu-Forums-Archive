---
title: "Reiniciar configuración del usplash"
date: 2009-04-06
forum: Software
---

### Post by guisheca on 2009-04-06
Que tal muchachos, resulta que estuve toqueteando la configuración del usplash de ubuntu, haciendo uso del administrador de arranque. Y resulta que ahora me quedé sin usplash, mejor dicho, aparece mientras la barra de progreso se mueve de un lado a otro. Pero cuando se supone que tiene que comenzar a cargarse la barra naranja, vuelve al modo texto (verbose mode) y me quedo sin splash.

En el administrador de arranque ya puse todo como estaba y siguen igual las cosas, me gustaría saber donde se encuentra, si existe, algún archivo de texto o lo que sea que me permita volver todo a como estaba al inicio de los tiempos :p

En realidad me tiene sin cuidado tener o no una barra de progreso, el problema radica en los momentos en los cuales el sistema considera que tiene que hacer una comprobación de disco, con el usplash activado puedo cancelarlo, pero sin el no. Ya se que es por mi propio bien la comprobación, pero es que mi home tiene un tamaño de 150gb y esta casi todo usado, es decir, tarda como 5 minutos de reloj en comprobarlo y me ha pasado de prender mi pc porque necesitaba algo apurado y justo coincidía que se hacía la comprobación de disco con las consecuencias imaginables :mad:.

Para esos casos me gustaría contar nuevamente con el querido usplash.

Espero me puedan tirar un cable. Saludos y gracias.

---

### Post by staar on 2009-04-06
yendo al clasico método windosero: desinstalalo con purge y volvelo a instalar :-P:-D

saludos

---

### Post by josecuervo86 on 2009-04-06
Guisheca, los archivos de texto del usplash estan en usr - lib - usplash

A mi me pasa que cargue kubuntu-desktop teniendo Ubuntu, para probar la suite de KDE pero me cambio el usplash al de Kubuntu, y no me gusta :(.
Asique si hay algun alma caritativa que me pueda pasar la configuracion del usplash de ubuntu, yo agradecidisimo :D

Edit: lo solucione como dijo el amigo staar:

```
sudo apt-get remove --purge usplash

sudo apt-get install usplash
```

Gracias staar ;)

---

### Post by Air23 on 2009-04-06
> **josecuervo86 said:**
> Guisheca, los archivos de texto del usplash estan en usr - lib - usplash

A mi me pasa que cargue kubuntu-desktop teniendo Ubuntu, para probar la suite de KDE pero me cambio el usplash al de Kubuntu, y no me gusta :(.
Asique si hay algun alma caritativa que me pueda pasar la configuracion del usplash de ubuntu, yo agradecidisimo :D

Edit: lo solucione como dijo el amigo staar:

```
sudo apt-get remove --purge usplash

sudo apt-get install usplash
```

Gracias staar ;)

Otra manera es la siguiente:
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by josecuervo86 on 2009-04-06
> Otra manera es la siguiente:
Code:

sudo update-alternatives --config usplash-artwork.so



Pero esa seria para poder configurar los archivos .so del splash no? En Gnome-look hay archivos de configuración para darle una "lavada de cara" al usplash que estan bastante buenos.

---

### Post by pablo.s on 2009-04-06
Eh guisheca, hacete un backup que estas
jugando con fuego rociado de nafta.

Y en que fomato tenés la partición?
No me vas a decir que con Ext2...

---

### Post by guisheca on 2009-04-07
Gentes, me está entrando mucha bronca desinstalé uspash con el comando que puso josecuervo86 y el problema persiste!! Edité el menu.lst del grup y añadí al final de la entrada que uso para arrancar ubuntu, agregando vga=791 y nada, sólo se ven letras mas pequeñas :(.
Todavía me falta probar el comando que puso Air23 (aguante jordan dicho sea de paso jeje) lo pruebo y comento que pasó.
Pablo.s jajaja ya se che ta todo bajo control pero gracias por el consejo, por cierto uso el viejo y querido sistema ext3, y por los comentarios que voy viendo no pienso pasar a ext4.
Saludos.

---

### Post by guisheca on 2009-04-07
En fin, lo intenté todo, hasta desinstalé usplash y lo volví a instalar, pero nada de nada. Sólo me queda esperar a que salga jaunty y actualizar.
Igual, encontré un comando que te fuerza la comprobación de disco al inicio:

$ sudo shutdown -rF now

Así no me encuentro con sorpresas jeje.
Saludos.



Bueno, acabo de comprobar que ese comando tampoco funciona... una mala noche, me iré a dormir y mañana con mejores luces trataré de solucionar el problema.

---

### Post by guisheca on 2009-04-07
Puff lo que es ser cabeza dura, me quedé buscando una respuesta y con los últimos signos de vida que me quedan escribo como lo solucioné:

El problema estaba en que hace un tiempo había cambiado de tamaño mi swap, puesto que era demasiado grande (1.5gb de swap y tengo 2gb de ram) y como al cambiar de tamaño se cambia el UUID, esto trae algunos problemas consigo, como esto que cuento en el post.

Como se arregla? fácil actualizando el nuevo UUID de la swap en donde haga falta, concretamente en /etc/fstab y en /etc/initramfs-tools/conf.d/resume. Como se hace? bueno, dejo el enlace en donde lo encontré que está mejor explicado de lo que yo pueda explicar a esta hora :grin:

[El enlace salvador!!]("http://www.mail-archive.com/linux-l@listas.softwarelibre.cu/msg12263.html")

Lamentablemente no encontré forma de agradecerle al flaco ese la ayuda que me dio.

Ojalá a alguien mas le sirva. Saludos.


PD: no me acuerdo como poner SOLUCIONADO

---

