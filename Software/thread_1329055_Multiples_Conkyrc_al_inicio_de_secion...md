---
title: "Multiples Conkyrc al inicio de secion..?"
date: 2009-11-17
forum: Software
---

### Post by Fak89 on 2009-11-17
Buenas!
Tengo dos conkyrc (conkyrc1 y conkyrc2), y no puedo hacer que arranquen al inicio de secion! No hay forma jaja
Un screen para que entiendan de que hablo (arriba a la derecha y abajo a la izquierda)..
[[IMG]http://h.imagehost.org/t/0610/Pantallazo.jpg[/IMG]]("http://h.imagehost.org/view/0610/Pantallazo")

Intente creando dos scripts para ponerlos en aplicaciones de inicio, eran asi:
Conky1
```

#!/bin/bash
sleep 10 && conky -c .conkyrc1;

```Conky2
```

#!/bin/bash
sleep 10 && conky -c .conkyrc2;

```Y no paso naranja, le fui aumentando el tiempo del sleep pero no paso nada..

Después intente haciendo un solo scritp como este..
```

#!/bin/bash
sleep 10 && conky -c .conkyrc1 && conky -c .conkyrc2;

```Y tampoco paso nada.. Aclaro que estos los guardaba en /usr/bin y los nombraba como inicio-conky1 e inicio-conky2 y este era el comando que le asignaba a cada uno en aplicaciones de inicio..

Intente sin hacer el script, a cada uno en vez de ponerle inicio conky le ponía el comando y así arrancaba, pero se superponía con las ventanas que abría como era de suponer..

La verdad que hasta ahi llego mi conocimiento jaja.. alguien me podrá tirar una ayuda?

---

### Post by matias_tati on 2009-11-17
Yo tengo dos conkys y lo tengo asi

#!/bin/bash
sleep 15 && conky & sleep 15 && conky -c .conkyrc2

Lo edite con el sig comando:
sudo gedit /usr/bin/inicio-conky

Y mis dos conky se llaman: conkyrc , conkyrc2

Y en programas al inicio agregue:
inicio-conky

Y me lo toma
Es mas en este momento estoy usandom el mismo conky que vos

[[img]http://h.imagehost.org/t/0969/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0969/Pantallazo)

Saludos!!!

---

### Post by Fak89 on 2009-11-17
> **matias_tati said:**
> 
Es mas en este momento estoy usandom el mismo conky que vos

[[IMG]http://h.imagehost.org/t/0969/Pantallazo.jpg[/IMG]]("http://h.imagehost.org/view/0969/Pantallazo")

Saludos!!!

Jaja, si.. creo que lo descargue de aca al conky

> **matias_tati said:**
> #!/bin/bash
sleep 15 && conky & sleep 15 && conky -c .conkyrc2

Ah! buenisimo. Despues le quito el numero a uno y pongo el comando así a ver que pasa..
Gracias por el dato! y, lindo escritorio :P

---

### Post by matias_tati on 2009-11-17
Fijate y copialo tal cual pero fijate que hay un sleep 15 delante del segundo comando qu vos no lo tenes copialo tal cual por las dudas.
Y gracias!!1

---

### Post by Fak89 on 2009-11-17
> **matias_tati said:**
> Fijate y copialo tal cual pero fijate que hay un sleep 15 delante del segundo comando qu vos no lo tenes copialo tal cual por las dudas.
Y gracias!!1

La verdad que no pude.. que raro che!

> #!/bin/bash
sleep 15 && conky **&** sleep 15 && conky -c .conkyrc2

Este esta copiado y pegado? .. como pensaba que iva un ";" intente poniéndolo y también agregando un & .. pero nada xD

---

### Post by matias_tati on 2009-11-18
```
sudo chmod a+x /usr/bin/inicio-conky
```

Quizas no le diste permisos de ejecuciom al script...

Te dejo este enlace que quizas te sea de ayuda tmbn...[http://www.ubuntu-es.org/index.php?q=node/103184](http://www.ubuntu-es.org/index.php?q=node/103184)

Y las caps por si no me crees....

[[img]http://h.imagehost.org/t/0208/Pantallazo.jpg[/img]](http://h.imagehost.org/view/0208/Pantallazo)

[[img]http://i.imagehost.org/t/0060/Pantallazo-inicio-conky_usr-bin_gedit.jpg[/img]](http://i.imagehost.org/view/0060/Pantallazo-inicio-conky_usr-bin_gedit)

[[img]http://i.imagehost.org/t/0461/Pantallazo-matias_Navegador_de_archivos.jpg[/img]](http://i.imagehost.org/view/0461/Pantallazo-matias_Navegador_de_archivos)

Comentame como te fue...

---

### Post by Fak89 on 2009-11-19
Ah! puede ser que no le haya dado permisos de ejecución.. Ahi debe estar el problema xD mas tarde me fijo, gracias! :P

Edit. eso mismo era lo que me faltaba.. ya me estoy olvidando de algunas cosas jaja gracias mati!

---

