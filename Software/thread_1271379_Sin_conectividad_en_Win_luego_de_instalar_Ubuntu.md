---
title: "Sin conectividad en Win luego de instalar Ubuntu"
date: 2009-09-20
forum: Software
---

### Post by fabaya on 2009-09-20
Hola, les consulto por algo bastante extraño que me ha sucedido luego de instalar ubuntu desde Win XP con Wubi. El problema es que, aunque ha quedado todo bien instalado, y los dos S.O. coexisten pacificamente, el tema es que cada vez que entro a Windows luego de haber utilizado Ubuntu, el cable de red me aparece como desconectado y la luz de la placa apagada. Para hacer que la placa de red arranque nuevamente, tengo que apagar la pc, sacar los cables de router y de la fuente de la PC, y solo asi, cuando entro a Win, la conectividad se reestablece y la placa de red comienza a funcionar. ¿Cómo puedo evitar esto? ¿En el CD de Ubuntu decia que lo instalaba sin modificar nada? Evidentemente, cuando cierra Ubuntu o cuando bootea la máquina algo se modifica. 

He notado que otras personas tienen el mismo problema en XP luego de instalar ubuntu; pero ninguna ha encontrado una solucion satisfactoria al problema. 

Ejemplos:

[http://www.ubuntu-es.org/?q=node/116703](http://www.ubuntu-es.org/?q=node/116703)
[http://www.mail-archive.com/ubuntu-accessibility@lists.ubuntu.com/msg03507.html](http://www.mail-archive.com/ubuntu-accessibility@lists.ubuntu.com/msg03507.html)
[http://www.linuxquestions.org/questions/linux-networking-3/network-cable-unplugged-on-windows-caused-by-linux-redhat-9.0-151754/](http://www.linuxquestions.org/questions/linux-networking-3/network-cable-unplugged-on-windows-caused-by-linux-redhat-9.0-151754/)



La verdad es que me da pena desinstalar Ubuntu, porque queria empezar a familiarizarme con el, pero si cada vez que lo uso voy a tener que desconectar los cables para poder usar XP, me parece que voy a esperar a que Ubuntu no toquetee tanto el hardware. 


Desde ya muchas gracias.

---

### Post by Hei Ku on 2009-09-20
Probaste de actualizar los drivers de tu placa de red?

---

### Post by fabaya on 2009-09-20
En eso estaba, porque al final de uno de los threads solucionaron el problema para las marvell yukon; el updater de win, no me trae, sin embargo, nuevas actualizaciones para la placa. Es la ATHEROS L2 FAST ETHERNET. Seguire buscando y les cuento.

Excelente, al final, actualizando el driver directamente desde la pagina de ATHEROS, todo funciona como corresponde. Desde ya muchas gracias.

---

