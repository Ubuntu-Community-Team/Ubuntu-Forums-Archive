---
title: "desfragmenté windows y desapareció el GRUB"
date: 2011-10-28
forum: Software
---

### Post by drazhe on 2011-10-28
Hola gente de la comunidad, básicamente es eso, des-fragmenté en windows y cuando reinicié la maquina se queda en un ciclo continuo de bios, carga, bios carga, bios carga... y asi hasta que apago la maquina... no da ninguna opción, ningún cuelgue ni aparece nada... solo queda en un ciclo continuo de arranque... 

AYUDA!!

el tema es que no es la primera vez que pasa, ya que la anterior estaba trabajando desde ubuntu con hojas de CALC y cuando reinicio la maquina comenzó con este error... en aquel entonces aproveché y reinstale todo, inclusive el windows y el ubuntu, y recién terminó de instalar y configurar como me gusta y vuelve a aparecer este error... y no quiero reinstalar todo de nuevo...

---

### Post by drazhe on 2011-10-28
bueno, pude recuperar mi grub y el arranque de mi pc siguiendo los pasos mencionados en este sitio

[http://mundogeek.net/archivos/2009/12/08/recuperar-grub-2/](http://mundogeek.net/archivos/2009/12/08/recuperar-grub-2/)

si alguno de los intelectuales de Linux me dice si esta bien lo que hice o si estoy exponiéndome a algo peligroso se lo voy a agradecer... 

por mi parte, es problema solucionado ya que conseguí arrancar los 2 SOs de mi Pc...

---

### Post by guillermolisi on 2011-10-28
Perfecto lo que indica ese tutorial. No warning.
Felicitaciones !!

Que version de Windows estas usando ?

---

### Post by drazhe on 2011-10-28
> **guillermolisi said:**
> Perfecto lo que indica ese tutorial. No warning.
Felicitaciones !!

Que version de Windows estas usando ?

uso windows 7 y ubuntu 10.04 LTS Lucid Lynx... y antes que eso (años atrás xp) pero nunca me pasó algo asi... me refiero a que desapareciera el grub por usar una hoja de calculo o por desfragmentar.... me parece raro que se j****a eso... mas aun teniendo en cuenta que desde windows nunca pude ver las particiones de linux...

---

### Post by guillermolisi on 2011-10-28
Ubuntu esta instalado en una particion aparte de WIndows 7 o utilizaste Wubi ?

---

### Post by drazhe on 2011-10-28
> **guillermolisi said:**
> Ubuntu esta instalado en una particion aparte de WIndows 7 o utilizaste Wubi ?

mismo rigido, distinta partición...

---

### Post by biale on 2011-10-30
Tengo entendido que cada tanto a W7 le gusta tocar el MBR rompiendo así el arranque de Grub. Alguien puede confirmar o agregar algo sobre esto?

---

### Post by drazhe on 2011-10-31
> **biale said:**
> Tengo entendido que cada tanto a W7 le gusta tocar el MBR rompiendo así el arranque de Grub. Alguien puede confirmar o agregar algo sobre esto?

y mirá.. debe ser cierto porque cada 4 o 5 días tengo que reinstalar grub... lo raro es que nunca pude ver particiones de Linux desde windows y el grub está instalado en esa partición...

---

### Post by guillermolisi on 2011-10-31
> **drazhe said:**
> y mirá.. debe ser cierto porque cada 4 o 5 días tengo que reinstalar grub... lo raro es que nunca pude ver particiones de Linux desde windows y el grub está instalado en esa partición...
A pesar de tener instalado Ubuntu en una particion, separado de Windows, GRUB se instala en el MBR (Master Boot Record) del disco rigido. No importa cuantas particiones tenga el disco, solo es posible un solo MBR.

Una forma de que Windows no pise el MBR donde se encuentra GRUB es contar con dos discos fisicos, uno para Win y otro para Ubuntu Linux. De esa forma el MBR del segundo disco no sera tocado por el Loader de Windows.

---

### Post by drazhe on 2011-10-31
> **guillermolisi said:**
> A pesar de tener instalado Ubuntu en una particion, separado de Windows, GRUB se instala en el MBR (Master Boot Record) del disco rigido. No importa cuantas particiones tenga el disco, solo es posible un solo MBR.

Una forma de que Windows no pise el MBR donde se encuentra GRUB es contar con dos discos fisicos, uno para Win y otro para Ubuntu Linux. De esa forma el MBR del segundo disco no sera tocado por el Loader de Windows.

entiendo lo que decís, pero siempre tuve ubuntu y windows con-viviendo en el mismo rígido y en distintas particiones y nunca tuve el problema que estoy teniendo ahora... 
me refiero a que no es la primera vez que des-fragmento windows con ubuntu en otra partición y no tengo otros programas ahora que no tuviera hacer 2 o 3 años cuando comencé con ubuntu y recién ahora comenzó a dar este problema de que desaparezca el grub...

---

### Post by EnriqueK on 2011-10-31
Recomiendo tener el Super Grub2 Disk , pesa muy poco, menos de2 megas, aún así vale la pena gastarse un cd para tenerlo .
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)
booteas con el, -->select any OS--> arrancas Ubuntu, luego para reinstalar el Grub2 ejecuta los siguientes comandos
sudo grub-mkconfig
sudo grub-install /dev/sda
sudo update-grub

---

### Post by guillermolisi on 2011-11-01
> **EnriqueK said:**
> Recomiendo tener el Super Grub2 Disk , pesa muy poco, menos de2 megas, aún así vale la pena gastarse un cd para tenerlo .
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)
booteas con el, -->select any OS--> arrancas Ubuntu, luego para reinstalar el Grub2 ejecuta los siguientes comandos
sudo grub-mkconfig
sudo grub-install /dev/sda
sudo update-grub

Y si no queres ocupar un CD solo por el SuperGrub2, podes usar [Multisystem]("http://liveusb.info/dotclear/") en un pendrive y aprovecharlo mejor con mas cosas, inclusive archivos propios ya que no requiere exclusividad del almacenamiento para funcionar.

---

### Post by drazhe on 2011-11-01
si, leí algo sobre esas aplicaciones mientras tenía el problema y las iba a probar en caso de que las solución que había encontrado usando el livecd no funcionara... ya los tengo bajados para probarlas en futuras ocasiones...

---

