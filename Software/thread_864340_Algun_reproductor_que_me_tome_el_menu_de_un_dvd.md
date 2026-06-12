---
title: "Algun reproductor que me tome el menu de un dvd??"
date: 2008-07-19
forum: Software
---

### Post by niko_3100 on 2008-07-19
Gente que reproductor reproduce peliculas DVD como si fuera un dvd normal? es decir para poner elegir el idioma los subtitulos y ver la peli de corrido? probe el mplayer y no va... el totem reproduce la peli de corrido pero no te deja seleccionar el idioma o minimo los subtitulos.. prove ogle y nada jeje... alguno podria recomendarme un buen reproductor de dvd?? gracias.

---

### Post by Hei Ku on 2008-07-19
Yo uso el Kaffeine sin problemas. 

Fijate que en Synaptics habia un par de paquetes para dvds, que tienen el soporte para menues y algo mas.

---

### Post by niko_3100 on 2008-07-19
El totem tiene para ir al menu y eso pero no funciona, probe on 3 dvd de peliculas y nada....

---

### Post by luks911 on 2008-07-19
Yo tampoco podía con el Totem y para eso VLC. No estoy seguro de si hace falta algún paquete extra para que tome los menús. A veces capaz que le tenés que pegar la ruta donde está montado el dvd que querés ver para que se dé cuenta dónde está, pero funciona.

---

### Post by Hei Ku on 2008-07-19
tenes instalado el paquete libdvdnav4?

---

### Post by ubuntu27 on 2008-07-19
Hola. mplayer is muy complicado. Asi que recomiendo que uses XINE.

```
sudo apt-get install xine-ui
```


No te olvides instalar Codecs necesarios:


Para Ubuntu (Gnome):

**Paso 1. Instalar Paquetes Restringidos:**


```
sudo apt-get install ubuntu-restricted-extras
```

Para Xubuntu (Xfce):

```
sudo apt-get install xubuntu-restricted-extras
```

Para Kubuntu (KDE):
```

sudo apt-get install kubuntu-restricted-extras
```

**Paso 2: Instalar Codecs para DVD:**

  a) Agregar el Repositorio de medubuntu

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

  b) Agregar la llave de GPG 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

  c) Instalar libreria de acceso a DVD encriptado:

```
sudo apt-get install libdvdcss2
```

**Paso 3: Instalar Codecs y formatos no nativos:** Seguir UNO de los siguientes pasos:
 
    a) Si tines Sistema Operativo de 32bit ```
sudo apt-get install w32codecs
```

    b) Si tienes 64bit:
```
sudo apt-get install w64codecs
```

---

### Post by rojojuan on 2008-07-19
Uso el VLC anda de diez.

---

### Post by marianom on 2008-07-20
> **Hei Ku said:**
> Yo uso el Kaffeine sin problemas. 

Fijate que en Synaptics habia un par de paquetes para dvds, que tienen el soporte para menues y algo mas.

+1

Igual creo que el soporte para menu y DVD encriptados (o como se llame) está en los repositorios de medibuntu (o lo estaban en 7.10)

---

### Post by marianom on 2008-07-20
Upps ahí leí el comentario de Ubuntu27 que explica todo...

---

### Post by niko_3100 on 2008-07-20
Bueno... recien probe con un dvd de u2 de un recital como un gil deje las pelis en la casa de mi novia... pero el vlc me tomo todo el mouse hace la funcion del control remoto, una maravilla.... tendria que venir instalado por defecto en ubuntu este reproductor..

---

### Post by faktorqm on 2008-07-21
> **niko_3100 said:**
> Bueno... recien probe con un dvd de u2 de un recital como un gil deje las pelis en la casa de mi novia... pero el vlc me tomo todo el mouse hace la funcion del control remoto, una maravilla.... tendria que venir instalado por defecto en ubuntu este reproductor..

asi es! no se por que no lo ponen, el vlc es lo maximo. salu2!

---

### Post by Tosh78 on 2008-08-14
Gente, ayer me paso lo mismo que a niko, solo que probe con VLC, que es el que uso por defecto, pero no me toma los menues, es decir, aprieto para elegir el idioma y no hace nada, alguna idea de como tengo que hacer para que considere los menues?

---

### Post by luks911 on 2008-08-14
Por si las dudas, ¿tenés instalado el paquete libdvdnav4? 
Saludos

---

### Post by vk-cdg on 2008-08-14
A mi me pasa lo mismo que a Tosh, el DVD de los Backyardigans (para la nena) no me toma los menues. Me parece que es algún paquete que me falta a mi, así que sigo todos los pasos mendionados un par de post mas arriba y les cuento. 
También uso el VLC.

