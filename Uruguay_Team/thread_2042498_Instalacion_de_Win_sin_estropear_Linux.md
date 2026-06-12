---
title: "Instalacion de Win sin estropear Linux"
date: 2012-08-14
forum: Uruguay Team
---

### Post by xGrp on 2012-08-14
Buenas a todos, necesito si alguien me puede dar una mano

tengo que usar un programa que solo corre en Win7, ahora hace mucho solo trabajo con xUbuntu 11.10 y lo tengo hecho una pinturita

mi hdd lo tengo particionado asi

  / 
  /swaap 
  /datos
  /datosII

quiero instalar el win7 en /datos 
PERO NO QUIERO ESTROPEAR MI XUBUNTU ANTES DE METER LA PATA alguien que me diga como hacerlo porfa

no quiero experimentar he visto muchos post pero los comentarios desaniman jejeje

y una maquina virtual no me sirve

Gracias

---

### Post by danielmato on 2012-11-05
Win, cuando se empieza a instalar, lo primero que hace es destruir el mbr, o sea, el lugar del grub.

Lo único que se me ocurre, es, crear una distro personalizada o un clonezilla de tu disco, instalar win, reinstalar Ubuntu.

La segunda opción, también muy arriesgada es, instalar win, reinstalar grub con supergrub.

No te puedo garantizar nada.

---

### Post by JoaquinGomez on 2013-03-25
Hola Compañero soy nuevo en El foro pero creo que puedo ayudarte, Si quieres instalar Windows despues de Ubuntu tienen que seguir estos pasos.
1. Para dejar espacio libre para la particion de windows debes entrar al Editor de particiones desde un live cd de ubuntu (desde un live cd porque si se esta usando la particion no te deja editarla) la herramieta se encuentra en: Sistema>Administracion>Editor de particiones
2. luego dentro editas la particion (ext3) dando click derecho sobre la particion y seleccionando `Redimencionar/Mover` y achicas la particion luego le das aplicar y te quedara un espacio sin particionar en ese espacio tienes que crear la particion ntfs de windows cuando estes instalandolo.
3. Instala Windows
4. Esto reescribira el mbr y no cargara el grub para recuperarlo y agregar windows a el grub debes descargar una aplicacion llamada: Super Grub Disk 
Es una imagen iso la descargas desde windows la grabas en un cd o la colocas En un usb son ( 5 mb ) booteas desde esa iso y te aparecera una pantalla con varias opciones elijes super grub disk y le das enter elijes el idioma y llegas a un menu elijes recuperar Gnu/Linux luego: fix boot of gnu/linux y te aparecera una opcion sola y le das enter luego comienza el proceso y solo queda reiniciar para comprobar que efectibamente el grub inicio

Saludos espero que te sirva ;-)  y que la comunidad siga aumentando

---

