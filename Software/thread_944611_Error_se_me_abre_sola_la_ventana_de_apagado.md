---
title: "Error: se me abre sola la ventana de apagado"
date: 2008-10-11
forum: Software
---

### Post by chulelinux on 2008-10-11
Aprovecho para saludar por primera vez a la comunidad y comentar que tan solo hace menos de un mes comencé a explorar el mundo linux y la verdad que pienso mudarme absolutamente cuando le tome mejor el tiempo al SO. El problema que tengo es que de la nada se me abre la ventana que uno solo abre cuando quiere apagar reiniciar o etc el equipo. No tengo problemas de hard (salvo que la nvidia 7300 o la sinto encore traigan problemas), los paquetes que instalé no han sido muchos, el test de memos ok, y busque por todos lados si aparecía algo sobre esto y nada. Iba a reinstalar pero cro que la mejor manera de aprender es tratar de solucionar el problema... Saludos.

---

### Post by Mauro22 on 2008-10-11
Hola, bienvenido al mundo de Linux!


Para tratar de resolver tu problema, tenes que darnos mas info.


Que "sabor" de ubuntu usas: Ubuntu, Kubuntu, Xubuntu, etc ?

Tenes algun receptor infrarrojo como los de las placas capturadoras? (Por experiencia)

Si probaste el liveCD, lo hacia?



Saludos!

---

### Post by chulelinux on 2008-10-12
Disculpen mi novates... Tengo Ubuntu 8.04  y respecto a lo que me preguntas Mauro si... tengo el receptor infrarrojo de la sintonizadora encore. En Cdlive no me lo hace, lo estuve probando rato largo y no lo hace. Revisé las memorias y no tira error... ahora que me lo haces pensar, creo que el problema apareció despues de instalar la sintonizadora y tvtime... Voy a tratar de desinstalar todo y ver que pasa... si se ocurre otra cosa aparte buenísimo...

---

### Post by Mauro22 on 2008-10-12
Te lo dije por experiencia, tuve que sacar el recpetor infrarrojo (tengo la misma sintonizadora, la ENLTV-FM) y al tener el receptor ese enchufado cualquier "señal" de cualquier controla (o veces solo) mostraba el cuadro de salir.

Como no le encontre solucion tuve que desistir. Si no podes hacerlo, cambialo de lugar, cosa que no quede tan a la "vista"

---

### Post by sebastianabate on 2008-10-12
A lo mejor esta anécdota mía aplica en el caso de ustedes:

Hace un tiempo estaba "arreglando" la pc de una amiga (y pongo arreglando entre comillas porque lo que estaba haciendo era reinstalarle el XP) y al momento de probar su placa sintonizadora, que ahora no me acuerdo la marca, me dí cuenta que cuando presionaba la tecla de avanzar canales del control de la placa, **se me quedaba sin sonido la TV** (o volvía el sonido si ya estava en mute). El tema era que justo la frecuencia de esa tecla en el remoto de la placa era igual a la del mute de mi TV.

Por esto les pregunto, ¿puede ser que la aparición de la ventana de cerrar sesión coincida con el uso del control remoto de otro equipo en las inmediaciones? y digo inmediaciones porque los remotos se puede usar sin tener visión directa con los aparatos (soportan rebote, por decirlo de alguna manera).

---

### Post by Mauro22 on 2008-10-12
Exacto, a diferencia de tu caso, A mi me aparecia esa pantalla con cualquier boton de cualquier c. remoto...


Hice lo mas facil, y lo saque y listo :D

---

### Post by chulelinux on 2008-10-12
Tal cual como decís Mauro... y esta info no la encontré por ningún otro lado¡¡¡¡. Gracias¡¡¡¡ Reinicié el equipo, le apunte con el control del TV viejo que tengo y zás.. se me abrió la ventana y empieza a colgarse o a trabarse el sistema... Y debe ser así con toda señal que da vueltas ja ja Ahora desconecté el infra... pero quiero tb desinstalar la placa porque me deja la línea de audio siempre abierta y no lo pude solucionar con el par de formas que encontré: que comandos pongo en la terminal pa desinstalar la placa? 
Voy a seguir investigando a ver si se puede arreglar la instalación de esta placa o si se ocurre algo por allí bienvenido sea...

---

### Post by Mauro22 on 2008-10-12
Si usas tvtime. podes usar este script para que ponga mudo o lo saque de forma automatica.


```

#!/bin/bash

amixer set Mic unmute
tvtime
amixer set Mic mute

```


cambia Mic por donde este la entrada desde la placa sintonizadora a la PC. puede ser Mic, Line, etc...


Para crear un script es facil.

* Crea un archivo de text comun y pega lo anterior. Guardalo y Cerralo.
(Podes guardarlo con el nombre que quieras, como tv)

* Le haces click derecho, solapa Permisos y marca la opcion de "Permiter ejecutar el archivo...". Cerras el cuadro de propiedades.

* Haces Alt + F2 y pones gksudo y te vas a la carpeta /usr/bin

* Copia y pega el archivo que hiciste antes en esa carpeta

* Abri una consola (o, sino, Alt + F2) y pones el nombre del archivo que creaste, por ejemplo tv

---

### Post by chulelinux on 2008-10-12
Como hago para tener permiso y poder pegar el scrip en la carpeta usr/bin?

---

### Post by chulelinux on 2008-10-12
Salvo lo del control pude hacer todo y me anda la encore apagando el sonido y todo ... Gracias nuevamente. Solo dos consultas: ahora siempre tengo que ejecutar a tvtime desde alt/f2 para que ande el script del sonido? Y por otro, ¿Para entrar como root siempre hay que cambiar de sesión?, porque cuando escribo por terminal con los comandos para ser superusuario, después en modo gráfico igual no me deja actuar como superusuario. Disculpen si es una pavada lo que pregunto pero leí y leí y me confunde un poco, y la verdad que hasta que le agarre la lógica al SO seguro me voy a seguir confundiendo...

---

### Post by Mauro22 on 2008-10-12
Para lanzarlo desde, podes crear un lanzador en el escritorio y donde diga "comando" pones el nombre del archivo. (Si esta en /usr/bin, solo el nombre, sino la ruta completa)


Lo de root o superusuario tenes 3 formas:

En la consola, si pones sudo antes del comando, no estas siendo root sino que tenes previlegios de superusuario.
En la consola, si pones sudo su, ahi te convertis en root pero solo en la consola activa.

Para ser root general, tenes que:

* Darle un password a root con el comando: passwd root
* El GDM por default no deja loguearse con root, asi que lo tenes que activar...


Pero te digo, con sudo y en algunos casos sudo su, es mas que suficiente. Tener una cuenta root es peligroso y nunca debe usarse como si fuera la de un usuario.

---

