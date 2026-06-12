---
title: "Cómo puedo eliminar &quot;la versión GNU GRUB 1.98-1ubuntu5&quot; durante el arranque?"
date: 2012-07-19
forum: Software
---

### Post by diegol3d on 2012-07-19
Hola. Necesito de su ayuda. Resulta que reinstale windows (lo tenia con  doble buteo: Windows 7 y Ubuntu 10.04). Lei un tutorial para recuperar  la grub. Me costo, creo que en algun momento me complique con las  particiones, quizas monte alguna que no tenia que montar, aclaro esto  porque quizas ahi esta el error. El tema es que ahora al botear la  maquina me sale esa pantalla negra que dice: "la versión GNU GRUB  1.98-1ubuntu5" durante el arranque. Si pongo exit y enter, se va y me da  la opcion de elegir que sistema operativo quiero (tal como estaba  antes)
Ahora pregunto: Como hago para eliminar esa pantalla negra???. por favor necesito ayuda.
Saludos.

---

### Post by YannBuntu on 2012-07-19
Hola
Por favor indique su URL [BootInfo]("https://help.ubuntu.com/community/Boot-Info").

---

### Post by diegol3d on 2012-07-19
> **YannBuntu said:**
> Hola
Por favor indique su URL [BootInfo]("https://help.ubuntu.com/community/Boot-Info").

Hola. Gracias por responder.
Si no entendi mal lo que tu me pides es esto:

[U]
[http://img543.imageshack.us/img543/2695/pantallazoer.png](http://img543.imageshack.us/img543/2695/pantallazoer.png)

[/U]Si no se lee dice: Tenga en cuenta el siguiente URL: [http://paste.ubuntu.com/1099785/](http://paste.ubuntu.com/1099785/)

2 cosas:
1) Me funciona internet lentisima en ubuntu, no asi en windows.
2) cambie el motherboard por eso formatie windows, no asi ubuntu. eso puede influir?
Saludos.

---

### Post by YannBuntu on 2012-07-19
> **diegol3d said:**
> [http://paste.ubuntu.com/1099785/](http://paste.ubuntu.com/1099785/)

No veo nada extraño con el boot/GRUB.

> **diegol3d said:**
> 
2 cosas:
1) Me funciona internet lentisima en ubuntu, no asi en windows.
2) cambie el motherboard por eso formatie windows, no asi ubuntu. eso puede influir?
Saludos.

Después de cambiar el motherboard (o calquier hardware importante, por ejemplo la carta graphica), es mejor reinstalar Ubuntu. 
E en su caso, aprovechar para hacer el upgrade a 12.04.

Consejo gravar un CD 12.04 y seguir este tutorial: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
Eso va actualizar el GRUB asi que:
- talvez se va a resolver tambien el problema de pantalla negra.
- talvez se necesitara crear un /boot separado. (si GRUB ya no aparece más)

---

### Post by diegol3d on 2012-07-19
Muchas gracias por tomarse la molestia de responderme. Voy a hacerle caso y voy a reinstalar Ubuntu 12.04, pero desde 0. Perdere todo, pero es mejor empezar de nuevo con hardware nuevo como bien dice ud. 
Gracias!!!
Saludos.

---

