---
title: "Problema para correr Alien Arena 2009, Ub-JJ"
date: 2009-08-22
forum: Software
---

### Post by r@fitiiixxx on 2009-08-22
Hola a todos,

comento mi problema, no puedo correr el Alien Arena 2009 ya sea desde un acceso directo y desde la consola, solo si entro con el nautilus a la carpeta "/usr/local/games/alienarena2009/"

y hago doble click en el archivo "crx" (ni idea si es un .bin o un .run ... no dice :S)

Mi conf: Ubuntu JJ con GNOME & Compiz Fusion + Emerald
targeta NVIDIA GeFroce 8600 GT 512 mb
```
$ grep -i "x driver" /var/log/Xorg.0.log
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
```
creo está actualizado.

El problema:
cuando me lo bajé por primera vez, un archivo .rar, se me bajó mal y puse a descargar otro mirror por las dudas. lo bajé y lei las instrucciones 

que vienen en el README.txt que decian descomprimir en:

"/usr/local/games" como el urban terror. y para ejecutarlo poner en consola "$ ./crx"

puse ese cmd... y me dice que el archivo o fichero no existe :S

puse la direc completa /usr/local/games/alienarena2009/crx y me larga el siguiente error:
```
nicolas@nicolas-desktop:~$ /usr/local/games/alienarena2009/crx
using /home/nicolas/.codered/data1/ for writing
using /home/nicolas/.codered/arena/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
OpenAL info:
  Vendor:     OpenAL Community
  Version:    1.1
  Renderer:   OpenAL Soft
  AL Extensions: AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_OFFSET AL_LOKI_quadriphonic
  ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_EFX
  Default Device: ALSA Software on default
  Available Devices:
    ALSA Software on default
    ALSA Software on HDA NVidia
    OSS Software
    Wave File Writer
  ALC Frequency: 44100
  ALC Mono Sources: 255
  ALC Stereo Sources: 1
  Generated Source Count: 128
  Generated Buffer Count: 256
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Master server at 74.63.48.146:27900
Sending shutdown to 74.63.48.146:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx
```

Ni bién lo instalé no podía ni iniciarlo con la solución que posteo mas abajo, sin embargo después buscando un poco encontré una solución a parte del error, que era 

"sudo apt-get update" y "sudo apt-get libopenal" pero no funcionó del todo. Intenté con darle permisos "$ sudo chmod +x /usr/local/games/alienarena2009/crx" pero tampoco sirvió.

En un foro encontré que tenía que poner el siguiente cmd para que se me arreglara
> sudo apt-get install build-essential libcurl4-openssl-dev libopenal-dev fakeroot devscripts debhelper dpatch libsdl1.2-dev libglu1-mesa-dev libgl1-mesa-dev libjpeg62-dev libxxf86vm-dev libxxf86dga-dev libxext-dev libx11-dev
y poner "sin configuración" una ves aparezca la opción. Pero tampoco.

por mi parte probé hacer aunque sea un "shortcut" del archivo y ponerlo en el escritorio para tenerlo facil acceso, pero no funcionó ya que le cambié permisos y no he podido hacerlo correr si no.

la unica manera de correr el juego fue, entrar a nautilus a la dirección, "usr/local/games/alienarena2009" y hacer doble click en el archivo ejecutable "crx" para que inicie el juego

y no estoy seguro en que parte de las tantas que probé modifiqué algo como para que lanze por lo menos desde esta solución precaria.

La solución:

 Quisiera poder agregarlo al menú como lo hice con el Urban Terror, solo necesito que corra si lo llamo por consola así me creo un lanzador y lo meto en el panel como a mi me gusta

si no es posible eso, aunque sea un acceso directo en el escritorio. He leido muchos comentarios de problemas con esta nueva versión, parece que es muy problematica. pero acepto cualquier tipo

de ayuda y que conste que lei todo el material que google.com me pudo dar sobre el tema.

si necesitan algun tipo de info de mi sistema me avisan que y como y se los paso, espero que alguien sepa del asunto.

r@fitiiixxx

---

### Post by totolinux on 2009-08-22
Hola mira yo lo he hecho andar, dede ya no dio ningun problema pero siempre lo instale desde los repositorios oficiales y te queda bién.

