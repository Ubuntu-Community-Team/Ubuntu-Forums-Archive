---
title: "Algunas consultas simples"
date: 2009-03-25
forum: Software
---

### Post by tinoq3 on 2009-03-25
Buen día gente, los molesto con algunas consultas que imagino son fáciles pero no le encontré la vuelta todavía:

1- Logré hacer funcionar speedy con los tutoriales que figuran acá (muchas gracias :biggrin:), el tema es que en cada inicio de sesión por defecto toma la conexión cableada. Probé eliminándola pero siempre vuelve a estar. La idea es dejar por defecto Speedy y si es posible con conexión automática.

2- Tengo instalado Ubuntu en un PATA viejo y funciona de diez, XP en un SATA. Por defecto, por lo poco que entiendo, linux monta automáticamente el disco SATA. El problema surge al crear lanzadores a carpetas de win dentro del disco, ya que cuando inicio siempre figuran rotos... como puedo montarlo de forma permanente?


PD: Instalé Quake 3 con éxito! :lolflag:  (ahora me falta hacer andar el sonido)

Desde ya muchas gracias!

---

### Post by tinoq3 on 2009-03-27
cri cri

:confused:

---

### Post by Hei Ku on 2009-03-27
1- Postea tu archivo /etc/network/interfaces y el resultado de tipear ifconfig en la consola

2- No depende del tipo de disco, sino del tipo de particion y si la monta o no automaticamente. Por lo general, no se recomienda ejecutar sobre particiones NTFS.

---

### Post by guillermolisi on 2009-03-27
> **tinoq3 said:**
> Buen día gente, los molesto con algunas consultas que imagino son fáciles pero no le encontré la vuelta todavía:

1- Logré hacer funcionar speedy con los tutoriales que figuran acá (muchas gracias :biggrin:), el tema es que en cada inicio de sesión por defecto toma la conexión cableada. Probé eliminándola pero siempre vuelve a estar. La idea es dejar por defecto Speedy y si es posible con conexión automática.

2- Tengo instalado Ubuntu en un PATA viejo y funciona de diez, XP en un SATA. Por defecto, por lo poco que entiendo, linux monta automáticamente el disco SATA. El problema surge al crear lanzadores a carpetas de win dentro del disco, ya que cuando inicio siempre figuran rotos... como puedo montarlo de forma permanente?


PD: Instalé Quake 3 con éxito! :lolflag:  (ahora me falta hacer andar el sonido)

Desde ya muchas gracias!
Para que no te tome la red por cable desenchufa la interface, dejala sin el cable para que el NM no note que en ese adaptador de red hay señal y lo intente conectar.
Igual con lo que pidio HeiKu vamos a tener un panorama mas detallado para darte una mano.

Para montar una particion NTFS en forma permanente necesitas modificar el /etc/fstab.

---

