---
title: "ayuda instalar fuentes"
date: 2009-08-01
forum: Software
---

### Post by lexer98 on 2009-08-01
hola chicos de nuevo los molesto xD me baje un paquete de fuentes llamado ''artwiz-aleczapka-de-sources-1.3.tar.bz2'' y no entiendo una parte de las intrucciones en el readme me dice estos para intalar

INSTALLATION
-------------------------------------------------------------------------------
Do the following (example for gentoo):

    cd your_font_dir
    tar xvjf artwiz-aleczapka-<LANG>-<RELEASE>.tar.bz2 
    cd artwiz-aleczapka-<LANG>-<RELEASE>
    fc-cache -fv ./
(de aca para abajo no entiendo) :confused::confused:    
    Add this path to your /etc/X11/XF86Config config
    FontPath "your_font_dir/artwiz-aleczapka-<LANG>-<RELEASE>"

    and fontconfig config file (eg. /etc/fonts/local.conf)
    <dir>your_font_dir/artwiz-aleczapka-<LANG>-<RELEASE>:unscaled</dir>

    restart X

Your installation may vary depending on your distro.

desde ya muchas gracias

---

### Post by pablo.s on 2009-08-01
> **lexer98 said:**
> 
(de aca para abajo no entiendo) :confused::confused:    

De ahi para abajo no
sirven los comandos
que ponen, ya estamos
en 2009.

---

### Post by lexer98 on 2009-08-01
[[URL=http://www.imagebam.com/image/b0791343904974][IMG]http://thumbnails11.imagebam.com/4391/b0791343904974.gif[/IMG]]("http://www.imagebam.com/image/214f7843904666")
[/URL]

---

### Post by pablo.s on 2009-08-01
Ahi tendrias que ejecutar el
script makepcf

```
sh makepcf.sh
```y luego copiar las fuentes en
formato PCF a la carpeta
.fonts de tu usuario, salir de la
sesión y entrar.

EDIT: Si cambiás la
captura de pantalla
aclará, cosa que no 
quede como que estoy
ayudando con cualquier
delirio...

---

### Post by lexer98 on 2009-08-01
sorry , las puse en .fonts y no las detecta , tire el comando para que regenere el cache de la fuentes y no la deteca dice en la carpeta ./fonts que no encontro ninguna

---

### Post by matias_tati on 2009-11-29
Pudiste solucionar este problema?
Acabo de instalar estas fuentes en Ubuntu 9.10
Si queres te ayudo.

---

### Post by matias_tati on 2009-11-29
Es mas estoy usando la fuente "cure" en este momento incluida en este paquete..

---

### Post by leonardomdq on 2009-12-03
Matias esa fuentes esta muy buenas, como hago para instalarlas?

---

### Post by matias_tati on 2009-12-03
Intenta seguir este tutorial:
[http://urukrama.wordpress.com/2008/0...-ubuntu-hardy/](http://urukrama.wordpress.com/2008/0...-ubuntu-hardy/)

Si usas Karmic agrega lo que recomienda este link:
[http://ubuntuforums.org/showthread.p...01#post8410401](http://ubuntuforums.org/showthread.p...01#post8410401)

Y si no podes avisame y te hago una explicacion mas detallada...

Saludos!!!

---

### Post by leonardomdq on 2009-12-03
> **matias_tati said:**
> Intenta seguir este tutorial:
[http://urukrama.wordpress.com/2008/0...-ubuntu-hardy/](http://urukrama.wordpress.com/2008/0...-ubuntu-hardy/)

Si usas Karmic agrega lo que recomienda este link:
[http://ubuntuforums.org/showthread.p...01#post8410401](http://ubuntuforums.org/showthread.p...01#post8410401)

Y si no podes avisame y te hago una explicacion mas detallada...

Saludos!!!
[http://urukrama.wordpress.com/2008/0...-ubuntu-hardy/](http://urukrama.wordpress.com/2008/0...-ubuntu-hardy/)
Page not found :sad:

No te voy a mentir, no entiendo nada...si me guias te agredeceria. Saludos

---

### Post by matias_tati on 2009-12-07
De acuerdo, pero usas Karmic?

---

### Post by leonardomdq on 2009-12-07
Si estoy usando Karmic Koala.

---

### Post by matias_tati on 2009-12-07
Bueno primero nada bajate el paquete de aca.

[http://sourceforge.net/projects/artwizaleczapka/files/iso-8859-1/1.3/artwiz-aleczapka-en-1.3.tar.bz2/download](http://sourceforge.net/projects/artwizaleczapka/files/iso-8859-1/1.3/artwiz-aleczapka-en-1.3.tar.bz2/download)

---

### Post by leonardomdq on 2009-12-07
Ya lo baje al paquete, vos diras que pasos seguir :biggrin:

---

### Post by matias_tati on 2009-12-07
Bueno primero que nada te cuento que solo sigo el tutorial de esta pagina:
[http://urukrama.wordpress.com/2008/05/25/artwiz-fonts-on-ubuntu-hardy/](http://urukrama.wordpress.com/2008/05/25/artwiz-fonts-on-ubuntu-hardy/)

Te traduzco igual:

Descomprimilo y copialo en el directorio /usr/share/fonts/X11/misc
Si no te deja podes hacerlo mediante sudo nautilus en la terminal que te va a abrir un navegador con todos los permisos necesarios...

Luego:

```
sudo fc-cache -f -v
```

```
sudo dpkg-reconfigure fontconfig
```

```
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
```

```
sudo ln -s /etc/fonts/conf.avail/70-yes-bitmaps.conf /etc/fonts/conf.d/70-yes-bitmaps.conf
```

Los ultimos dos pasos los saque de este enlace donde se hablo de un problema en karmic:
[http://ubuntuforums.org/showthread.php?p=8410401#post8410401](http://ubuntuforums.org/showthread.php?p=8410401#post8410401)

Y por ultimo nuevamente:

```
sudo fc-cache -f -v
```

Saludos!!!!

---

### Post by leonardomdq on 2009-12-07
Por fin pude, muchas gracias matias, recien acabo de instalarlas.
Gracias por la mano que me diste.

Saludos

---