sudo apt-get install alien-arena
sudo apt-get install alien-arena-data

Opcional
sudo apt-get install alien-arena-dbg
sudo apt-get install alien-arena-server
sudo apt-get install alien-arena-server-dbg


ahora no se, pero me parece que tendrias que desinstalar todo lo que tenias anteriormente pero de esto no estoy del todo seguro. saludos

---

### Post by r@fitiiixxx on 2009-08-22
@totolinux:

Claro, el de los repositorios anda perfecto, pero ese no es este juego, este es el Alien Arena 2009, y no está en los repositorios, modificaron todo el motor grafico, el viejo, que vos bajaste es el 2007 y ya quedo mas feo que hacer la tarea, la gracia era el motor grafico, ya el contenido del juego es pobre, si a eso le sumo graficos pobres me aburro mucho, yo queria chequear el nuevo motor grafico.

la onda es este que está en la pagina

[http://icculus.org/alienarena/rpa/aquire.html](http://icculus.org/alienarena/rpa/aquire.html)

es facil encontrar el link de descarga, es un .rar y lo descomprimis y listo

este nuevo alien arena usa un motor grafico que usa  GLSL, OpenGL Shading Language, una tecnología parte del API estandar OpenGL y han mejorado los volumenes de luz, lo que hace que el juego se vea mucho más real, se ven los reflejos de objetos vidriosos y las sombras en los angulos correctos, también se ha mejorado y cambiado el sonido por completo usando openAL

he probado el juego con bots, ya que no hay casi servers, y es impresionante, me recuerda mucho al DOOM 3, aunque no lo juge mucho, tiene ambientes similares.

en fin es un juego que vale la pena tener en tu disco duro si tenes linux y te gustan los juegos piolas. Eso si nesitas una buena targeta de video. la mia a veces tira algunas bajas, aunque puede que estén influidas por los drivers NVIDIA que no salieron muy buenos para JJ.

pero antes que todo quiero agregar que al problema se le suman mas sintomas:

siempre que inicio el juego se me borra la config y tengo que volver a poner la resolución y los graficos al maximo y la sensibilidad del mouse. se ve que haber copiado esos archivos 
default.cfg
config.cfg (lo inventé, copié un default.cfg y le cambié el nick, por el error de arriba)
en la carpeta "/.codered/data1/"
me "andubo" pero a costa de que no me carga las configuraciones de video, controles y audio.

igual te la habrás gastado bajandote el v2007, se agradece el esfuerzo ;) 

ahora solo necesito de alguien que le alla pasado lo mismo y sepa que me pasa acá. :P

PD: recien vuelvo a las 9 así que no esperen una rta rapida. jeje

r@fitiiixxx

---

### Post by totolinux on 2009-08-22
Disculpame pero creí que el problema es era mas simple. Me encanta el juego pero mis hijos son muy chicos y se vuelven locos con alien-arena y no es recomendado para niños pequeños, asi que desinstale y voy a esperar unos años para jugar denuevo. saludos:(

---

### Post by r@fitiiixxx on 2009-08-22
> **totolinux said:**
> Disculpame pero creí que el problema es era mas simple. Me encanta el juego pero mis hijos son muy chicos y se vuelven locos con alien-arena y no es recomendado para niños pequeños, asi que desinstale y voy a esperar unos años para jugar denuevo. saludos:(

Ojalá dependiera de paquetes deb o de los repositorios, pero es un .rar y no entiendo muy bien su funcionamiento.

Es verdad lo chicos pequeños no deben jugar video juegos de ningun tipo, puede influir en su desarrollo, pero gracias por colaborar ;)

intenté modificar los archivos default.cfg y config.cfg pero no hay caso, no funciona, sigue sin tomarme las configuraciones guardadas,

habrá chance de bajar el Alien Arena viejo que está bien hecho y reemplazar el motor del juego y los demas archivos por los del v2009 para que funcione bien?

r@fitiiixxx

---

### Post by villa77 on 2009-08-24
Acá[1] tenés la versión 7.3-1 que si no me equivoco es el 2009 en .deb.
Fijate si te sirve...
Abrazo!

[1] [http://www.playdeb.net/updates/?q=Arena](http://www.playdeb.net/updates/?q=Arena)

---

