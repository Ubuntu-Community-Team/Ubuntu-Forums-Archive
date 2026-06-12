---
title: "Levantar Win XP instalado en disco, desde Virtual Box"
date: 2009-09-07
forum: Software
---

### Post by erdaseq on 2009-09-07
Hola que tal, a todos, soy nuevo en este mundo, tal ve mi pregunta es muy basica para ustedes, pero quiero que me ayuden

Les comento que tengo instalado Ubuntu en una partición y win xp en otra.
Estoy usando ubuntu e instale Virtual-Box. Lo que queria saber es si puedo levantar el Sistema Operativo instalado en la otra particion (XP) desde VBox, se puede?

o tengo que levantar un ISO?

si tengo un ISO, con que herramienta grabo mi SO Win XP,para despues levantarlo.
Gracias...

---

### Post by Eduardo Natali on 2009-09-07
Hola,

Haces una imagen del sistema que tenés instalado, y luego en GNU/Linux con VMWare Player levantas la imagen, fijate que acá te dice que formatos de imagenes podes utilizar:

[http://www.vmware.com/products/player/features.html](http://www.vmware.com/products/player/features.html)

Use 3rd-party virtual machines and images

Open Microsoft virtual machines, Symantec Backup Exec System Recovery (formerly called Live State Recovery) images, Norton Ghost 10 images, Norton Save & Restore images, StorageCraft ShadowProtect images, and Acronis True Image images. In this process, the initial virtual machine or image is left untouched in its native format and any modifications are saved in a much smaller VMware-formatted file that is linked to the initial image.

Saludos Edu..

---

### Post by guillermolisi on 2009-09-07
> **Eduardo Natali said:**
> Hola,

Haces una imagen del sistema que tenés instalado, y luego en GNU/Linux con VMWare Player levantas la imagen, fijate que acá te dice que formatos de imagenes podes utilizar:

[http://www.vmware.com/products/player/features.html](http://www.vmware.com/products/player/features.html)

Use 3rd-party virtual machines and images

Open Microsoft virtual machines, Symantec Backup Exec System Recovery (formerly called Live State Recovery) images, Norton Ghost 10 images, Norton Save & Restore images, StorageCraft ShadowProtect images, and Acronis True Image images. In this process, the initial virtual machine or image is left untouched in its native format and any modifications are saved in a much smaller VMware-formatted file that is linked to the initial image.

Saludos Edu..
Pero el interesado usa Virtual Box, no Vmware ....

Hay que leer mejor las consultas :)

---

### Post by EnriqueK on 2009-09-07
Creo mas bien que se refiere a usar desde Ubuntu mediante VirtualBox su actual instalaciñin de Xp y no una imagen que se pueda sacar y que obligaría a instalar si se quiere conservar los datos que se editen.
El caso es que yo tambión estuve en estas averiguaciones y aparentemente solo se puede lograr con Vmware y la forma mas simple es con Vmware Workstation que es de pago, pero también se puede con Vmware Player que es gratuita , pero es bastante mas trabajoso de lograrlo, en la red vas a encontrar tutoriales , pero repito que solo se puede con Vmware, al meos por ahora y supongo que será cuestión de tiempo para que se pueda con VirtualBox.

---

### Post by erdaseq on 2009-09-08
Hola chicos? gracias por las respuesta, pude realizarlo, lo que fue Virtualizar la particion
en mi caso C:\, y enlazarla con una Maquina Virtual que cree con VBox,

[http://casidiablo.net/correr-windows-preinstalado-sobre-ubuntu/pagina-comentarios-3/#comments](http://casidiablo.net/correr-windows-preinstalado-sobre-ubuntu/pagina-comentarios-3/#comments)

[http://www.taringa.net/posts/linux/1611488/Virtualizar-particion-existente-de-Windows-en-Linux!!!.html](http://www.taringa.net/posts/linux/1611488/Virtualizar-particion-existente-de-Windows-en-Linux!!!.html)


esta es con VmWare  (no la probe todavia)
---------------------------
[http://www.kriptopolis.org/virtualizar-una-particion-windows-ya-existente](http://www.kriptopolis.org/virtualizar-una-particion-windows-ya-existente)

En mi caso, me resulto la opcion 1, pero dicen que es muy riesgoso. Ya que lo tengo que realizar en 12 Pcs, usaria el caso de grabar la Imagen de XP personzalizado y levantarlo con VMWare Player (optare por esta)

Estamos en un proceso en que lo usuarios se tienen que pasar a OpenSource, y esta seria una alternativa temporal. 

Saludos 

Ernesto

---

