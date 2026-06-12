---
title: "Problemas al instalar sistema de monitoreo"
date: 2009-09-04
forum: Software
---

### Post by johersa on 2009-09-04
Saludos a todos los compañeros de la lista.

He tratado de instalar un sistema de monitoreo para redes, el cual se llama opsview, en los requerimientos de software mencionado en la pàgina señala ubuntu hardy, el problema que tengo es que luego de instalar el sistema operativo y de haber configurado los repositorios para el mismo, cuando quiero instalar me da como respuesta que dicho paquete no existe.

root@monitoreo:/# apt-get install opsview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package opsview

¿Alguien tiene alguna idea al respecto?  De antemano gracias por sus comentarios.

---

### Post by Carlos C on 2009-09-04
Hola. Por favor recuerda publicar tus dudas en el subforo adecuado. En cada uno encontrarás un thread, que está como sitcky, en el que se especifica lo que corresponde publicar en ellos.

En caso de tener dudas te recomiendo que leas las normas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Movido al subforo "Software".

Respecto a tu pregunta, me da la impresión de que estás tratando de instalar un paquete que no está en los repositorios oficiales, por lo que necesitas añadir el repo adecuado antes de que puedas instalarlo mediante apt-get. Dices que configuraste los repos para el programa, sería bueno saber cómo lo hiciste, ya que, en caso de que esté bien configurado es tan simple como que el nombre del paquete no es el correcto o simplemente el paquete no está.


Saludos.

---

### Post by kamus on 2009-09-04
> **johersa said:**
> Saludos a todos los compañeros de la lista.

He tratado de instalar un sistema de monitoreo para redes, el cual se llama opsview, en los requerimientos de software mencionado en la pàgina señala ubuntu hardy, el problema que tengo es que luego de instalar el sistema operativo y de haber configurado los repositorios para el mismo, cuando quiero instalar me da como respuesta que dicho paquete no existe.

root@monitoreo:/# apt-get install opsview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package opsview

¿Alguien tiene alguna idea al respecto?  De antemano gracias por sus comentarios.

Creo que ese paquete no forma parte de los repositorios oficiales de ubuntu, me imagino que agregaste los sources del proyecto y luego actualizaste tus fuentes (apt-get update)?, bueno no se exactamente que tipo de monitoreo estas buscando pero te puedo recomendar ntop, nagios, cacti ;)

Saludos

---

### Post by johersa on 2009-09-05
Gracias por la aclaratoria con respecto a donde postear correctamente, no sabia donde colocarlo.

Con respecto a los repositorios, los instale siguiendo las instrucciones de:
[http://docs.opsview.org/doku.php?id=opsview:apt]("http://docs.opsview.org/doku.php?id=opsview:apt")
 

Link de plataformas soportadas:
[http://docs.opsview.org/doku.php?id=opsview3.2:platforms#web_browsers]("http://docs.opsview.org/doku.php?id=opsview3.2:platforms#web_browsers")

**Ubuntu	8.04 (Hardy Heron)	x86/x86-64	Supported**

pero al tratar de instalar me da error por paquete desconocido.

---

### Post by moreback on 2009-09-05
Dentro del depósito indicado por el enlace puedo ver que existe un paquete llamado opsview:

[http://downloads.opsera.com/opsview/apt/community/pool/main/o/opsview-core/opsview_3.3.0.2987-1hardy1_all.deb](http://downloads.opsera.com/opsview/apt/community/pool/main/o/opsview-core/opsview_3.3.0.2987-1hardy1_all.deb)

Esto me lleva a pensar que no estás ejecutando el comando **sudo apt-get update** o simplemente ingresaste mal la línea en el /etc/apt/sources.list.

Saludos.

---

