---
title: "cambio de hora permanente :S"
date: 2008-10-08
forum: Software
---

### Post by Jhonyp on 2008-10-08
La situacion es la siguiente, desde ayer que tengo 2 discos (ambos sata) en uno tengo ubuntu y en el otro vista.

Ambos SO andan perfecto y sin problemas, elijo desde el post con cual bootear (elijo el disco).

Cuando arranco con ubuntu la hora esta perfecta, pero luego booteo con vista y se me cambia la hora (se adelanta varias horas), corrijo este error (actualizo la hora de internet, la zona horaria no se me cambia) pero cuando vuelvo a ubuntu, y luego a vista otra vez se ha cambiado.

Alguna idea?

---

### Post by guisheca on 2008-10-08
En ubuntu, tanto como en otros sistemas *nix está habiendo un problemita con el tema de la hora, supongo que eso tiene algo que ver.
Te dejo este enlace donde se habla del tema:
[http://ubuntuforums.org/showthread.php?t=938859](http://ubuntuforums.org/showthread.php?t=938859)
cualquier cosa preguntá algo ahí que ese hilo está bastante activo.
Saludos.

---

### Post by sebtev on 2008-10-08
Si la hora esta perfecta en Ubuntu y se modifica en Vista, el problema es Vista, desconozco bastante este sistema operativo, pero hay una opción de sincronizar la hora con internet o el servidor de internet...
Haz lo sig., configura la hora bien en Vista, destilda la casilla de sincronizar la hora con internet (si es q sigue existiendo o algo similar), vuelve a Ubuntu y reinicia a Vista para ver q onda.
Un abrazo, te me cuidas!

---

### Post by niko_3100 on 2008-10-08
Esta ves no hay que hecharle la culpa a vista... es un problema del TZData o algo asi es el daemon... actualiza tu SO.

---

### Post by Hei Ku on 2008-10-08
El tema es que Ubuntu sincroniza la hora a GMT y luego te muestra la hora segun tu huso horario. Windows sincroniza y muestra la hora local.
Tenes que configurar Ubuntu para que sincronice la hora local. Habia una pregunta de esas en la instalacion.

---

### Post by crosssover on 2008-10-09
te dejo este link donde explican como arreglarlo

[http://ubunlog.blogspot.com/2008/10/arreglar-error-time-zone-argentina.html]("http://ubunlog.blogspot.com/2008/10/arreglar-error-time-zone-argentina.html")

segun dicen ahi en unos dias sale el update oficial del Tzdata, espero te sirva

---

### Post by pol666 on 2008-10-09
Desde hace mucho ya ni lo doi bola al reloj en todos los so estan mal, ponele me dicen que son las 11:30 de la mañana, y en el otro las 5 de la tarde. Lo malo es que en realidad son las 6 ^^^

---

### Post by WanderingKnight on 2008-10-09
> Desde hace mucho ya ni lo doi bola al reloj en todos los so estan mal

En ningún sistema mío tuve problemas con la hora... de hecho la encuentro una de las cosas más útiles de todo el escritorio :p

---

### Post by majatu on 2008-10-10
opino igual que lo que te han dicho mas arriba pero aporto algo. Puede ser que tengas agotada la pila del clock de la motherboard o que te ande mas o menos porque se esta agotando, te digo porque la mayoria de las veces falla todo el sistema o no anda directamente, otras veces hace lo que te pasa a vos, fijate, usa Ubuntu o Windows un rato, apaga o reinicia la pc y volve a entrar al mismo sistema que venias usando, no al otro, y mira la hora.

o sino las zonas horarias las tenes cambiadas.

para todo lo que te dije, fijate en el menu de la BIOS el reloj y chequea la hora, si esta mal, correjila. apaga la pc, espera unos segundos y entra de nuevo a la bios y fijate si sigue en hora.

Saludos y espero a lo mejor te ayude ;)

---

