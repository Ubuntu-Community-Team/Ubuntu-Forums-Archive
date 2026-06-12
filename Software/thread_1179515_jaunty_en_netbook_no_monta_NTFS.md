---
title: "jaunty en netbook no monta NTFS"
date: 2009-06-05
forum: Software
---

### Post by rubenb on 2009-06-05
Netbook MSI con jaunty y una partición ntfs.
Desde la primera vez, al intentar montar la partición muestra cartel:

No es posible montar el volumen
Detalles: Cannot get volume.fstype.alternative

Revisando en launchpad veo que es un tema marcado como bug en tres casos (uno de ellos es 313770), pero no encontré forma de solucionarlo.

Si busqué mal, y la respuesta estaba ya posteada, por favor copienme el link

Muchas gracias.
Ruben.-

---

### Post by staar on 2009-06-05
y montándola a través de fstab directamente? en una Terminal ```
sudo gedit /etc/fstab
``` y agregar esta línea al final ```
/dev/sda*x* */punto/de/montaje* ntfs-3g defaults,locale=es_AR.UTF-8 0 0
``` reemplazando sda*x* por el correspondiente a la partición (con sudo fdisk -l podés ubicar el nombre), y */punto/de/montaje* por el directorio donde deseas montarla (comúnmente /media/disco o /media/windows o el que quieras, ese directorio tiene que estar creado ANTES de montar la partición) después con ```
sudo mount -a
``` volvés a montar todo...

saludos

---

### Post by fmsismo on 2009-06-06
Que error te tira caundo queres montarlo?

Saludos

---

### Post by rubenb on 2009-06-07
[B]Respuesta para fmsismo
[/B]Desde la primera vez, al intentar montar la partición muestra cartel de error que dice:

[B][I]No es posible montar el volumen
Detalles: Cannot get volume.fstype.alternative[/I][/B]

Alguna idea?

---

### Post by rubenb on 2009-06-07
**Respuesta para staar**

Gracias, **staar**.
Soy un absoluto newbie, muy lejano del uso cómodo de la línea de comandos. Probaré el "minitutorial"
Dos preguntas:
1)
Estas instrucciones me permiten montar esa partición una sola vez? Debo, entonces, montar/desmontar por línea de comandos cada vez que lo necesite?
2)
El bug al que me referí no fue solucionado?
Gracias de nuevo.-

---

### Post by Hei Ku on 2009-06-07
Las instrucciones solucionan el problema también cuando reinicias, y tenes que hacerlo solo esta vez.

---

### Post by rubenb on 2009-06-07
**Respuesta para Hei Ku**

Muchas gracias,   **Hei Ku**. Pruebo el "minitutorial" que **staar** me dejó arriba, cruzo los dedos, y después les cuento.

El bug 313770 no ha sido solucionado? Yo busqué en launchpad y no encontré respuesta, sólo el comentario original del bug.
Gracias otra vez.-

---

### Post by staar on 2009-06-07
ese bug fue marcado como duplicado de este [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443") el que, en teoría, está solucionado y un fix fue lanzado, pero, por los comentarios, al parecer sigue ocurriendo el problema, tu sistema está actualizado?

saludos

---

