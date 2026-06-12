---
title: "Inatalando Ubuntu EEE con UNetbootin"
date: 2008-08-22
forum: Software
---

### Post by mecdem on 2008-08-22
Mi consulta se refiere a la instalación de Ubuntu EEE 8.04 en una subnotebook ASUS EEE PC 4G, para lo es necesario crear un “live USB” para instalar la distribución.

Tengo:
1 - en una notebook con Kubuntu 8.04:
a) la iso de Ubuntu EEE
b) instalado syslinux
2 - en un CD la descompresión de la iso.

Luego de algún otro intento, encontré que podía utilizar UNetbootin para descomprimir la iso directamente en el pendrive. Bajé UNetbootin y le dí todos los permisos (777).

Al intentar ejecutarlo desde el modo gráfico, junto al puntero del mouse aparece el iconito del programa, pero luego de unos momentos desaparece.

En la barra de tareas se ve “gksu cargando aplicación” que también desaparece después de unos instantes.

Al intentar ejecutarlo desde consola, posicionándome en el directorio donde se encuentra el ejecutable, la línea ./unetbootin-linux-272 devuelve este mensaje:

unetbootin-linux-272: cannot connect to X server  :0.0

Y de aquí no sé cómo seguir.

Estuve utilizando un howto que está en [http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install) y una traducción al español.

Muchas gracias por la ayuda. Saludos.

---

### Post by kowal on 2008-08-22
Probá ejecutando esto antes:

DISPLAY=:0.0 xhost +

O bajá la versión de de [UNetbootin para Windows](http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-eeeubuntu-windows-238.exe&use_mirror=osdn) (utilizarías el lado oscuro para hacer el bien :P)

Saludos

---

### Post by mecdem on 2008-08-22
Muchas gracias, Kowal.
Pruebo y te cuento.

---

### Post by mecdem on 2008-08-23
No pude o no supe ejecutar DISPLAY=:0.0 xhost +
Lo que hice fue loguearme como root en una consola y escribir DISPLAY=:0.0 xhost +, pero me contestó:
No protocol specified
xhost:  unable to open display ":0.0"
...que no tengo idea de lo que significa.

Pero ¡¡funcionó "el lado oscuro"!!
Con la colaboración de Wine, claro.
¡¡Grandioso, Kowal!! Gracias.
__________________________________

Bien: ahora tengo mi live-pendrive.
Pero no todas son rosas...

Lo he probado en una notebook donde funcionó perfectamente.
En cambio la Asus EEE se niega a arrancar desde el pendrive, no obstante estar configurada para que bootee primero desde un removable-no-se-qué.

Si alguien me puede arrimar una ayuda, desde ya la agradezco.
Mientras tanto voy a recorrer los foros de Asus EEE, a ver si encuentro otra víctima de la tecnología que haya podido solucionar esto.

Muchas gracias y un saludo.

---

### Post by mecdem on 2008-08-25
¡Claaaaro, cómo iba a bootear desde el pendrive si una no mira bien el BIOS Setup!!!!

En la solapa Boot ingresé a Boot Device Priority, puse a la cabeza, como 1st Boot Device el [Removable Dev.] y... ¡ala!, F10, vamos p'adelante...

¡No, señor! Hay una segunda línea, Hard Disk Drives, que se habilita solo cuando está conectado el pendrive y que es donde hay que configurar la secuencia de booteo. Esta secuencia es "volátil": cuando se apaga el ordenador (o quizás sea efecto de desconectar el pendrive) el HDD:SM-Siliconmoti vuelve a encabezar la secuencia. Es decir que cada vez que se quiera arrancar desde el pendrive habrá que reconfigurar.

Espero que esta info le sirva a otros tan torpes como yo. Que alguno habrá.

Tengo instalado el Ubuntu EEE. :):)

---

### Post by Alejandro Vidal on 2008-08-25
> **mecdem said:**
> Tengo instalado el Ubuntu EEE. :):)

¿Cuál es tu opinión con el ubuntu EEE?
Hace un tiempo que estoy evaluando el tema de comprarme una de esas mini notebooks pero mi decisión esta enteramente condicionada por el sistema operativo.

Gracias.

---

### Post by mecdem on 2008-08-25
> **Alejandro Vidal said:**
> ¿Cuál es tu opinión con el ubuntu EEE?

Hola, Alejandro.
Mi Ubuntu EEE no tiene aun ni 24 horitas de instalado, así que mucho no puedo decirte todavía.

Ya sabrás que la Asus EEE viene con un Xandros preinstalado. Me pareció una opción simpática para acercar el equipito al gran público, pero también me pareció un tanto limitado. Mi interés en cambiarlo por algo más "sustancioso" tuvo que ver en parte con la idea de normalizar las tres notebooks con que me manejo, tener escritorios más o menos similares en todas y esas cosas. En las otra dos tengo Kubuntu, y Ubuntu, aunque no sea exactamente igual, le está más cercano que Xandros.

> Hace un tiempo que estoy evaluando el tema de comprarme una de esas mini notebooks pero mi decisión esta enteramente condicionada por el sistema operativo.

Quizás podrías probarlo bajándote la ISO correspondiente ([http://www.mininova.org/tor/1465678](http://www.mininova.org/tor/1465678)) y armándote un live-CD o un live-pendrive.

Por ahora no se me ocurre qué más decirte. Podré agregar algo más cuando haya "sacudido" un poco al Ubuntu EEE.

Saludos.

---

