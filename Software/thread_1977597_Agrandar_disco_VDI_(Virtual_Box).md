---
title: "Agrandar disco VDI (Virtual Box)"
date: 2012-05-10
forum: Software
---

### Post by Lio56 on 2012-05-10
Muchach@s

Antes que nada pido disculpas si estoy posteando un nuevo thread sin haber terminado el de la Resolución del monitor. Pregunto se puede hacer un nuevo thread, no?

Ya todos saben que estoy super contento con UBUNTU 12.04, pero para algunas aplicaciones en particular sigo necesitando WinXP.
Averigue y me instale el Virtual BOX, es GENIAL adoro como se instalan los programas en el UBUNTU 12.04 SUPER FACIL.

Cree una maquina virtual con Win XP  instalé todo  y de pronto mi modesto disco VDI de 4Gb se quedó chico. En el momento de creación estoy casi seguro que le di la posibilidad de ampliarlo a futuro.

Vi que se puede ampliar el tamaño pero no entiendo mucho la parte de usar el Gparted... muchos de los post que vi son para el caso que la maquina virtual (creo que le dicen GUEST) es un linux.

Y tampoco entiendo porque tengo que clonar el disco rigido... no era que los estoy ampliando???

Quieren que postee los pasos de algun otro post y en base a eso pregunto mis dudas?

Muchas gracias
Abrazoo
LIO

---

### Post by gmunioz on 2012-05-14
Para vBox 4 en adelante:
Abrir una terminal
Ejecutar

VBoxManage modifyhd "path_al_archivo_de disco/xxxx.vdi" --resize 40000 

40000 son 40 Gigas.

Luego en la máquina virtual hay que expandir la partición para que ocupe el espacio sin asignar, esto lo haces iniciando la máquina con la iso del cd live de gparted cargado en su lector virtual de cd.

---

### Post by Lio56 on 2012-05-30
uyyy esta me parece que es la super posta  cuando llegue a casa lo pruebo :)
graciasss
Saludos 
Lio

---

