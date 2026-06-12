---
title: "mi hijo se come todo el ancho de banda con su windows PC"
date: 2014-09-21
forum: Software
---

### Post by fleetwood1970 on 2014-09-21
Hola a todos:

Mi problema es facil. Mi hijo es el unico que usa Windows en mi casa y juega en red todo el dia.
Mi marido usa Ubuntu Studio 14.04 y yo Ubuntu 14.04 LTS.
La gente de Telecentro nos dio un modem, yo me conecto por cable de red directamente 
y tanto mi marido como mi hijo tienen tarjetas de wifi.
El servicio que tenemos es de 10 Megas y necesito limitar la maquina de mi pibe (Windows 7).
Sino todos los fines de semana tenemos una guerra por el ancho de banda.
Algun programa que pueda hacer esto? Obviamente algo que mi hijo no pueda anular.
Algo que yo pueda instalar y remotamente limitar su maquina?
Tengo que hacerlo desde el modem mismo que me dio Telecentro? Como se hace?

Mucha Gracias Lorena

---

### Post by euzkoarima on 2014-10-13
La función de limitar el ancho de banda le corresponde al router, por eso primero hay que ver que modelo es el router que te dio telecentro, que capacidades tiene y si todas esas capacidades quedaron disponibles (a veces los ISP limitan el acceso a ciertas configuraciones del router).
Entiendo que lo mejor sería hacer un QoS por ip, para lo cuál habría que hacer que la máquina de tu hijo tenga ip fijo (se puede hacer que el dhcp del router entregue siempre un mismo nro de ip basado en el MAC address de la placa que se conecta, en este caso la tarjeta wifi de la pc con windows).
Paso un link donde muestra como se hace un router determinado, casi seguro NO es el que te entregó telecentro, pero lo paso como referencia para que veas "la facha" de una solución de este tipo

[http://www.tp-link.com/ar/article/?faqid=194](http://www.tp-link.com/ar/article/?faqid=194)

Saludos,
Eduardo

---

