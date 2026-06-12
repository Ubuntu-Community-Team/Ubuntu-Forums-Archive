---
title: "como &quot;upgradear&quot; mi versión de ubuntu"
date: 2008-10-30
forum: Software
---

### Post by Barasuishou on 2008-10-30
verán, hace poco(2 minutos lo leí) me enteré salió la nueva versión de ubuntu 8.10, intrepid "nosecuanto", sory por la ignoracia =P, y quería ver de pasarme a esa versión yo estoy en hardy heron osea 8.04 x64, como hago para pasarme a la nueva???? tengo que formatear ????XS

---

### Post by nahuel_89p on 2008-10-30
creo que basta con ejecutar el comando "sudo apt-get distro upgrade"
Googlea y algo de eso te va a salir.

---

### Post by lega on 2008-10-30
en la pagina de ubuntu tenes una guía para actualizar de la 8.04 a 8.10
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by BlackHero on 2008-10-31
aptitude full-upgrade

---

### Post by niko_3100 on 2008-10-31
cual es la posta??

---

### Post by Zeq on 2008-10-31
Hay un par de maneras como las que mencionan arriba y todas sirven.

Yo personalmente fui a *Sistema > Administración > Origenes de Software*

Y en la pestaña **Actualizaciones**, en la opción '**Actualización de la distribucón**' puse: '**Ediciones normales**'

Y listo, ahora yendo al **Gestor de Actualizaciones** en *Sistema > Administración* te va a salir que está la versión nueva de **Ubuntu** disponible.
Le das a **Actualizar** y listo.

Espero que te sirva

---

### Post by Aspergillus on 2008-10-31
No se como tendras el S.O. en cuanto a customizacion, pero dependiendo de cuan customizado tengas la version que tenes ahora de Ubuntu, el upgrade puede ser un exito total o un desastre total..

si tenes el sistema muy customizado la opcion que te recomiendo personalmente es que guardes todo lo del Home que te sea de interes y demas archivos que hayas retocado vos en el sistema y te bajes una imagen del 8.10 la quemes a un cd e instales de 0

---

### Post by sam_award on 2008-10-31
Zeq tiene toda la razon , ese es el trukin de este rollo , haz eso y tendras tu distri ibex actualizada

---

### Post by sajnox on 2008-10-31
Tenes varias formas de hacer update.

sudo apt-get dist-upgrade (cuando la version fue publicada)
update-manager -d (levanta la interfaz grafica de instalaciones y te permite hacer update desde la primer alpha)

Y seguro que hay mas....

---