Aprovecho que estamos con VLC (para no abrir un topic nuevo), alguien sabe si hay forma de hacer que tome las teclas multimedia del teclado?
Totem, Exaile y otro mas que tengo toman las teclas multimedia (play, pausa, stop, next y prev) normalmente sin haber hecho nada. VLC nop. :(

---

### Post by Tosh78 on 2008-08-15
Si, me fije y tengo instalado ese paquete. No se por que no funciona el menu :(

---

### Post by luks911 on 2008-08-15
> **Tosh78 said:**
> Si, me fije y tengo instalado ese paquete. No se por que no funciona el menu :(

Caramba, ahí se acaban mis ideas para arreglarlo. Pero se me ocurre una alternativa: usar Mplayer, con ese no ves la pantalla de menús del DVD, pero con un click derecho sobre el programa hay una opción que es DVD y que se abre en títulos, capítulos, pistas de audio y subtítulos. O sea, navegas por el menú pero de otro modo. Tal vez no sea lo mejor, pero... 
Saludos

---

### Post by Tosh78 on 2008-08-18
Bueno, logre algo. El menu aparece, PERO el problema que hay es que no puedo apretar los botoncitos, es como que los botones no tienen links. Por ejemplo, si quiero apretar para ver el capitulo 1, paso el mouse por encima del titulo que dice capitulo 1 y no aparece la manito. Y si de todas formas intento hacer click sobre el titulo 1, no pasa nada. Alguna ayuda o idea?

---

### Post by luks911 on 2008-08-18
> **Tosh78 said:**
> Bueno, logre algo. El menu aparece, PERO el problema que hay es que no puedo apretar los botoncitos, es como que los botones no tienen links. Por ejemplo, si quiero apretar para ver el capitulo 1, paso el mouse por encima del titulo que dice capitulo 1 y no aparece la manito. Y si de todas formas intento hacer click sobre el titulo 1, no pasa nada. Alguna ayuda o idea?

Mmmm... parece que el problema sigue siendo que no reconoce el menú. Leyendo en el foro encontré hace un rato [este post]("http://ubuntuforums.org/showpost.php?p=5610809&postcount=3"), por un problema similar, capaz que te sirve. 
Ahora, al menos para el paquete libdvdcss2 hace falta el repositorio de Medibuntu. Para garegarlo:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

y 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Tosh78 on 2008-08-21
Hola! No se que hacer! Ya hice todo lo que me dicen y ni a palos.

---

### Post by ramiro_md on 2008-08-30
Gente ya que encuentro este tema sobre dvds y peliculas, tengo un problema al reproducir videos. Ya sea con mplayer, totem y vlc, algunas veces suele trabarse la imagen unos segundos, pero el sonido sigue, realmente no sé que podrá ser, mi perfil de maquina es "bueno", es decir, no deberia tener problemas para reproducir videos, y temas de codecs tampoco creo porque sino ni reproduciria. Alguien tiene algo para comentarme ?? gracias =)

---

### Post by luks911 on 2008-08-30
> **ramiro_md said:**
> Gente ya que encuentro este tema sobre dvds y peliculas, tengo un problema al reproducir videos. Ya sea con mplayer, totem y vlc, algunas veces suele trabarse la imagen unos segundos, pero el sonido sigue, realmente no sé que podrá ser, mi perfil de maquina es "bueno", es decir, no deberia tener problemas para reproducir videos, y temas de codecs tampoco creo porque sino ni reproduciria. Alguien tiene algo para comentarme ?? gracias =)

Mmmm... a mí me pasaba pero por falta de RAM. Habría que ver cuánta tenés y qué otras cosas estás ejecutando en al tiempo que reproducís video. Aunque si decís que el perfil de la máquina es bueno.....

---

### Post by ramiro_md on 2008-08-30
Luks gracias por contestar, mira te comento tengo 1 gb de ram, 256 aseginados a video. Con un applet, puedo ver la cantidad de memoria usada (441 de 751 mb) por lo que creo que no es problema de ram, asique sigo en la lucha jejeje xD

---

### Post by ramiro_md on 2008-08-30
Ya que estamos hablando de peliculas y dvds, alguien sabe de un buen ripeador ?? (A) un saludo gente, gracia.

---

### Post by luks911 on 2008-08-30
Dvdrip y en kde k9copy. Tal vez haya alguno más, y nunca usé ninguno así que no te puedo decir qué tal son.

---

### Post by ramiro_md on 2008-08-30
Okey gracias luks, voy a probar ambos.

---

### Post by jpmorelli on 2008-09-01
Para usar Totem con menu, subtitulos, idiomas etc hay que cambiar la versión que viene por defecto con backend de gstreamer por el que trae el motor xine.

sudo apt-get remove totem
sudo apt-get install totem-xine

a esto se le agregan todos los codecs que se nombraron anteriormente y listo !
Igualmente prefiero kaffeine, y VLC segun el DVD trae ese problema de no poder ver algunos menu.
Suerte !

---

