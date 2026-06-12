---
title: "Ubuntu 10.04 y ArchLinux (Dual Boot)"
date: 2010-06-28
forum: Software
---

### Post by guidito73 on 2010-06-28
Bueno gente, siendo usuario de Ubuntu desde hace 1 año y medio, me decidí por querer probar Archlinux. Me trae algunas preguntitas el proceso que no he podido saciar del todo en Google.

Sé que Ubuntu instala GRUB2, mientras que en Arch todavía no lo adoptaron, por lo que la instalación me dejaría entre GRUB o no instalar ningun Bootloader. Qué tengo que hacer para que una vez instalado Arch el GRUB2 me reconozca todos los SO correctamente?

Las particiones que tengo actualmente son como subo en el attachment.
La idea sería usar Sda8 y Sda 9 para instalar el / y el /home de Arch (más Gnome).

Consejos, tips, cuestiones a tener en cuenta?

Desde ya, muchas gracias!

PD: Ya instalé Arch una vez, pero no pude levantar el server gráfico, tuve problemas, etc, todo esto en otra PC y con menos conocimientos que ahora, pero el proceso de instalación lo conozco.

EDIT: Como verán, tengo una partición con Windows 7 también.

---

### Post by granjero on 2010-06-29
hola, yo cuando tuve problemas de grub los he solucionado con el supergrubdisk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

ojalá te sirva.

salud!

---

### Post by guidito73 on 2010-06-29
Claro, el problema es que yo quiero mantener GRUB2, y que éste reconozca los 3 SO que voy a tener. Vi por ahí que mucha gente hace una partición aparte para /boot, pero no termino de entender los beneficios de esto (hay gente que le trae problemas para hacer un Dual o Tri boot).

---

### Post by alfplayer on 2010-06-29
Con ubuntu 10.04, con Grub 2, ejecutar *sudo update-grub* detecta y agrega al menú de booteo todas las opciones de todos los sistemas operativos en todos los discos rígidos. Si Grub 2 no lo hace en forma automática, debe hacerse con un editor de texto manualmente (en el foro de Arch seguramente hay información).

---

### Post by guidito73 on 2010-06-30
Bueno, era una cosa de nada, pensé que podía haber problemas pero no.

Luego de instalar Arch, cargué el GRUB2 desde el LiveCD de Ubuntu y listo :)

---

### Post by sancospi on 2010-08-20
Hola, podrías decirme como lo solucionaste siendo un poco mas especifico :D, es que tengo el mismo problema. Gracias

---

