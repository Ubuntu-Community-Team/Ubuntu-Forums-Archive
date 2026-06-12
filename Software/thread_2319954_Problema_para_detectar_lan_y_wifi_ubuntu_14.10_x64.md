---
title: "Problema para detectar lan y wifi ubuntu 14.10 x64"
date: 2016-04-08
forum: Software
---

### Post by nikoniko on 2016-04-08
[COLOR=#333333][FONT=Ubuntu]Hola gente.[/FONT]

[FONT=Ubuntu]LA VERSIÓN ES 16.10, ME EQUIVOQUE EN EL TITULO.[/FONT]
[/COLOR]
[COLOR=#333333][FONT=Ubuntu]Quería contarles que tengo en mi pc instalado el Ubuntu 16.10 i386, el cual no me remitió ningún problema tanto en la instalación como el uso, pero al hacer multitasking se traba un poco y por eso quise instalar la versión X64 para poder sacarle todo el máximo a mi pc, Pero cuando pongo el LiveCD no me detecta la conexión Lan ni Wifi, y si intento instalarlo luego tampoco la detecta, cosa que con la versión i386 no tuve ningún problema, trate de configurarla manualmente y no resulto, varias veces tuve que configurar manualmente las redes y nunca tuve problemas, espero que alguien pueda darme una mano por que estoy desaprovechando las prestaciones de mi PC al usarla en 32bits, dejo los detalles de mi PC abajo, y ante todo muchas gracias.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Mi PC tiene un Mother Gigabyte 990FXA-UD3 R5, 8gb de ram, microprocesador AMD FX-8320E de 8 núcleos y placa de vídeo NVidia GeForce GTX 750Ti 2Gb DDR5, esta conectada mediante cable LAN a Cable módem, pero también tiene una placa de red Wifi Pci Tp-link Tl-wn951n.[/FONT][/COLOR]

---

### Post by gmunioz on 2016-04-09
En principio la tarjeta wireless card TP-Link TL-WN951N que existe en dos versiones (V1 y V3) tiene como chip uno basado en Atheros AR5008-3NG y completamente soportado por el kernel linux desde Ubuntu 10.10. Es posible que por estar utilizando una versión en desarrollo tenga problemas aun no resueltos. Y en cuanto a las diferencias entre usar 32 ó 64 bits, particularmente no me resultan importantes, salvo que las aplicaciones de 64 bits requieren un poco más de memoria para funcionar. Sugerencia, si te funciona bien la versión de 32 bits, continua con ella.

---

