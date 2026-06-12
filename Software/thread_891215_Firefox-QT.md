---
title: "Firefox-QT"
date: 2008-08-15
forum: Software
---

### Post by Mauro22 on 2008-08-15
Hola!!

Aunque es una version de prueba, al parecer el proyecto va muy bien. Se trata de Firefox adaptado totalmente a KDE usando QT.

PD: Seguro que los KDEistas :D entenderan mas las ventajas/desventajas de QT, etc, etc, etc... :D. 
Yo 0% KDE

Pasos:

```
sudo aptitude install mecurial
``` ```
sudo aptitude install libidl-dev libqt4-core libqt4-gui libqt4-dev libasound-dev autoconf2.13
``````
hg clone http://hg.mozilla.org/users/vladimir_mozilla.com/mozilla-qt mozilla-qt
``````
autoconf
``````
./configure &#8211;enable-application=browser &#8211;enable-default-toolkit=cairo-qt &#8211;enable-debug=&#8221;-g3&#8243; &#8211;enable-tests &#8211;disable-installer &#8211;disable-crashreporter &#8211;disable-javaxpcom &#8211;disable-printing &#8211;disable-embedding-tests &#8211;disable-elf-dynstr-gc
``` ```
make -j3
``` ```
cd dist/bin
``````
./firefox
```Sacado de: (Mas info y screenshot)
[http://swik.net/Ubuntu/Planet+Ubuntu/Jussi+Schultink:+Testing+Firefox+QT/ccj5n](http://swik.net/Ubuntu/Planet+Ubuntu/Jussi+Schultink:+Testing+Firefox+QT/ccj5n)  (Ingles)

---

### Post by Hei Ku on 2008-08-15
Para KDE, la ventaja de esto es que no hace falta cargar librerias de Gnome para usar Firefox. Ademas, las librerias de Qt tienen mas funciones, asi que Firefox se hace mas liviano. Para la parte mobile, y es por lo que Nokia puso plata para esto, permite correr firefox en telefonos y dispositivos moviles que corran Qt. Ahi es donde esta la papa del asunto.

Mas info: [http://dot.kde.org/1218543988/](http://dot.kde.org/1218543988/)

---

### Post by leo_rockway on 2008-08-17
[http://browser.garage.maemo.org/news/10/](http://browser.garage.maemo.org/news/10/)

Screenshots!

---

