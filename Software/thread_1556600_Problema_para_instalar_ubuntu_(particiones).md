---
title: "Problema para instalar ubuntu (particiones)"
date: 2010-08-19
forum: Software
---

### Post by diegol3d on 2010-08-19
Hola gente del foro, soy menos que novato. tengo windows 7 y quisiera meterme en el mundo linux (ubuntu). Luego de bajarme de la pagina de ubuntu el dvd 10.04 y quemarlo, y leer tutoriales al respecto me encontre con un problema en la parte de particiones manual (avanzado) porque tengo 1 disco de 500gb donde el sistema operativo esta en C y tengo otra particion D donde tengo datos. me quedan libres 78gb que es donde quiero poner el ubuntu (doble boot) para meterme en este mundo. 

[[IMG]http://img832.imageshack.us/img832/3738/discoparticion.jpg[/IMG]]("http://img832.imageshack.us/i/discoparticion.jpg/")



Dentro del ubuntu (particiones - modo avanzado) me sale:
/deb/sda
    /deb/sda1           ntfs           104 mb (archivo de sistema)
    /deb/sda2           ntfs          163.000 mb  (sistema operativo windows 7)
    /deb/sda5            ntfs          252.000 mb  (datos: ojo esta es logica, no primaria)
  Espacio libre                   84.000 mb

Segun el GParted

[[IMG]http://img534.imageshack.us/img534/8297/pantallazo1eh.jpg[/IMG]]("http://img534.imageshack.us/i/pantallazo1eh.jpg/")




Dentro de particiones - avanzado, cuando pincho espacio libre - añadir - seteo: primaria y principio, luego / (raíz), ext4, tamaño: 15.000 mb me queda el resto 69.000 mb inútil :shock: ,y no me deja añadir mas. Supongo que esto es porque abarque el máximo de 4 particiones primarias. Hay alguna manera de poner el doble boot (windows 7 y ubuntu) en un mismo disco con 2 particiones en windows 7 (C y D)???

---

### Post by alfplayer on 2010-08-20
El espacio sin asignar puede estar en la partición extendida. Probá si deja usar más espacio creando como lógica la partición de root (las lógicas usan espacio dentro de las extendidas).

---

### Post by diegol3d on 2010-08-20
Hola alfplayer, gracias por contestar. Teneme un poco de paciencia soy muy novato en esto. No se que es root, es acaso raiz, home y swap? Lo que propones es que aparte de C (windows) haga una sola particion grande, esto seria D, y dentro de esta particion cree 78gb para linux y ahi crear las subparticiones? esta bien? estas serian (raiz, home y swap) pero todas como lógica. Es asi o te entendi mal? Si es asi igual funcionara el doble boot? Porque habia leido que la raiz (/) tiene que ser primaria.

---

### Post by alfplayer on 2010-08-20
> **diegol3d said:**
> Hola alfplayer, gracias por contestar. Teneme un poco de paciencia soy muy novato en esto. No se que es root, es acaso raiz, home y swap? Lo que propones es que aparte de C (windows) haga una sola particion grande, esto seria D, y dentro de esta particion cree 78gb para linux y ahi crear las subparticiones? esta bien? estas serian (raiz, home y swap) pero todas como lógica. Es asi o te entendi mal? Si es asi igual funcionara el doble boot? Porque habia leido que la raiz (/) tiene que ser primaria.

Hola. 

Eso no es lo que propongo. 

Unas aclaraciones:
[LIST]
[*]Tu idea original de usar el espacio no asignado es la mejor. No hay necesidad de modificar las paritciones de windows.
[*]La partición root es la partición raíz (es lo mismo).
[*]La partición de root no tiene que ser primaria, puede ser lógica.
[/LIST]

Mi opinión y lo que propongo es que, si tu PC tiene una cantidad grande de RAM y si no querés usar hibernación, no hagas partición swap. Y también que no es necesario crear una partición home. La partición raíz es la única totalmente necesaria, que es la que podrías ubicar en el espacio no asignado (que es lo que tenés que lograr).

---

### Post by diegol3d on 2010-08-20
> **alfplayer said:**
> Hola. 

Eso no es lo que propongo. 

Unas aclaraciones:
[LEFT]
[LIST]
[*]Tu idea original de usar el espacio no asignado es la mejor. No hay necesidad de modificar las paritciones de windows.
[/LIST]
[/LEFT]

[LIST]
[*]La partición root es la partición raíz (es lo mismo).
[*]La partición de root no tiene que ser primaria, puede ser lógica.
[/LIST]

Mi opinión y lo que propongo es que, si tu PC tiene una cantidad grande de RAM y si no querés usar hibernación, no hagas partición swap. Y también que no es necesario crear una partición home. La partición raíz es la única totalmente necesaria, que es la que podrías ubicar en el espacio no asignado (que es lo que tenés que lograr).

Hola de nuevo, muchas gracias por responder nuevamente. Se entendio perfecto. Te digo a boca de urna lo que pienso hacer: 
     
Voy a dejarlo tal cual, en el espacio no asignado que tengo (78gb) voy a crear como logica la particion raiz (/) de un tamaño de 15.000 mb y si me deja, voy a poner el resto, tambien como logica, el /home. Sino me deja crear el home, pongo todo como root (/) y listo, Le doy para adelante y como dijo Duhalde: que sea lo que dios quiera.
El orden de crear particiones es indiferente, o si o si me tiene que quedar primero el root y abajo el home?
Una ultima cosa; crees que una vez que termine con la instalacion de esta manera voy a tener el doble boot, o eso es incierto? Soy reiterativo con este tema, porque tengo la terrible sospecha que una vez que termine, o no me entra a windows, o no me entra a ubuntu.

---

### Post by alfplayer on 2010-08-21
> **diegol3d said:**
> Voy a dejarlo tal cual, en el espacio no asignado que tengo (78gb) voy a crear como logica la particion raiz (/) de un tamaño de 15.000 mb y si me deja, voy a poner el resto, tambien como logica, el /home. Sino me deja crear el home, pongo todo como root (/) y listo

No entiendo para qué probar crear una home primero. Si querés home, hacés home. Y si no querés, no la hacés.

> **diegol3d said:**
> El orden de crear particiones es indiferente, o si o si me tiene que quedar primero el root y abajo el home.
Una ultima cosa; crees que una vez que termine con la instalacion de esta manera voy a tener el doble boot, o eso es incierto? Soy reiterativo con este tema, porque tengo la terrible sospecha que una vez que termine, o no me entra a windows, o no me entra a ubuntu.

En la mayoría de los casos linux funciona con las particiones en cualquier orden. Pero a veces hay problemas: por ejemplo, si la computadora es vieja puede aparecer el error 18 de Grub por instalar el sistema lejos del principio del disco rígido (no sé si es un problema con Ubuntu 10.04). Lo más probable es que el dual-boot funcione bien, y si no funciona se busca la forma de resolverlo.

---

### Post by diegol3d on 2010-08-22
Gracias alfplayer nuevamente por contestar. Me exprese mal, lo que quise poner fue que primero voy a crear la raiz (/) y si me deja creo el home. La maquina que tengo es nueva, ojala que no tenga drama en el doble boot. El lunes voy a probar, igualmente más que seguro que voy a postear. Te agradezco tu amabilidad en contestar y hacerme animar a probar este nuevo mundo. Mil gracias!

---

