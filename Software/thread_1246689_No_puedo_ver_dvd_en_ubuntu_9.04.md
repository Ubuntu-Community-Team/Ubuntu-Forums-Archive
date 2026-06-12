---
title: "No puedo ver dvd en ubuntu 9.04"
date: 2009-08-22
forum: Software
---

### Post by soichirutk on 2009-08-22
Hola que tal despues de poder actualizar ubuntu 8.04 a 9.04 me encontre con algunos problemas que aun no he podido resolver con respecto a reproducir dvd, ya que ningun reproductor me permite ver el contenido de algun dvd. En ubuntu 8.04 si podia ver el dvd aunque la desventaja era que no podia entrar a los menus de capitulos, y a veces no podia adelantar el video. 

No se a que se deba que en ubuntu 9.04 lo que hace es abrir el reproductor y cerrarlo enseguida y si no algunos me manda un error de que no se puede reproducir el formato ..

Gracias

---

### Post by rubioo on 2009-08-22
Tenes que tener los codecs.
Los podes bajar desde medibuntu que es un repositorio donde podemos encontrar algunas aplicaciones y codecs que no son instalados por defecto en Jaunty.

Añadimos el repositorio de MEDIBUNTU:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Añadimos la clave del repositorio:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Para la reproduccion de DVD ejecutamos:

```
sudo apt-get install libdvdcss2 libdvdread4
```

Para instalar Windows codecs, Real Networks, Quick Time y otros:

Para Ubuntu 9.04 32 bits ejecutamos:

```
sudo apt-get install w32codecs
```

Para Ubuntu 9.04 64 bits ejecutamos:

```
sudo apt-get install w64codecs
```

Instalar otros codecs adicionales:

```
sudo aptitude install non-free-codecs
```

---

### Post by Carlos C on 2009-08-22
He movido el hilo al subforo software. Por favor, soichirutk, recuerda publicar en el subforo adecuado. He publicado, en cada uno de ellos, un post en donde explico lo que corresponde publicar en las diferentes categorías. Te pido que leas las normas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos.

---

### Post by AlvaroV on 2009-08-22
A mi me ocurrió lo mismo con los videoa cuando me cambie a 9.04 encontre esta solución  [https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/020018.html](https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/020018.html)       


La solución esta al final del mensaje.

---

### Post by soichirutk on 2009-08-30
> **AlvaroV said:**
> A mi me ocurrió lo mismo con los videoa cuando me cambie a 9.04 encontre esta solución  [https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/020018.html](https://lists.ubuntu.com/archives/ubuntu-ar/2009-May/020018.html)       


La solución esta al final del mensaje.

Pues no me queda otra que agradecerte esta respuesta ya que soluciono el problema que tenia, probe el otro metodo pero me aparecia el mensaje de que no se encontraba el medibuntu-keyring.

Pero ya parece resuelto el problema vientos

---

### Post by maxmoraga on 2009-08-31
Yo tuve el mismo error ayer cuando me cambie a 9.04, y descubrí que ocurre al actualizar el paquete xserver-xorg-video-intel, así que luego de formatear nuevamente decidí no actualizarlo ya que ni siquiera tengo t.video intel.

Saludos.

---

