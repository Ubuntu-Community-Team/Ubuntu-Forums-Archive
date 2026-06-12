---
title: "Problemas para reproducir dvd con Totem. Ubuntu 9.04"
date: 2009-06-22
forum: Software
---

### Post by Foxtrot_35 on 2009-06-22
Hola aMigos, soy nuevo en Ubuntu...y saben? ya tengo algunas dudas...habrá alguién que me pueda ayudar???....les cuento, tengo el ubuntu 9.04 y no hay caso que no pueda reproducir dvd con el Totem y descargue el dragon player y nada....he visto en foros y descrgados codecs  etc etc etc...que puede pasar?...lo mismo ocurre para poder ver páginas con contenidos JAVA como el chat...hice lo mismo...busqué...y nada...creo que algo falta...
Ojalá alguien me  pueda ayudar...desde ya...Muchas Gracias

---

### Post by bichopro on 2009-06-23
Hola..
Agrega estos repositorios, busca la aplicacion terminal y copia pega y enter, cuando te pida la contraseña tecleala y enter tambien.

aqui van os comando en el orden que corresponde:

> sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

> sudo apt-get install libdvdcss2

y finalmente...

> sudo apt-get install w32codecs

o si tienes un ubuntu de 64...

> sudo apt-get install w64codecs

y tb puedes instalar en añadir y quitar el paquete ubuntu-restricted-extras

---

### Post by Carlos C on 2009-06-23
> **Foxtrot_35 said:**
> Hola aMigos, soy nuevo en Ubuntu...y saben? ya tengo algunas dudas...habrá alguién que me pueda ayudar???....les cuento, tengo el ubuntu 9.04 y no hay caso que no pueda reproducir dvd con el Totem y descargue el dragon player y nada....he visto en foros y descrgados codecs  etc etc etc...que puede pasar?...lo mismo ocurre para poder ver páginas con contenidos JAVA como el chat...hice lo mismo...busqué...y nada...creo que algo falta...
Ojalá alguien me  pueda ayudar...desde ya...Muchas Gracias

Un título como "Una ayudita por favor" no es muy descriptivo de tu problema. Por favor evita publicar threads con títulos como esos y escoge uno que de una idea de tu problema. Por otro lado, tu consulta obviamente no corresponde al subforo comunidad. Los nombres de los subforos son bastante descriptivos y si tienes dudas he dejado un stick en cada uno señalando lo que puedes publicar en ellos.

Por favor lee el siguiente thread para evitar estos inconvenientes:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Procedo a editar el título y mover el thread.

---

### Post by CdK1 on 2009-06-23
sudo apt-get install vlc

---

### Post by Eddy_Kine on 2009-06-29
Sabes, sin querer salirme del tema, Totem es bastante practico para ver DVD, sin embargo tiene algunos problemas con los menús de inicio del DVD. Fuera de eso, pues es genial, al igual que vlc, me gusta usarlo cuando quiero tocar un solo tema de mi colección de musica, es practico ya que no te carga las playlist o librerias.

---

### Post by CdK1 on 2009-06-29
La gracia del FS es que tiene suna gran cantidad de programas para hacer "lo mismo", para ver DVDs, como ya te dije, te recomiendo VLC o XINE, para demás, MPlayer. Otra cosa si ya solucionaste tú problema, avisa para cerrar este thread....

---

### Post by nopersona on 2009-06-29
SMPlayer tiene soporte para los menús de dvd y trabaja con mplayer, es una interfaz muy buena. Además, si usas nvidia de la serie 8, tiene soporte vdpau, para una mejor reproducción, funciona de maraviilas.

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

Saludos.

---

### Post by paneo on 2009-11-01
> **bichopro said:**
> Hola..
Agrega estos repositorios, busca la aplicacion terminal y copia pega y enter, cuando te pida la contraseña tecleala y enter tambien.

aqui van os comando en el orden que corresponde:







y finalmente...



o si tienes un ubuntu de 64...



y tb puedes instalar en añadir y quitar el paquete ubuntu-restricted-extras

Me re-sirvio esto. Ahora se ven completos los DVDs y re-bien.
Que pasen bien.

---

