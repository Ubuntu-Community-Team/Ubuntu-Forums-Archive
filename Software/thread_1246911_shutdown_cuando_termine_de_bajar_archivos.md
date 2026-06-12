---
title: "shutdown cuando termine de bajar archivos"
date: 2009-08-22
forum: Software
---

### Post by rafaelca on 2009-08-22
Hola ^^

Pues uso "Ubuntu 9.04 Desktop Edition"

Y la verdad que si bajo algo como podría apagarse el PC solo?


Algun programa etc...?

Gracias! ;)

---

### Post by guillermolisi on 2009-08-22
> **rafaelca said:**
> Hola ^^

Pues uso "Ubuntu 9.04 Desktop Edition"

Y la verdad que si bajo algo como podría apagarse el PC solo?


Algun programa etc...?

Gracias! ;)
Fijate que en algunos programas para descarga de archivos se contempla la opcion de apagar la maquina cuando haya terminado la descarga.

(Edito el titulo del thread para que sea mas significativo a su contenido.)

---

### Post by nemodot on 2009-08-22
Ciertamente hay muchos programas que tienen esa opción.

De última podes dejar programado el apagado con un comando como este:

```
sudo shutdown -h +60

```

En el ejemplo está programado para que se apague dentro de 60 minutos.

---

### Post by FB91 on 2009-08-22
yo uso alarm clock (sudo aptitude install alarm-clock) es una simple alarma que la podés programar para que ejecute algún comando cuando pase cierto tiempo...

También podés hacer lo que dice nemodot...

---

### Post by nopersona on 2009-08-22
Especifica qué programa estás usando. Una buena opción sería automatizar todo con Cron.

---

