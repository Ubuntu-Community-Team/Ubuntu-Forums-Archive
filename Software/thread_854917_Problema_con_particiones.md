---
title: "Problema con particiones"
date: 2008-07-09
forum: Software
---

### Post by loopeando on 2008-07-09
Ultimamente ando con algo de tiempo libre y con ganas de probar otra distro. Elegi openSUSE 11 y libere un poco de espacio de mi particion de datos para instalarlo ahi quedando mi tabla de particiones asi:

[IMG]http://img75.imageshack.us/img75/9301/screenshotde2.png[/IMG]

sda1 = / de Ubuntu
sda2 = /home de Ubuntu
sda3 - sda5 = Swap
sda4 = /Depot (mi particion de datos)

Como se ve en la imagen libere 10GB para instalar SUSE pero el tema es que GParted no me deja crear una particion primaria para instalarlo en los 10GB de espacio libre diciendome que ya tengo el maximo de 4 particiones primarias cuando tengo 3 en realidad. Les dejo un screen del error:

[IMG]http://img236.imageshack.us/img236/9471/screenshot1dg7.png[/IMG]

Basicamente lo que quiero es que mi instalacion de Ubuntu no sufra ningun tipo de alteracion cuando instale SUSE.

¿Como hago para crear la particion primaria para SUSE?

Gracias!

P.D: No estaba seguro de donde postear esto, si esta en el lugar equivocado sepan disculpar.

---

### Post by Mister X on 2008-07-10
> Como se ve en la imagen libere 10GB para instalar SUSE pero el tema es que GParted no me deja crear una particion primaria para instalarlo en los 10GB de espacio libre diciendome que ya tengo el maximo de 4 particiones primarias cuando tengo 3 en realidad.

Ya tenes las cuatro creadas, la swap (sda5) es una particion logica que está dentro de una extendida, que  en sí es una primaria (sda3).
El espacio sin particionar lo tenes que asignar a una particion logica (sda6) dentro de la extendida, lo que realmente no sé es si te va a dejar crear la particion logica dentro de la sda3 ya que en medio tenés otra primaria.

---

