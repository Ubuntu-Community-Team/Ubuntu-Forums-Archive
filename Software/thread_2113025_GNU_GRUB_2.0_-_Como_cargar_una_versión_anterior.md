---
title: "GNU GRUB 2.0 - Como cargar una versión anterior"
date: 2013-02-06
forum: Software
---

### Post by JimJazz on 2013-02-06
Hola Comunidad,

De antemano muchas gracias, les explico mi problema, estuve realizando unas actualizaciones y cambio en mi ubuntu 12.10 y sin querer cambie algo que provoco que el sistema ahora no pueda iniciar la parte grafica, he intentado varias cosas para solucionarlo pero no he podido, entonces recurri a entrar en el menu de opciones avanzadas del grub y seleccione una versión anterior de ubuntu (3.5.0.22-generic) y funciona bien, mi consulta es la siguiente, como puedo hacer para que esta versión pase a ser la "ultima" y no la que toma actualmente (3.7.0-7-generic) o como puedo compararlas para saber que es lo que tengo diferente entre estas versiones para poder reparar la que toma ahora como ultima.

No se si puse bien esto, si no es así, pido disculpas!!:lolflag:

---

### Post by JimJazz on 2013-02-08
[IMG]http://www.divideyvenceras.es/galeria/memes/okay-meme.png[/IMG]

---

### Post by JimJazz on 2013-02-11
Nadie sabe como hacerlo :confused: o no me explique bien :(

---

### Post by asterix77 on 2013-02-13
Está un poco abandonado un poco el forum parece.
Haber si te te entendí bien, con el kernel 3.7.0.7 no puedes iniciar el entorno gráfico, pero si seleccionas el kernel 3.5.0.22 si puedes arrancar el modo gráfico.

¿En el 3.7 en que se detiene el proceso?¿te aparece una pantalla negra esperando alguna orden?. Si puedes ejecutar comandos escribe para iniciar el entorno gráfico lo siguiente:

sudo service lightdm start

Si no puedes ejecutar este comando intenta realizar estos pasos:

a) control + alt + F1
b) login
c) contraseña
d) sudo services lighdm start

Si esto no te funciona puedes eliminar el kernel que te da problemas (siempre y cuando tengas acceso a la consola), con el siguiente procedimiento:

[http://ubunlog.com/eliminar-kernels-antiguos-en-ubuntu/](http://ubunlog.com/eliminar-kernels-antiguos-en-ubuntu/)

Espero que te pueda servir, saludos

---

