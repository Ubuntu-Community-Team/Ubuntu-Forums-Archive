---
title: "Actualicé Windows y desapareció grub"
date: 2009-11-10
forum: Software
---

### Post by ketzelleshelle on 2009-11-10
Tenía instalado Windows XP y Ubuntu 9.10 en la misma laptop.
Ahorá actualice a Windows 7 y no inicia el grub.
Cómo hago para rescatar Ubuntu?

Muchas Gracias

---

### Post by rubioo on 2009-11-10
Lo que paso es que cuando instalaste Windows, escribio la MBR y borro GRUB.
Te dejo una explicacion de como tenes que [Recuerar GRUB]("http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB")

---

### Post by Tosh78 on 2009-11-10
Si, es como te dice rubioo. Lo ideal siempre es instalar windows primero y despues instalar Ubuntu, ya que Ubuntu detecta si estas usando otros sistemas operativos, pero Windows no.
Si tenes algun problema con la guia, avisa y te damos una mano.

---

### Post by ketzelleshelle on 2009-11-10
Use el SuperGrub pero no pasa nada. Vuelve una y otra vez al comienzo para volver a empezar.
Se supone q este programa deber{ia volver a instalar Grub o lo tengo q usar cada vez que quiero arrancar?
Gracias.

---

### Post by pablo.s on 2009-11-10
Creo que el Super GRUB Disk
no sirve para GRUB 2.
Podes probar con el LiveCD
de 9.10, en una terminal escribi:

```
sudo os-prober
```
```
sudo update-grub
```

---

### Post by ketzelleshelle on 2009-11-10
No tengo el Live CD de 9.10... puedo hacerlo con 9.04?
O me tengo que bajar el cd sin más?
Muchas gracias.

---

### Post by ramiro_md on 2009-11-10
> **ketzelleshelle said:**
> No tengo el Live CD de 9.10... puedo hacerlo con 9.04?
O me tengo que bajar el cd sin más?
Muchas gracias.

Con cualquier live cd de Ubuntu :)

---

### Post by rojojuan on 2009-11-10
Podés probar con entrar a Synaptics (Sistema-Administración) y marcar grub-pc para reinstalar. En mi caso lo hice, respondí las preguntas  y sobreescribió todo ok.

---

### Post by pablo.s on 2009-11-10
> **ramiro_md said:**
> Con cualquier live cd de Ubuntu :)

No, muchachos, valga la aclaracion
que debe ser de 9.10, porque la
version 9.04 tiene GRUB Legacy...

La propuesta de Rojojuan me parece
que puede ser lo que funcione.

---

### Post by rubioo on 2009-11-10
En el apartado 13. Reinstalling GRUB 2 from the LiveCD, de [URL="http://ubuntuforums.org/showthread.php?t=1195275"]The Grub 2 Guide
(formerly Grub 2 Basics)[/URL] dice como hacerlo (esta en ingles).

---

### Post by ketzelleshelle on 2009-11-13
Muchachos: este foro me ha sido de gran ayuda muchas veces. Hay gente que sabe mucho y mucha más gente con muchas ganas de ayudar.
El problema es que a veces cuando las ganas de ayudar son muchas y los conocimientos medios, las respuestas suelen ser confusas y una pérdida de tiempo.
Personalmente siempre prefiero buscar las respuestas acá o en algún que otro foro experto en el tema, pero tengo que decirles como una crítica constructiva que lamentablemente todas las respuestas de aquí me hicieron dar vueltas sobre lo mismo sin solución y la respuesta la encontré... en [Taringa]("http://www.taringa.net/posts/linux/1224132/Reinstalando-el-Grub-de-Ubuntu-sin-programas.html").
La solución era supersencilla y lo hice sin problemas.

Dejo aquí la solución:

Lo primero es iniciar la computadora con el CD de instalación de Ubuntu, iniciamos una terminal y tecleamos lo siguiente:

sudo grub

find /boot/grub/stage1

en mi caso me regreso el valor (hd0,6) ese valor lo vamos a necesitar en el siguiente paso.

root (hdx,y)

donde x es el primer valor devuelto en el paso anterior (en mi caso un 0) e y es el segundo valor (después de la coma y en mi caso un 6), básicamente esto indica el lugar donde ya se encontraba instalado grub y sus archivos de configuración que generalmente es la partición root ( / ) de nuestro Ubuntu.

setup (hd0)

Eso instalará grub en nuestro primer disco duro (hd0) , que es con el que inicia la computadora.

Luego rebooteamos y listo.

Agradezco siempre la ayuda, pero tratemos entre todos de ir a lo seguro.

K.

---

### Post by josecuervo86 on 2009-11-13
Perdoname que discienta, pero todos las respuestas que te dieron solucionaban el problema. De cualquier manera tampoco consultaste, en el supuesto caso de que hayas seguido alguna y no te haya dado resultado. En este foro debe haber quinticientos threads abiertos referidos a la misma temática, asique de ultima podrias haber buscado en alguno en el cual se haya informado que se resolvio para reproducirlo en tu caso.

Saludos!

---

### Post by ketzelleshelle on 2009-11-13
Gente: esto fué sin ánimo de ofender, siempre agradezco la buena voluntad, solo que a veces pienso que para ayudar hay que estar bien seguro.

JoseCuervo: con el Supergrub probé y no dió resultado, postée aqui el inconveniente.
Me sugirieron escribir unos comandos en un terminal desde live CD pero tampoco funcionó.
Me dijeron que era con cualquier Live CD, después que solo con 9.10.
Entré a Synaptic y trate de reinstalar pero tampoco me funcionó.
Después me mandaron al apartado 13 de The Grub 2 Guide...era el apartado 12 no el 13, pero tampoco me dió resultado.

A esto me refiero, esto me pasó varias veces en distintos foros expertos en el tema (como este). Si mi crítica está fuera de lugar algún moderador la borra y listo.

El tema está solucionado y postée la solución que a mi me dió resultado.

Gracias.

K.

---

### Post by guillermolisi on 2009-11-13
> **ketzelleshelle said:**
> Gente: esto fué sin ánimo de ofender, siempre agradezco la buena voluntad, solo que a veces pienso que para ayudar hay que estar bien seguro.

JoseCuervo: con el Supergrub probé y no dió resultado, postée aqui el inconveniente.
Me sugirieron escribir unos comandos en un terminal desde live CD pero tampoco funcionó.
Me dijeron que era con cualquier Live CD, después que solo con 9.10.
Entré a Synaptic y trate de reinstalar pero tampoco me funcionó.
Después me mandaron al apartado 13 de The Grub 2 Guide...era el apartado 12 no el 13, pero tampoco me dió resultado.

A esto me refiero, esto me pasó varias veces en distintos foros expertos en el tema (como este). Si mi crítica está fuera de lugar algún moderador la borra y listo.

El tema está solucionado y postée la solución que a mi me dió resultado.

Gracias.

K.
Este no es un "foro experto", es un foro especifico que no es lo mismo y en ningun lado dice que la gente que participa es "experta" por que tal cosa no existe, siempre habra alguien que sabe mas y alguien que sabe menos en valores relativos.

En algo coincido y es en que si no se conoce el tema, mejor no decir nada. Luego, es cierto que muchas veces la actitud le puede ganar al raciocinio pero siempre se aprende algo, particularmente de los errores.

Tema finalizado y gracias por tus comentarios que deben ser tomados de buena forma por todos los que han participado como experiencia para proximas oportunidades.

---

