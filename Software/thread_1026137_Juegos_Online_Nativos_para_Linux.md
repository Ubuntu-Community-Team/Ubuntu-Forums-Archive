---
title: "Juegos Online Nativos para Linux"
date: 2008-12-30
forum: Software
---

### Post by NickCis on 2008-12-30
Navegando por Taringa, me encontre con esta pagina [http://www.historiasdequeso.es/2008/05/se-puede-jugar-en-gnulinux.html](http://www.historiasdequeso.es/2008/05/se-puede-jugar-en-gnulinux.html) , en la cual muestran muchos juegos nativos para LInux.

Los que me interesaron fueron:
[* Daimonin]("http://www.daimonin.com/")
[* CrossFire]("http://crossfire.real-time.com/")
Por lo que vi, para el CrossFire, te podes bajar un deb, para instalarlo entonces no hay problema. Pero para el Daimonin, hay que compilar, cosa que nunca hice (o siempre me tiro error), alguien sabe que tengo que instalar para que cuando ponga Make no me diga que no encuentra el archivo makefile?.

Ademas, alguien alguna vez jugo a estos juegos?, conocen servers para jugar online?, hay mucha gente jugandolos?.

Saludos.

---

### Post by Hei Ku on 2008-12-30
Probablemente tengas un README o INSTALL que te diga que comandos poner para compilar.

Lo más probable es que sea ./configure

PD: Movido a software

---

### Post by NickCis on 2008-12-30
Lei, el readme, me dice que hay que ahcer "sh ./configure", lo hago pero el error sigue pasando. Puede ser que nececite algo mas que las "build-essentials"?

Saludos.

---

### Post by MeduZa on 2008-12-31
> **NickCis said:**
> Lei, el readme, me dice que hay que ahcer "sh ./configure", lo hago pero el error sigue pasando. Puede ser que nececite algo mas que las "build-essentials"?

Saludos.

para poder compilar necesitas las build-essentials y posiblemente te pida otras librerias!
de todas maneras antes de compilar fijate si no esta ya compilado en synaptics o en la pagina getdeb.net

---

### Post by Hei Ku on 2008-12-31
Y necesitamos el error exacto que te da. Aunque no lo creas, pueden dar muchos errores distintos y cada uno tiene una solución diferente. ;)

---

### Post by totolinux on 2008-12-31
hola pero crossfire esta compilado en gestor de paquetes synaptic. es mas simple

---

### Post by faktorqm on 2008-12-31
> **MeduZa said:**
> para poder compilar necesitas las build-essentials y posiblemente te pida otras librerias!

Si, para comprar lapices y biromes! yo creo que el necesita BIBLIOTECAS, no librerias.... 

antes de compilar, como dijo aca totolinux, siempre tenes que hacer

```
apt-cache search crossfire
```

entonces te aparece algo como esto:

```
faktorqm@the-edge:~$ apt-cache search crossfire
crossfire-client - Sound server for the game Crossfire
crossfire-client-gtk - GTK Client of the game Crossfire
crossfire-client-gtk2 - GTK2 Client of the game Crossfire
crossfire-client-images - Base crossfire-client images
crossfire-client-sounds - sound files for playing crossfire
crossfire-client-x11 - XLib Client of the game Crossfire
crossfire-common - Common files for Crossfire
crossfire-doc - Documentation for Crossfire
crossfire-edit - Map editor for the Crossfire Gameset
crossfire-maps - Standard set of maps for crossfire
crossfire-maps-small - Small set of maps for crossfire
crossfire-server - Server for Crossfire Games
faktorqm@the-edge:~$ 

```

entonces a partir de aca solo haces 

```
sudo apt-get install <nombre_del_paquete>
``` y listo!!

Salu2!

---

