---
title: "[COMO] Instalar y Configurar AWN"
date: 2007-10-24
forum: Software
---

### Post by Timbis on 2007-10-24
Para los que quieran tener la barra dock como la de mac os, aqui les dejo el link al blog donde lo explican. Muy Completo
[http://blogdeellow.blogspot.com/2007/07/dock-en-linux-al-estilo-leopard.html](http://blogdeellow.blogspot.com/2007/07/dock-en-linux-al-estilo-leopard.html)

---

### Post by spg76 on 2007-10-24
Ese tutorial está un poco desactualizado.
Para instalarlo en Gutsy se puede agregar el repositorio de reocard que está bastante actualizado. Para esto ingresar en una teminal:
```
gksudo gedit /etc/apt/sources.list
```
Agregar la siguiente línea al final:
```
deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```
Y por último correr:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

### Post by Timbis on 2007-10-24
siiii, perdon, despues encontre una version mas nueva y no habia que hacer tanto lio

---

### Post by DavidRnR on 2007-10-24
Yo tengo funcionando todo joya....compiz, etc...

Voy a Sistema---preferencias---  Awn Manager ..........hago clic y no pasa nada.

Esta bien el primer codigo?

[PHP]wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -[/PHP]

Poruqe me tira un error.

david00@CDM-UBUNTU:~$ wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O- | sudo apt-key add -
--01:01:22--  [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
           => `-'
Resolviendo download.tuxfamily.org... 88.191.250.18
Conectando a download.tuxfamily.org|88.191.250.18|:80... conectado.
Petición HTTP enviada, esperando respuesta... 404 Not Found
01:01:23 ERROR 404: Not Found.

gpg: No se han encontrados datos OpenPGP válidos
david00@CDM-UBUNTU:~$ 



El ultimo codigo lo descargo y joya. 
[PHP]sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr[/PHP]

Pero me parece que me falta ese codigo que cargue bien.

Alguna sugerencia? Graciassssss

---

### Post by dj_isaco on 2007-10-24
mira david yo lo instale con este tutorial y me anda de 10
[http://tuxpepino.wordpress.com/2007/08/01/instalar-avant-window-navigator/](http://tuxpepino.wordpress.com/2007/08/01/instalar-avant-window-navigator/)
suerte

---

### Post by sajnox on 2007-10-24
> **DavidRnR said:**
> Yo tengo funcionando todo joya....compiz, etc...

Voy a Sistema---preferencias---  Awn Manager ..........hago clic y no pasa nada.

Esta bien el primer codigo?

[PHP]wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -[/PHP]

Poruqe me tira un error.

david00@CDM-UBUNTU:~$ wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O- | sudo apt-key add -
--01:01:22--  [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
           => `-'
Resolviendo download.tuxfamily.org... 88.191.250.18
Conectando a download.tuxfamily.org|88.191.250.18|:80... conectado.
Petición HTTP enviada, esperando respuesta... 404 Not Found
01:01:23 ERROR 404: Not Found.

gpg: No se han encontrados datos OpenPGP válidos
david00@CDM-UBUNTU:~$ 

Lo que estas haciendo es descargar un llave publica, pero evidentemente tenes mal el link ya que no lo encuentra.

¿De donde lo sacaste? Deberias tener problemas al actualizar apt-get

Eso es el repo de Treviño no?? Alguien sabe si actualizo para Feisty, la verdad que todavia no lo invstigue, pero tampoco vi que salga en ninguno de mis sites de informacion amigos

---

### Post by DavidRnR on 2007-10-24
> **dj_isaco said:**
> mira david yo lo instale con este tutorial y me anda de 10
[http://tuxpepino.wordpress.com/2007/08/01/instalar-avant-window-navigator/](http://tuxpepino.wordpress.com/2007/08/01/instalar-avant-window-navigator/)
suerte

Muchas Gracias!...Segui el segundo paso y se instalo perfecto!:lolflag:

---

### Post by Hernán-Amaya on 2007-10-24
tengo un pequeño problemita con el awn no me toma todos los iconos del sistema, los dos reveldes iconos son el de la papelera y el de mostrar el escritorio

uso el tema OSX_MOD
[http://www.gnome-look.org/content/show.php/OsX_MoD?content=54851](http://www.gnome-look.org/content/show.php/OsX_MoD?content=54851)

---

### Post by Mataca on 2007-10-24
Hernan me pasa lo mismo... la papelera se resiste viteh !!!
pero no es nada q me mate

---

### Post by Hernán-Amaya on 2007-10-24
no es tema de vida o muerte pero bueno ya lo solucionaremos
jejejejeje

---

### Post by jairoalejandros on 2010-08-28
Acá hay un tutorial
[http://www.youtube.com/watch?v=WgHO3zNdYMs](http://www.youtube.com/watch?v=WgHO3zNdYMs)

---

### Post by ketzelleshelle on 2010-10-02
Instalé AWN en la RC de Maverick, pero tengo un problema que me tuvo toda la tarde y no le encuentro la vuelta: se me abren dos paneles de AWN, uno encima del otro (y uno más peque&#324;o que el otro).

Alguna sugerencia o ayuda? Gracias!

Edito: descubrí que no se abre dos, sino TRES veces...

---

