---
title: "Ayuda con contraseña de usuario"
date: 2012-02-14
forum: Software
---

### Post by lkzMini on 2012-02-14
Hola gente, hace poco instale ubuntu 11.10
el usuario tenia contraseña y para evitar autentificarme cada ves que queria instalar algo le saque la contraseña, pero me seguia pidiendo contraseña, entonces lo que hice fue apretar enter sin escribir nada y me seguia pidiendo, puse la contraseña vieja pero no funciona, ahora no puedo instalar mas aplicaciones, una ayuda porfavor? :confused:

---

### Post by josephmills on 2012-02-14
> 
Hi folks, I recently installed ubuntu 11.10
the user had to avoid autentificarme password and every time you wanted to install something remove the password, but I was still asking for password, then I did was press enter without typing anything and I was still asking, but I put the old password does not work, now I can install more applications, a help please?
and another thing, everything works except the sound, when I test the speakers in the sound options it hears me, but when I play something I do not play, I'm using the player that includes the operating system, of course thanks

Hola, he intenta esta url? [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
No estoy seguro acerca de su sonido tú. ¿Podría usted por favor, abra su terminal (ctrl + alt + t) e introduzca

```
aplay -L && lsmod 
```

y pegar aquí. gracias


Esperamos traductor de google funciona bien
:)

---

### Post by lkzMini on 2012-02-14
[http://imageshack.us/photo/my-images/403/screenshotat20120215014.png/](http://imageshack.us/photo/my-images/403/screenshotat20120215014.png/)

esa es una imagen y esta es la otra

[http://imageshack.us/photo/my-images/692/screenshotat20120215014.png/](http://imageshack.us/photo/my-images/692/screenshotat20120215014.png/)

sinceramente no entendi nada, asi que espero una ayuda, tengo sonidos pero no tengo idea como reproducirlo en ubuntu, los formatos son propios de windows, mp3 por ejemplo.

---

### Post by josephmills on 2012-02-15
> **lkzMini said:**
> [http://imageshack.us/photo/my-images/403/screenshotat20120215014.png/](http://imageshack.us/photo/my-images/403/screenshotat20120215014.png/)

esa es una imagen y esta es la otra

[http://imageshack.us/photo/my-images/692/screenshotat20120215014.png/](http://imageshack.us/photo/my-images/692/screenshotat20120215014.png/)

sinceramente no entendi nada, asi que espero una ayuda, tengo sonidos pero no tengo idea como reproducirlo en ubuntu, los formatos son propios de windows, mp3 por ejemplo.

 [http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum) 

podría ser capaz de ayudar con la barrera del idioma?

Realmente espero que esto ayude. también se podría tratar de instalar ubuntu-restricted-extras

en terminal (ctrl+alt+t)
```
sudo apt-get install ubuntu-restricted-extras && 
```
then 
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

```

también hay vlc igual que las ventanas
```
sudo apt-get install vlc
```

Espero que esto ayude

---

### Post by guillermolisi on 2012-02-16
> **lkzMini said:**
> Hola gente, hace poco instale ubuntu 11.10
el usuario tenia contraseña y para evitar autentificarme cada ves que queria instalar algo le saque la contraseña, pero me seguia pidiendo contraseña, entonces lo que hice fue apretar enter sin escribir nada y me seguia pidiendo, puse la contraseña vieja pero no funciona, ahora no puedo instalar mas aplicaciones, una ayuda porfavor? :confused:
y otra cosa, funciona absolutamente todo excepto el sonido, cuando pruebo los parlantes en las opciones de sonido me los detecta, pero cuando reproduzco algo no me lo reproduce, estoy usando el reproductor que incluye el sistema operativo, desde ya gracias
Si revisas como estan generadas las consultas podras observar que se intenta desarrollar un tema especifico por hilo.

Si la cuestion que se consulta se puede "patear", entonces se abre el hilo en la seccion Hardware.

Si el tema solo se lo puede insultar, entonces se abre el hilo en la seccion Software.

Y si el tema no es de ninguna de las dos clases anteriores y se puede desarrollar comodamente tomando una cerveza, entonces va en Comunidad.

Siempre un tema por hilo.

Por lo tanto deberias abrir tu consulta en dos:
Una, en Software, por el tema de la contraseña y, la otra, en Hardware por la posibilidad de que te este faltando algun driver, que la placa funciona mal o directamente no funcione, etc.

De esta manera, quienes busquen respuestas a sus problemas podran encontrar hilos concretos, sin necesidad de leer 35 posts que hablen de otra cosa que no es de su interes.

Gracias por tener en cuenta estas recomendaciones en lo sucesivo.

---

### Post by granjero on 2012-02-17
Antes de hacer lo que voy a escribir a continuación, por favor esperá que alguien lo confirme. :D

Booteá un live cd. Navegá en tu disco rígido hasta la carpeta /etc y abrí con un editor de textos el archivo que se llama passwd.

Casi al final vas a ver una linea que empieza con tu nombre de usuario la linea se va a ver algo así:

```
usuario:x:1000:1000:usuario,,,:/home/usuario:/bin/bash
```

Borrá la x que está después de tu usuario guardá y reiniciá tu ordenador.

Cuando inicies tu user no va a tener contraseña. Para agregarle una abri una terminal y ecribí el comando ```
passwd
```

Ingresá una contraseña segura. No "enter"

Las contraseñas no son para molestarnos si no para mantener nuestros datos seguros.

=)

Repito no hagas esto hasta que alguien lo confirme ya que estoy escribiendo de memoria y quizá me falle!

salud!

---

