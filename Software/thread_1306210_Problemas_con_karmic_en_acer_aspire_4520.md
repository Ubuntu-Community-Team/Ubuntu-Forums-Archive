---
title: "Problemas con karmic en acer aspire 4520"
date: 2009-10-30
forum: Software
---

### Post by marcos@liotti.com.ar on 2009-10-30
Hola Gente . ante todo gracias por el tiempo. Es la primera nota que abro en un foro a pesar de hacer casi 1 a#o que vengo leyendo y aprendiendo gracias a Uds. 
Me anime a abrir un hilo nuevo por que la verdad estoy encajado. Tengo una notebook acer aspire 4520.con una particion de vista que vino con la maquina y otra con ubuntu, que inicie con la 8.10 y hasta antes de ayer funcionaba todo perfecto con ubuntu 9.04 . hice la actualizacion a karmic 9.10 atraves del gestor de actualizaciones y me encontre con algunas dudas y problemas.
Lo primero que note fue que no funcionaba el touchpad y encontre googleando que poniendo en un terminal :
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
despues
reboot.
se corrigio y funciona perfecto.
Otra dificultad es que no consigo tener sonido . Probe en reinstalar alsa , cambiarlo por la version 1.0.21-4 y no logro hacerla sonar. En la barra de tareas el icono del parlante aparece sin problemas, es mas , el volumen sube y baja, aunque nada se oye. Por supuesto no esta silenciado.
En las prefecencias de sonido no existe ningun hardware, solo una "Salida Boba" mono. Lo que me da a pensar que no reconoce la plada de sonido. 
$lspci| grep Audio
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
Pero las mayores dudas aparecen cuando leyendo por ahi el grub no es el indicado para karmic y hay que instalar el grub2 ????.
Cuando inicia la notebook todavia aparece en grub el 9.04 linux-2.6.28.15-generic o algo asi y no el 9.10 linux-2.6.31.xx . Esto por que es?. Recuerdo perfectamente las preguntas de la actualizacion de si queria mantener el menu.lst pero no me daba opcion a decir que no.
Tengo que cambiar el Grub a grub2 ? como se hace eso?.
Si pongo en un terminal :
root@Pc-Acer-amd64:/home/marcos# uname -r
2.6.28-15-generic
El sonido no funciona por que sigo arrancando en 9.04 mezclado con karmic 9.10 ? Si es asi Como cambio el grub o como cambio para arrancar con el 9.10?
La pantalla de inicio de gnome es la nueva (muy bonita por cierto)
Bueno Espero que entiendan que es un tema muy especifico y por eso me anime a abrir un hilo nuevo. No quiero ser pesado pero dudas tengo un monton. Como se si tengo ext3 o ext4 ? como me paso si es que tengo ext3?. Gracias por la atencion , un personaje televisivo decia "Y SI NO PREGUNTO COMO SE?".

---

### Post by Mauro22 on 2009-10-30
> **marcos@liotti.com.ar said:**
> 
Lo primero que note fue que no funcionaba el touchpad y encontre googleando que poniendo en un terminal :
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
despues reboot.
se corrigio y funciona perfecto.


Eso estaria pero no es "normal"... 

> **marcos@liotti.com.ar said:**
> 
Otra dificultad es que no consigo tener sonido . Probe en reinstalar alsa , cambiarlo por la version 1.0.21-4 y no logro hacerla sonar. En la barra de tareas el icono del parlante aparece sin problemas, es mas , el volumen sube y baja, aunque nada se oye. Por supuesto no esta silenciado.
En las prefecencias de sonido no existe ningun hardware, solo una "Salida Boba" mono. Lo que me da a pensar que no reconoce la plada de sonido. 
$lspci| grep Audio
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)


Probaste con el LiveCd antes de instalar? Sé que hiciste un upgrade, o sea el cd no lo bajaste... 

