---
title: "No puedo instalar el 9.10"
date: 2010-01-02
forum: Software
---

### Post by Piero71 on 2010-01-02
Hola!!

Ayuda por favor!! pongo el cd de ubuntu 9.10 ("original", me lo mandaron desde Holanda :) ), arranco la máquina desde el cd, elijo idioma español, y luego aparece una lista bastante larga que se va desplazando, y termina en:

[     3.308142]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[     3.308217]  [<c0570be3>] ? error_code+0x72/0x80

y acá se queda. En el teclado, la lucecita de teclado-num queda apagada, y las mayúsculas y bloq.despl quedan parpadeando...

El cd está bien, porque en otra máquina lo instalé sin problemas. Pero, ya que estamos, en la utiidad de disco, selecciono uno de los discos y dice: "Estado SMART: el disco tiene muchos sectores erroneos"

luego:
contador de sectores reubicados: 1035 sectores
contador de sectores pendienrtes: 1 sector

¿se me está "muriendo" el disco? El scandisk de Wincaca dice que está todo bien...

saludos!!

Ale...

---

### Post by luks911 on 2010-01-02
Voy a empezar por lo que sí sé: el error de disco que te aparece en la otra máquina es un bug de la utilidad que comprueba los discos. Hay por ahí otro thread sobre el asunto. Sucede que interpreta como en riesgo un disco que no lo está. Hasta que haya una actualización que lo solucione, podés ignorar el aviso o en la utilidad para comprobar discos desactivar la alarma.

El problema que tenés en la instalación es una incompatibilidad del kernel con algún componente de tu hard. No sé mucho del tema y sería bueno que cuentes detalles de la máquina y si ya le habías instalado otra versión de Ubuntu.
Lo poco que ponés del error es lo mismo que aparece en este bug[0] que es un duplicado de este otro[1]. Si es eso, parece que ya está arreglado pero todavía no está en los repositorios la actualización que lo soluciona (el kernel 2.6.31-17-generic). De todos modos, si no es algo del hard que puedas desactivar (placa wifi, por ejemplo) deberías esperar a que se lance la actualización, instalar un 9.04 y después actualizar desde ahí. Eso, o conseguir que alguien te pase un CD actualizado hecho ad hoc porque el que tenés no te va a servir.
Hasta ahí llega mi conocimiento. 

[0] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454575](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454575)
[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454575](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454575)

---

### Post by Piero71 on 2010-01-04
gracias luks!!!

En dos máquinas me hizo lo mismo, ahora no recuerdo los mothers, pero me fijo bien y te digo. En otras máquinas, usando el mismo CD (9.10) se instaló sin problemas...

garacias y saludos!

---

