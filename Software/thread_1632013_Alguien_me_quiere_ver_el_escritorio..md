---
title: "Alguien me quiere ver el escritorio."
date: 2010-11-27
forum: Software
---

### Post by Fitmoos on 2010-11-27
La cosa es que un estupido, me ha estado solicitando decenas de  veces poder ver mi escritorio
un pc-92-88-44-190.cm.vtr.net

aqui un pantallazo
[IMG]http://i53.tinypic.com/10zpx10.png[/IMG]

¿Como puedo blouquear su ip?

¿por que me webea?

---

### Post by Patriciologico on 2010-11-27
Por que te molesta no tengo idea, me da la impresión que es alguien que te conoce ¿alguien ha manejado tu pc, te ha ayudado, etc?

¿tienes abiertas las conexiones de escritorio remoto?

Bloquear ip no creo sirva de mucho pues vtr, segun entiendo, usa ip's dinamicas.


Nota: Este post es ta mal ubicado, usa la sección que corresponda, en este caso a "Software"

---

### Post by moreback on 2010-11-28
Puede ser que tenga el servicio de VNC funcionando, lo malo es que no me acuerdo donde puede ver uno los servicios que se inician con la máquina.

Por consola está el comando service.

Saludos.

---

### Post by hisam on 2010-12-05
Eso es el servicio de Escritorio Remoto de GNOME me parece, bueno  sea cual sea si no lo ocupas puedes desactivarlo del inicio automático.

---

### Post by Darkade on 2010-12-16
Tienes varias opciones.

1) Desactiva el servicio de VNC. (En este momento no estoy frente a ubuntu pero debe estar en System>Administration>Remote Desktop). Esto va a deshabilitar Vino, que es el VNC server por default de gnome.

2) Si tu usas VNC de cualquier forma te recomiendo desactivar Vino y usar x11vnc (o vino, x11vnc es solo preferencia personal) pero restringir las solicitudes de VNC al localhost, luego hacer un tunel con SSH.

Esta solución te va a funcionar bien en tu red local, pero para acesar tu computadora desde el internet vas a tener que hacer un portfowarding de tu router. Asi es como lo tengo configurado yo y funciona muy bien. Puedes leer más sobre vnc + ssh [aqui]("https://help.ubuntu.com/community/VNC")

Si no usas VNC, ni quieres acesar tu computadora de forma remota quedate con la primera opción :)

Espero que te sea de ayuda

---