> **marcos@liotti.com.ar said:**
> 
Pero las mayores dudas aparecen cuando leyendo por ahi el grub no es el indicado para karmic y hay que instalar el grub2 ????.
Cuando inicia la notebook todavia aparece en grub el 9.04 linux-2.6.28.15-generic o algo asi y no el 9.10 linux-2.6.31.xx . Esto por que es?. Recuerdo perfectamente las preguntas de la actualizacion de si queria mantener el menu.lst pero no me daba opcion a decir que no.
Tengo que cambiar el Grub a grub2 ? como se hace eso?.


Eso ni idea. :S

> **marcos@liotti.com.ar said:**
> 
Como se si tengo ext3 o ext4 ? 
como me paso si es que tengo ext3?.

Con alguno programa tipo Gparted deberias poder saber, "sudo fdisk -l" dice extendida nomás pero no especifica si es 3 o 4 (al menos a mi)


Mi recomendacion: Probar  un liveCd de 9.10 y ver como anda todo; si anda joya, hacer un fresh install... sino quedarte en 9.04... si andaba todo... ;)

---

### Post by guillermolisi on 2009-10-30
> **marcos@liotti.com.ar said:**
> Hola Gente . ante todo gracias por el tiempo. Es la primera nota que abro en un foro a pesar de hacer casi 1 a#o que vengo leyendo y aprendiendo gracias a Uds. 
Me anime a abrir un hilo nuevo por que la verdad estoy encajado. Tengo una notebook acer aspire 4520.con una particion de vista que vino con la maquina y otra con ubuntu, que inicie con la 8.10 y hasta antes de ayer funcionaba todo perfecto con ubuntu 9.04 . hice la actualizacion a karmic 9.10 atraves del gestor de actualizaciones y me encontre con algunas dudas y problemas.
Lo primero que note fue que no funcionaba el touchpad y encontre googleando que poniendo en un terminal :
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
despues
reboot.
se corrigio y funciona perfecto.
Otra dificultad es que no consigo tener sonido . Probe en reinstalar alsa , cambiarlo por la version 1.0.21-4 y no logro hacerla sonar. En la barra de tareas el icono del parlante aparece sin problemas, es mas , el volumen sube y baja, aunque nada se oye. Por supuesto no esta silenciado.
En las prefecencias de sonido no existe ningun hardware, solo una "Salida Boba" mono. Lo que me da a pensar que no reconoce la plada de sonido. 
$lspci| grep Audio
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
Pero las mayores dudas aparecen cuando leyendo por ahi el grub no es el indicado para karmic y hay que instalar el grub2 ????.
Cuando inicia la notebook todavia aparece en grub el 9.04 linux-2.6.28.15-generic o algo asi y no el 9.10 linux-2.6.31.xx . Esto por que es?. Recuerdo perfectamente las preguntas de la actualizacion de si queria mantener el menu.lst pero no me daba opcion a decir que no.
Tengo que cambiar el Grub a grub2 ? como se hace eso?.
Si pongo en un terminal :
root@Pc-Acer-amd64:/home/marcos# uname -r
2.6.28-15-generic
El sonido no funciona por que sigo arrancando en 9.04 mezclado con karmic 9.10 ? Si es asi Como cambio el grub o como cambio para arrancar con el 9.10?
La pantalla de inicio de gnome es la nueva (muy bonita por cierto)
Bueno Espero que entiendan que es un tema muy especifico y por eso me anime a abrir un hilo nuevo. No quiero ser pesado pero dudas tengo un monton. Como se si tengo ext3 o ext4 ? como me paso si es que tengo ext3?. Gracias por la atencion , un personaje televisivo decia "Y SI NO PREGUNTO COMO SE?".
Bienvenido.

Para proximas incursiones y para facilitar las respuestas y posteriores consultas de otros interesados, separa los temas en threads diferentes, mas focalizados, y no todo junto en uno solo como acabas de hacer.

Los temas de software, son los que solamente se pueden insultar, en la seccion Software. Los de hardware, que se pueden patear, en la de Hardware. Los temas relacionados con cuestiones sociales, del LoCo Team argentino, de software libre, y todo otro vinculado con Ubuntu que sea mas ameno tratarlo en una charla de cafe o cerveza de por medio, en Comunidad.

Esto siempre y cuando alguno de los temas no tengan algun thread ya abierto con lo cual solo tendrias que agregar tu caso.

---

