---
title: "No puedo ver videos!"
date: 2010-09-26
forum: Software
---

### Post by nemodot on 2010-09-26
Tengo un problema,

luego de instalar una placa de video nueva, una geforce 8400GS, no puedo reproducir bien archivos de video.

Los abro y parece que se reproducen, hay sonido pero la pantalla permanece negra.

No tengo la menor idea como solucionar el problema. Tiene algo que ver con la nueva placa? Instalé los drivers recomendados.

Saludos.

---

### Post by Tosh78 on 2010-09-26
Hola! Que placa es? Estas hablando de videos online, como youtube, o videos en archivos como rmvb o avi?

---

### Post by matias_tati on 2010-09-26
Instalaste los driver?

---

### Post by nemodot on 2010-09-26
Como dije, tengo los drivers instalados.

No puedo ver videos de archivo como .avi, aunque sí videos flash en internet.

Tengo una geforce 8400GS

Por cierto, tampoco puedo ver la visualización cuando reproduzco un mp3 con el totem:
[IMG]http://i.imgur.com/cpAxt.png[/IMG]

Asi que esto está raro.

---

### Post by Pan0ramix on 2010-09-26
has probado con lanzar el configurador de hardware? habitualmente se encuentra bajo Sistema->administración. Debería decirte si hay algun controlador privativo que te imposibilite cargar los videos con la placa.

---

### Post by nemodot on 2010-09-27
Dice que tengo instalados los controladores recomendados de nvidia y no parece haber señales de que algo ande mal.

Me da la impresión que me falta o tengo mal una librería, por que cuando abro un video la ventana mantiene el tamaño del video pero no muestra nada. Ademas no puedo ver las visualizaciones cuando uso el totem para reproducir musica.

---

### Post by devozero on 2011-04-14
[COLOR=Black]lo que sucede es que 10.10 controla la grafica directo el kernel y cuando instalas una nueva tarjeta se crea el archivo xorg.conf y este toma el control yo hice estas 2 opciones

[/COLOR][COLOR=Black]1- prueba con lo siguiente: en una terminal ejecutá el comando  gstreamer-properties  En las opciones que te van a aparecer, ve a la pestaña Video y en Salida predeterminada  selecciona la opción "X Window System (Sin Xv)". Cierra el cuadro de diálogo y prueba un video

en mi caso los reproducio el totem pero en el vlc solo se escuchaba el sonido


[/COLOR][COLOR=Black]la otra es eliminar el archivo xorg.conf para que vuelva tomar el control el kernel con el comando

[COLOR=Black]sudo rm /etc/X11/xorg.conf[/COLOR]

Reiniciamos con:
[COLOR=#BF9000][COLOR=Black]sudo reboot

EN MI CASO FUNCIONO con una nvidia 6800gt pero si tienes algun problema en iniciar despues del reinicio modo grafco has lo siguiente
[/COLOR]
[/COLOR]Iniciar Ubuntu en modo recuperación (recovery).

Elige la última opción: "root"[/COLOR] [COLOR=Black]

Escribe en la pantalla:[/COLOR] [COLOR=Black]
[/COLOR] [COLOR=Black]Xorg -configure

Se creará el archivo "[/COLOR] [COLOR=Black]xorg.conf.new" en el directorio o carpata /root 

Renómbralo como "[/COLOR] [COLOR=Black]xorg.conf" y Muévelo al directorio /etc/X11 con  el comando:
[/COLOR] [COLOR=Black]mv xorg.conf.new /etc/X11/xorg.conf

Ya tienes tu archivo xorg.conf cargado con la configuración  predeterminada. Sólo queda reiniciar con:[/COLOR] [COLOR=Black]
[/COLOR] [COLOR=Black]reboot

y si aun asi tienes problemas regresa a tu anterior tarjeta grafica para q almenos trabajes en modo grafico[/COLOR]  
[COLOR=Black][COLOR=#bf9000]

[/COLOR][/COLOR]

---

### Post by granjero on 2011-04-14
en lugar de borrar el archivo de configuración de X te recomiendo cambiarle el nombre. De esa manera si no funciona luego de lo que hagas podrás volver a ponerle el nombre original y todo volverá a como estaba antes.

en lugar de:
```
sudo rm /etc/X11/xorg.conf
```
podés hacer 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
para volver 
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

salud!

---

