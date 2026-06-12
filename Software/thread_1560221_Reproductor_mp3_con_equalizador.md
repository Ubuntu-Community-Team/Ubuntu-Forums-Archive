---
title: "Reproductor mp3 con equalizador"
date: 2010-08-24
forum: Software
---

### Post by diegol3d on 2010-08-24
Les quiero consultar tambien por algun reproductor de musica mp3 que me aconsejen porque el que viene con el ubuntu no trae ecualizador.
Saludos.

---

### Post by leonardomdq on 2010-08-24
Hola diego, el reproductor DeadBeeF tiene equalizador.
Para instalarlo en Ubuntu Lucid Lynx:
```

sudo add-apt-repository ppa:alexey-smirnov/deadbeef
sudo apt-get update
sudo apt-get install deadbeef
 
```

---

### Post by sartrejp on 2010-08-25
Acá explican como agregarle un equalizador a rhythmbox
[http://dmnet.bitacoras.com/archivos/debian/ecualizador-para-rhythmbox.php]("http://dmnet.bitacoras.com/archivos/debian/ecualizador-para-rhythmbox.php")
Suerte

---

### Post by diegol3d on 2010-08-25
Muchas gracias leonardo ;)  una pregunta sartrejp: no encuentro la ruta [B]~/.gnome2/rhythmbox/plugins/  
[/B]ya me baje el archivo y lo descomprimi, pero no encuntro esa ruta. con el buscado de archivos encontre una ruta pero no estoy seguro si tengo que descomprimir ahi. esta es:** /usr/share/doc/rhythmbox-plugins**.  Pero como no estoy seguro no hice nada. prefiero que me digan los que saben.

---

### Post by leonardomdq on 2010-08-25
Por nada Diego, DeadBeeF es mucho mas liviano y completo que Rhythmbox pero gustos son gustos.
Volviendo a la instalacion de Plugin la ruta es [B]~/.gnome2/rhythmbox/plugins/
[/B]Fijate que que el directorio **.gnome2** que esta en tu home es oculto, para visualizarlo tenes que presionar **Ctrl+H**[B] .
[/B]

---

### Post by diegol3d on 2010-08-25
Hola leonardo. debo estar haciendo algo mal, porque no logro dar con esa carpeta. dentro del Home encontre la carpeta .gnome2, pero dentro de la misma no encuentro la carpeta **rhythmbox. **no se que estoy haciendo mal.[B]

[[IMG]http://img844.imageshack.us/img844/4927/pantallazot.th.png[/IMG]]("http://img844.imageshack.us/i/pantallazot.png/")


[/B]

---

### Post by leonardomdq on 2010-08-25
Proba creandola la carpeta en tu home

```
mkdir -p $HOME/.gnome2/rhythmbox/plugins/
```

Luego pones el plugin que descargaste dentro de la carpeta plugins.

Cabe aclarar que todos los plugins se  activan y configuran dentro de rhythmbox en el menu Editar,  Complementos, ademas de que ningun plugin surtira efecto hasta reiniciar  rhythmbox. 

Avisa como te fue.

---

### Post by diegol3d on 2010-08-25
Muchas gracias leandro. te cuento que puse tal cual me dijiste vos y me lo reconoce pero no me funca. asi que me baje el DeadBeeF y estoy muy contento. muy amable leandro!

---

### Post by sartrejp on 2010-08-25
Cuando lo activás, se te habilita el botón de configuración a la derecha.
Igual ya está solucionado, así que podemos dormir tranquilos.
Saludos!

---

### Post by diegol3d on 2010-08-25
Asi es, se me habilita, voy a configuracion y toque lo que toque no cambia nada. Con el DeadBeeF estoy muy contento, lo unico que me gustaria es ponerlo en 24 bits ya que poseo una creative x-fi. y cuando pongo un mp3 me lo toma a 16 bits. igual es un detalle, estoy mas que conforme.

---

