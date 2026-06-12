---
title: "Problema de ubuntu en una red windows"
date: 2009-08-11
forum: Software
---

### Post by jcoronelc on 2009-08-11
Cuento largo.

Existen dos redes.


[LIST]
[*]la principal 192.168.1.0
[/LIST]


[LIST]
[*]en el punto 192.168.1.11 se ha instalado un router d-link dir-300 para dar acceso wireless. Dicho router su interfaz wan se le asigno la ip estatica 192.168.2.1 con gateway 192.168.1.1
[/LIST]


[LIST]
[*]desde 192.168.1.0 a 192.168.2.0 se puede realizar ping a todo equipo conocido y viceversa
[/LIST]


[LIST]
[*]**todo equipo windows en la red 192.168.1.0 puede acceder a cualquier equipo en 192.168.2.0 examinando con \\nombre_equipo o \\ip_equipo y viceversa.**
[/LIST]


[LIST]
[*]**desde la red 192.168.1.0 cuando se quiere examinar al equipo ubuntu en 192.168.2.0, el quipo no aparece, mensaje de error que no se encuentra, aunque al realizar ping al equipo entregue resultado positivo...**
[/LIST]


[LIST]
[*]cuando el equipo con ubuntu está en 192.168.2.0 puede resolver netbios de cualquier equipo  en su propia red y en la red 192.168.1.0 usando \\nombre_equipo o \\ip_equipo
[/LIST]


[LIST]
[*]cuando el equipo ubuntu esta en la red 192.168.1.0, cualquier equipo de esta red y de la red 192.168.2.0 puede examinarlo sin problemas usando \\nombre_equipo o \\ip_equipo
[/LIST]

entonces...
¿que puede estar pasando cuando ubuntu está en 192.168.2.0 que nadie de 192.168.1.0 puede examinarlo? no asi cuando ubuntu está en 192.168.1.0 en que todos pueden verlo incluidos los de 192.168.2.0?

alguna idea?

espero haber sido lo suficientemente claro.

agradecido desde ya por vuestras atentas respuestas

---

### Post by kamus on 2009-08-11
Tienes configurada la misma puerta de enlace?, lo otro es que tu puerta de enlace debe soportar el bridge para que puedas llegar de un segmento de red hacia el otro.

---

### Post by jcoronelc on 2009-08-11
> **kamus said:**
> ... lo otro es que tu puerta de enlace debe soportar el bridge para que puedas llegar de un segmento de red hacia el otro.


Me pillaste con eso...
a que te refieres???

tener en cuenta que poco se de redes...

el eq con ubuntu tiene instalada para administrar conexiones de red el "Wicd"

la asignacion de Ip en la red 192.168.2.0 se realiza con DHCP automatico generado por el router dlink.

los datos entregados deberían ser

ip 192.168.2.100
mascara 255.255.255.0
puerta enlace 192.168.2.1

el servidor wins se lo indico por smb.conf

algun otro comentario???

---

### Post by moreback on 2009-08-13
¿Quién rutea entre las redes 192.168.1.0 y 192.168.2.0? Por lo visto quieres que sea el mismo dlink (por la máscara que usas de 255.255.255.0) pero que yo sepa éstos no tienen como rutear redes conectadas a su LAN.

---

### Post by jcoronelc on 2009-08-14
> **moreback said:**
> ¿Quién rutea entre las redes 192.168.1.0 y 192.168.2.0? Por lo visto quieres que sea el mismo dlink (por la máscara que usas de 255.255.255.0) pero que yo sepa éstos no tienen como rutear redes conectadas a su LAN.


le digo que : por physical port  destino :192.168.1.0 submask: 255.255.255.0 gategaway: 192.168.1.11

lo mismo para 192.168.0.0


pero indico... ningun ep con windows tiene problema, solo el de ubuntu.

---

