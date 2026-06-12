---
title: "Excesivo consumo de cpu"
date: 2009-08-19
forum: Software
---

### Post by jagrock on 2009-08-19
Hola ubunteros,

Estoy mis disgustado con el rendimiento obtenido en la actual version de ubuntu jaunty jackalope, resulta que hasta hace un tiempo usaba ubuntu 8.04 hardy heron amd64 y volva mi maquina que es un acer aspire 4535, ahora con 9.04 adm64 el rendimiento es deplorable...

El consumo de CPU mostrado por el monitor de sistema en ocaciones alcanza un 100% y normalmente se mantiene sobre el 40% sin ninguna razon aparente.

Las caracteristicas de mi laptop son:

Turion 64 x2 (2.1 ghz)
3 GB ddr2 @ 667mhz
320 gb sata
Ati radeon hd3200 

La tarjeta de video esta con los controladores fglrx activados y funcionando, de hecho estoy corriendo compiz y va horrible... mi disco duro esta con ahci por las dudas...

¿Que estara pasando?

---

### Post by anarko on 2009-08-19
Tu problema es el compiz, los drivers de ATI fglrx ponene el micro al 100% cuando habilitas el compiz. Deshabilita los efectos de escritorio y vas a ver como queda el micro al 0%. Ami me pasaba exactamente lo mismo, yo tenia una HD3650 y no hubo forma de hacerlo andar razonablemente bien al driber de fglrx y compiz juntos.

Je je justo que posteo veo mi firma, mira lo que tengo puesto en la firma. Hacia mucho que no entraba al foro, desde que compre la nVidia

---

