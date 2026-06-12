---
title: "como hacer ubuntu mas rapido"
date: 2008-11-03
forum: Software
---

### Post by tsueseres on 2008-11-03
hola, convenci a un amigo de instalar ubuntu le dije algo k antes me habian dicho de que ubuntu se adapta el sistema pero ahora no estoy muy seguro de que sea verdad ya que cuando lo instalo le corria un poco mas lento, hay alguna manera de hacer que ubuntu corra mas rapido?

---

### Post by c4d0rn4 on 2008-11-03
sacale la indexación de archivos y los modulos de servicio que no usa (bluetooth si no tiene por ejemplo) y si le metés cosas esteticas correlas con *nice COMANDO*.
[[IMG]http://img377.imageshack.us/img377/4006/trackerix2.th.png[/IMG]](http://img377.imageshack.us/my.php?image=trackerix2.png)[[IMG]http://img377.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

te dejo una screen porque no tengo idea de como se llaman las opciones en castellano o donde están.

Supongamos le metés awn, ponele al inicio no awn sino *nice awn* como comando a ejecutar y así. Si tenés conky bajale el refresh

Si es media batata la pc, sacale el compiz y el fondo de pantalla tmb. Y podes tmb quitarle los applets que no use en las barras.

---

### Post by valucha on 2008-11-03
[COLOR="DarkOrchid"]SI anda muy muy lento posiblemente no puedas aumentar mucho la velocidad.
Por qué no tratás usando xfce?[/COLOR]

---

### Post by hictio on 2008-11-03
Cambia de Desktop Environment.
Googlea Fluxbox, OpenBox o BlackBox (son Window Managers ultra rapidos que usan muy pocos recursos)
Esto es quizas demasiado extremo, pero si tenes tiempo, la experiencia de hacer el recorrido es bien valida: [Installation on Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Digo, aunque no tengas tan poco RAM, es una buena excusa para hacer una instalacion "limpia", sin un monton de extras, e ir progresando de alli.

---

### Post by mhoyos on 2008-11-03
> **tsueseres said:**
> hola, convenci a un amigo de instalar ubuntu le dije algo k antes me habian dicho de que ubuntu se adapta el sistema pero ahora no estoy muy seguro de que sea verdad ya que cuando lo instalo le corria un poco mas lento, hay alguna manera de hacer que ubuntu corra mas rapido?

hola..

para poder ayudarte.. podrias describir el hardware que estas usando ?? como tambien que version de Ubuntu estas y/o estabas usando ??

como tambien, que "agregados" tenes (si es que existen) en el escritorio, y/o los servicios/aplicaciones que estas usando...

salu2

---

### Post by tsueseres on 2008-11-03
> **mhoyos said:**
> hola..

para poder ayudarte.. podrias describir el hardware que estas usando ?? como tambien que version de Ubuntu estas y/o estabas usando ??

como tambien, que "agregados" tenes (si es que existen) en el escritorio, y/o los servicios/aplicaciones que estas usando...

salu2

ram creo k es 128 o 256  ddr1

procesador pentium 4

disco duro particion para ubuntu 10GB

---

### Post by hictio on 2008-11-03
Hay posibilidad de agregarle mas RAM? 128 es muy, muy poco para un Ubuntu normal; es mas, creo que debe ser 256, porque sino la instalacion les deberia haber costado mucho.
Mi desktop es un Pentium II @ 350 MHz, pero se puede "usar" porque le puse 512 MB de RAM; ojo es lento; pero queria probar Ubuntu.
Sino le podes agregar mas RAM, yo te diria de hacer una instalacion de Ubuntu Server, no le instales nada, cuando te ofrece que instalar, y despues de terminada, le instalas el Desktop Environment que quieras, pero para 128 MB, yo te recomendaria algo como FluxBox o similar.

---

### Post by User21 on 2008-11-03
Proba instalando [**Xubuntu**]("http://www.xubuntu.com") desde su [disco alternate]("http://torrent.ubuntu.com/xubuntu/releases/intrepid/release/alternate/xubuntu-8.10-alternate-i386.iso.torrent"), y si lo seguis sintiendo lento, instalate Fluxbox, a ese Xubu... 
```
sudo apt-get install fluxbox
```
Sino, que se compre algo mas de RAM. No queda otra.

---

### Post by valucha on 2008-11-05
[COLOR="DarkOrchid"]Posiblemente le hayas puesto Ubuntu porquew me imagino que habrá tenido un WIndows super viruseado que andaba re lento.
Probá con otras distros, como Zenwalk, y otras que ahra no me acuerdo, hay mucha sy están muy bien desarrolladas cosa que ya no se necesita mucha comptadora y son lindas y usables.

Saludos[/COLOR]

---

### Post by NickCis on 2008-12-19
Yo hace poco hice una instalacion asi, para una maquina de tambien 128mb, y lo que te recomiendo es que o instales el LXDE (googlea LXDE) o el Ubuntu Lite (que usa el LXDE).
Si usas Openbox, nececitas ponerle muchos complementos para que sea usable (por ej, no tiene barra de herramientas,).
Otro es Ice Wm, que lo encontre muy feo y dsp Flutebox, no me gusto para nada.
Encambio, Lxde, es simple, no es feo, y si venis de Windows te va a resultar muy comodo.
Esta es la pagina de Lxde: [http://lxde.org/](http://lxde.org/) (en este link te dice como instalarlo: [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu))
Y esta es la de Ubuntu Lite: [http://u-lite.org/?q=node/2](http://u-lite.org/?q=node/2)

Aunque, ahora opte por comprarle mas ram (actualmente tiene 512mb) y pienso instalarle el Xubuntu 8.10 para probar.

Saludos.

---

### Post by andy_91 on 2008-12-20
yo quise instalar ayer u-lite y no pude me decía error del servidor???

---

### Post by KrossX on 2008-12-21
[COLOR="Navy"]Quizá el servidor estaba caído por algún motivo.[/COLOR]

---

