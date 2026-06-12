---
title: "Jugando con al red: Que programas hay para....?"
date: 2009-09-09
forum: Software
---

### Post by pol666 on 2009-09-09
Estaba queriendo experimentar que podia hacer con las dos pc de mi casa, ambas tienen linux y comparten archivos por nfs. 
Estaba buscando algunos programas que sirvan para..


[LIST=1]
[*]Monitorear la pantalla de una computadora, de modo de poder observar en vivo lo que esta sucediendo. Similar a las herramientas que tienen algunos cyber, aunque supongo que en una red inalambrica va a funcionar lento.
[*]Usar remotamente alguno de los equipos, supongo que necesito algun programa vnc, tengo en mente vino o vinagre que creo que venian en ubuntu, no esetoy seguro si sirve para esto.
[*]Enviar mensajes en forma de notificaciones. En windows existia un programa que se llamaba Winpopup, hay algo similar para linux?
[/LIST]

---

### Post by pablo.s on 2009-09-09
> **pol666 said:**
> Estaba buscando algunos programas que sirvan para..

Monitorear la pantalla de una computadora, de modo de poder observar en vivo lo que esta sucediendo. Similar a las herramientas que tienen algunos cyber, aunque supongo que en una red inalambrica va a funcionar lento.

Podés utilizar xvnc4viewer para
esto.

> **pol666 said:**
> Usar remotamente alguno de los equipos, supongo que necesito algun programa vnc, tengo en mente vino o vinagre que creo que venian en ubuntu, no esetoy seguro si sirve para esto.

O podés utilizar el mejor invento
de la humanidad: ssh

> **pol666 said:**
> Enviar mensajes en forma de notificaciones. En windows existia un programa que se llamaba Winpopup, hay algo similar para linux?

Linpopup, pero precisás SAMBA.

---

### Post by pol666 on 2009-09-10
mmm que macana, nfs me funciona bastante bien para cambiarlo por Samba. Gracias por el dato de los programas, aunque acceder por shh es solo por consola, o estoy errado?

---

### Post by pablo.s on 2009-09-10
> **pol666 said:**
>  acceder por shh es solo por consola, o estoy errado?

Se puede trabajar con Tunneling por X,
que te trae el servidor X de la máquina 
remota a la tuya.
Lo del Linpopup lo podés suplantar por
cualquier cliente de mensajeria instantanea.

---

