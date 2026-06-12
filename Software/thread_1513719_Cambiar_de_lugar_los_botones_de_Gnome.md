---
title: "Cambiar de lugar los botones de Gnome"
date: 2010-06-19
forum: Software
---

### Post by federico-c on 2010-06-19
Wenas gente, nose que toqe de un tema que me cambio de lugar 

[IMG]http://s3.subirimagenes.com:81/imagen/previo/thump_4688607pantallazo.png[/IMG]
ven el borde arriba, lo de cerrar maximizar y minimizar se me cambio de lugar y me pone loco, como hago para ponerlo como tendria que ir qe es del otro lado, por favor ayudenmee!!! se los voy a re agradecer

---

### Post by alfplayer on 2010-06-20
Hola Federico.

La imagen lamentablemente no ayuda porque su tamaño es muy chico.

---

### Post by atari130xe on 2010-06-20
> **federico-c said:**
> Wenas gente, nose que toqe de un tema que me cambio de lugar 

[IMG]http://s3.subirimagenes.com:81/imagen/previo/thump_4688607pantallazo.png[/IMG]
ven el borde arriba, lo de cerrar maximizar y minimizar se me cambio de lugar y me pone loco, como hago para ponerlo como tendria que ir qe es del otro lado, por favor ayudenmee!!! se los voy a re agradecer


Hola por defecto Lucid Lynx trae los botones de minimizar maximizar cerrar de lado izq. tenès 2 opciones para cambiar eso:

Primera opciòn:
Teclea ALT+F2 y escribi lo siguiente gconf-editor y dale ENTER.
luego que se te abra una ventana con el editor de configuraciòn buscàs a la izquierda la que dice "apps" clickeas encima y al abrirse nuevamente buscàs "metacity" clickeas nuevamente encima y buscas "general" nuevamente clickeas encima y en la linea button_layout dice close,minimize,maximize: doble click encima de esas 3 palabras y las cambias por estas: minimize,maximize,close

cerras y listo.

Segunda opciòn:
Instalàs Ubuntu Tweak y luego vàs a "desktop" "window manager" seleccionas de que lado queres los botones (derecho en tu caso) y listo.
espero te sirva. :)

---

### Post by leonardomdq on 2010-06-21
Otra opción, vas a **Aplicaciones -> Accesorios -> Terminal** :

> 
[INDENT] [B]gconftool-2 --type string --set  /apps/metacity/general/button_layout
"menu:minimize,maximize,close[/B] [/INDENT]


---

