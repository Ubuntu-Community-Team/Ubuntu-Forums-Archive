---
title: "Actualice a 10.10 y ahora no conecta a internet"
date: 2010-11-10
forum: Software
---

### Post by alavorano on 2010-11-10
Hola, el tema es el siguiente: hace 2 dias actualice de ubuntu 10.04 a 10.10. Todo funcionaba perfecto (excepto un poco el tema de video y sonido, q lo tengo posteado en otro threat), hasta que hoy dejo de funcionar internet. Es decir, esta conectado el router y todo, pero como que no lo reconoce. De hecho, esta conectado quiero decir q tambien se ve que esta conectado el cable de ethernet y todo, pero aun asi no lo toma. 
Es más, si en el icono de conexiones de red (el de arriba  a la izquierda de todo, onda wifi parece) desactivo la red y luego la reactivo (que solia funcionar), no sólo no funciona... sino que ademas como q me desconecta el cable de red (es decir, desaparece el led del router) y por supuesto que volvemos a la misma donde no reconoce internet.
Que hago??

Saludos
Aldu

---

### Post by Wiredfixer on 2010-11-11
que te aparece con el comando "ifconfig"?

Puede que tus interfaces esten apagadas, no siempre se activan correctamente con los controles de Gnome. si ya tienes identificadas tus interfaces, prueba haciendo "sudo ifconfig ethX up" donde ethX es tu interface (eth0,eth1,wlan, etc..,)

---

