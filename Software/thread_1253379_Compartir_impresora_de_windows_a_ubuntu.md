---
title: "Compartir impresora de windows a ubuntu"
date: 2009-08-30
forum: Software
---

### Post by VonlisT on 2009-08-30
Saludos a todos los foreros.
MI problema es el siguiente:
Tengo una impresora HP 910 con soporte limitado para linux (La velocidad es horrenda comparada con el driver de windows) y no vale la pena volver a windows por esto.
Se me ocurrió la idea de instalar windows xp en una maquina virtual y compartirla por LAN virtual para poder imprimir desde Ubuntu y que Windows le envíe los datos a la impresora.
Hasta ahi todo bien, logré configurar tanto en windows como en ubuntu (9.04), pero al momento de imprimir desde linux, la impresora hace el tipico ruido de que va a salir la hoja, pero no sale nada, la cola de impresiones en windows se hace eterna y aunque la elimine sigue ahi.

Quisiera saber si hay otras formas de hacer exactamente lo mismo que hice yo, necesito ideas o sugerencias para poder imprimir (soy estudiante e imprimo muchisimo).
Saludos a todos ! :)

---

### Post by Carlos C on 2009-08-30
Hola. Sería bueno que nos dijeras el modelo exacto de tu impresora.
Saludos!

---

### Post by Carlos C on 2009-08-30
Hola. Pude ver que ya habías consultado por tu impresora en launchpad:

[https://answers.launchpad.net/hplip/+question/73790](https://answers.launchpad.net/hplip/+question/73790)

Lamentablemente el estado actual de ese driver parece responder exactamente a lo que tú describes:

[http://hplipopensource.com/hplip-web/models/other/hp_910.html](http://hplipopensource.com/hplip-web/models/other/hp_910.html)

Voy a buscar más información y si encuentro algo aviso.
Saludos.

---

### Post by VonlisT on 2009-08-31
> **Carlos C said:**
> Hola. Pude ver que ya habías consultado por tu impresora en launchpad:

[https://answers.launchpad.net/hplip/+question/73790](https://answers.launchpad.net/hplip/+question/73790)

Lamentablemente el estado actual de ese driver parece responder exactamente a lo que tú describes:

[http://hplipopensource.com/hplip-web/models/other/hp_910.html](http://hplipopensource.com/hplip-web/models/other/hp_910.html)

Voy a buscar más información y si encuentro algo aviso.
Saludos.

Así es, muchas gracias por responder.
Me di una solución algo engorrosa pero aceptable.
HIce lo siguiente:
Instalé Virtualbox (la versión privativa para tener soporte USB) e instalé windows xp, instalé lo necesario y el driver de la impresora, activé la red del virtualbox y cree una carpeta compartida (desde virtualbox), luego en windows la veo en Mi PC (le hice un acceso al escritorio). Entonces desde linux, mando lo que quiero imprimir a la carpeta compartida (Le puse la carpeta de mi usuario para tener mas acceso) e imprimo sin problemas.
Luego cierro la maquina virtual y sigo con mi vida :)

NOTA:
Intenté compartir la impresora desde windows para imprimir por red desde Ubuntu, pero no me funciona, la impresora hace los "chasquidos" como que va a salir la hoja pero nada, aveces el LED de la impresora se vuelve loco, mejor no sigo intentando, me quedo con lo que hice.
Saludos !

---

### Post by moreback on 2009-09-01
> **VonlisT said:**
> Intenté compartir la impresora desde windows para imprimir por red desde Ubuntu, pero no me funciona, la impresora hace los "chasquidos" como que va a salir la hoja pero nada, aveces el LED de la impresora se vuelve loco, mejor no sigo intentando, me quedo con lo que hice.

Eso me parece que es problema del driver de impresión usado en Ubuntu. Generalmente hay varios que sirven para la impresora, puedes probar con esos o con el que te indica como recomendado. Ojalá que encuentres el indicado.

Saludos.

---

