---
title: "Problema al instalar Ubuntu 10.04 con GRUB2"
date: 2010-06-04
forum: Software
---

### Post by Thalskarth on 2010-06-04
Buenas, estoy teniendo un problema con el GRUB2 tras instalar Ubuntu 10.04.

En mi PC tengo instalado ArchLinux y tengo el disco particionado de esta forma:

[IMG]http://www.graphicshost.net/images/xbbvc86dwfae2x.png[/IMG]

En donde el /, /boot, /var y /home son los correspondientes a Arch. El **Ubuntu sería instalado en /dev/sda8** como su / y el /home va junto al de Arch en sda6.

Paso a comentar bien el caso, el LiveCD me carga perfecto, e incluso puedo instalar el Ubuntu sin dramas en una partición.
El problema es que, luego al reiniciar el sistema nunca puedo bootear, ya que al momento en que debería cargar el GRUB2, se me queda la pantalla en negro con un guion titilando. Entonces no puedo hacer nada.

Mediante un livecd, recuperé el grub1 de mi arch y booteo en ese sistema, pero no logro hacer bootear a Ubuntu, ya que este usa GRUB2 y no lo puedo "invocar" desde el GRUB1 de arch.
A su vez, probé usando SuperGrubDisk2 para solucionarlo, pero tengo el mismo problema de GRUB2 y nunca me bootea :mad:

Alguno sabe como se puede solucionar esto? o como hacer para instalar Ubuntu con el grub-legacy?

Muchas Gracias


PD: dicho sea de paso, durante la instalación de Ubuntu este nunca reconocé a Arch.

---

### Post by alfplayer on 2010-06-05
Quedó seleccionado instalar Grub 2 en /dev/sda en la instalación de Ubuntu ? Hay un botón para elegir dónde se instala abajo a la derecha en la pantalla con el texto de resumen de las opciones elegidas.

---

### Post by Thalskarth on 2010-06-06
> **alfplayer said:**
> Quedó seleccionado instalar Grub 2 en /dev/sda en la instalación de Ubuntu ? Hay un botón para elegir dónde se instala abajo a la derecha en la pantalla con el texto de resumen de las opciones elegidas.

Sí, la primera vez no le di bola, al segundo intento verifiqué que efectivamente estuviese seleccionado.

---

### Post by Thalskarth on 2010-06-08
Pero para avisar que he probado otras distros con GRUB2 y tampoco me andan. El problema parece ser del GRUB2 en mi PC.

Así que reitero la pregunta, exite alguna forma de instalar Ubuntu directamente con GRUB-legacy???

O de, después instalado, cambiarle el GRUB por GRUB-legacy desde algún LiveCD???

---

