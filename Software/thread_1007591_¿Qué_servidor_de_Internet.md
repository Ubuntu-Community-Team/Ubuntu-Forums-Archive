---
title: "¿Qué servidor de Internet?"
date: 2008-12-10
forum: Software
---

### Post by athnea on 2008-12-10
Hola a todos...
hace mucho tiempo di vueltas por este foro, intentando configurar una VPN (de sion) en Ubuntu. Al final no se pudo conectar nunca y tuve que dejar utilizar Ubuntu (por mi trabajo necesito una conexión a internet sí o sí).
Pero la verdad, me encariñé con Ubuntu y quisiera instalarlo de nuevo, pero para eso tengo que cambiar de servidor de Internet. ¿Qué me recomendarían, qué servidores funcionan sin mucho problema?
Cualquier dato me vendrá más que bien para "convertirme" a Ubuntu.

Gracias!!
Inna

---

### Post by z37a on 2008-12-10
> **athnea said:**
> Hola a todos...
hace mucho tiempo di vueltas por este foro, intentando configurar una VPN (de sion) en Ubuntu. Al final no se pudo conectar nunca y tuve que dejar utilizar Ubuntu (por mi trabajo necesito una conexión a internet sí o sí).
Pero la verdad, me encariñé con Ubuntu y quisiera instalarlo de nuevo, pero para eso tengo que cambiar de servidor de Internet. ¿Qué me recomendarían, qué servidores funcionan sin mucho problema?
Cualquier dato me vendrá más que bien para "convertirme" a Ubuntu.

Gracias!!
Inna


En realidad no importa mucho el ISP si no el servidor del otro lado, si es que esta usando OpenVPN u otra tecnologia.

En tu trabajo como armaron la VPN?

---

### Post by hictio on 2008-12-10
Estoy de acuerdo con z37a, me suena raro que el ISP este bloqueando... 

Para aclarar un poco:

- Vos queres conectarte, usando un cliente VPN desde tu maquina Ubuntu, a que dispositivo?
- Es un concentrador VPN de la oficina?
- Quien lo administra? Podes hablar con la persona a cargo?
- En lo personal vi varias veces problemas para conectarse a concentradores VPN Cisco, siempre tuve que usar el Cliente Cisco, y ademas, ver que la configuracion del concentrador permita clientes que no son Windows (esto, digo convencer a la persona a cargo que de ser posible lo modifique, es lo mas dificil de todo)/

---

### Post by athnea on 2008-12-11
Hola, hictio y z37a,
el asunto es así: yo soy usuaria doméstica y me conecto a una VPN, así es el servicio de internet que da la empresa de internet que contraté. Fue imposible conectar, a pesar de tener mucha ayuda ([http://ubuntuforums.org/showthread.php?t=808768&highlight=sion+internet](http://ubuntuforums.org/showthread.php?t=808768&highlight=sion+internet)). Así que tuve que sacar ubuntu. Ya no creo que haya forma de conectar con Sion, las pocas personas que pudieron conectarse con ubuntu me dijeron que la conexión era muy inestable.

Lo que quisiera ahora es saber que compañía de internet me puede servir de una, no sea que me pase a Telecentro y tampoco sea posible usarlo en Ubuntu.

Saludos!

---

### Post by Hei Ku on 2008-12-11
En general, las que son cablemodem andan bien. Sismo, vos tenes Telecentro, no?
Yo tengo Fibertel y anda bien. Y antes tenía Multicanal y no tuve dramas con el Ubuntu.
Obviamente, el servicio varia con cada una, pero el Ubuntu no es un tema.

---

### Post by sajnox on 2008-12-11
Hace dos meses, mas o menos, que tengo Arnet. La verdad que hasta ahora no tuve ni un problema siempre que lo prendo anda, y tengo la velocidad contratada a la hora que lo pruebe.

En mi caso me encargue de que manden un modem con placa ethernet, con eso tenes el problema solucionado. Aunque la verdad que por lo que veo el soporte para los modems usb anda cada vez mejor (eso se nota por la cantidad de posts que hay en el foro con ese tema, hace un año habia todos los dias alguien con ese problema)

---

### Post by guillermolisi on 2008-12-11
Coincido que Fibertel o Telecentro son las opciones (menos malas) para un uso domestico.

Tengo FIber desde un poco antes del 2000 y desde principios del 2007 con Ubuntu, siempre via Ethernet, y nunca tuve problemas en ese sentido.

---

### Post by hictio on 2008-12-11
Yo tengo Fibertel en casa, que la verdad sea dicha, tiene muy pocos downtimes, por lo menos en mi zona.
Y ahora estoy conectado a Multicanal -no estoy en mi casa- que es bastante maleta el servicio.
(De paso, Multicanal & Fibertel, no son la misma cosa ya?)

Pero volviendo al tema de tu post. No me queda en claro tu respuesta la verdad...

1- Vos queres montar tu servidor VPN en tu casa, o donde sea, a traves de tu ISP?
2- Vos queres conectarte a un servidor VPN desde tu casa?
(La opcion 2 en lo personal no tuve problemas desde ninguno de los dos ISPs)

El problema estaba, como te decia en otro post anterior a este, que el concentrador VPN al que me conectaba estaba configurado, 1ero, para aceptar conexiones de clientes VPN de Cisco solamente; y 2do, clientes clientes Windows... 

Para el 1ro no habia problema, en Ubuntu 7.04 el cliente de VPN Cisco que tenia que usar compilaba e instalaba perfecto.
Para el 2do no pude hacer nada.

---

### Post by NickCis on 2008-12-11
Mira, yo que empece con Ubuntu hace unas semanas, tengo Multicanal (creo que Trabaja por Flash), con un Modem que tiene Ethernet y Usb. Por Usb fue imposible conectarlo, los drivers no existen y en la misma pagina de Flash, te dice que no existen para linux, pero por Ethernet, anda todo barbaro, ni configuracion nececito andubo todo de una sin problemas. Ademas, noto, que la velocidad de descargar es superior a la que tenia antes con un Win Xp.

Saludos.

---

### Post by faktorqm on 2008-12-12
Caso general: Cualquier cosa que te deje una boca ethernet con dhcp te va a funcionar en ubuntu automaticamente.

caso particular: Tengo speedy, y a pesar de las quejas de muchos, a mi siempre me anduvo de diez, nunca un drama. Incluso me he llegado a quedar sin telefono pero la conexion seguia andando :D Salu2!!

---

### Post by z37a on 2008-12-12
> **faktorqm said:**
> Caso general: Cualquier cosa que te deje una boca ethernet con dhcp te va a funcionar en ubuntu automaticamente.

caso particular: Tengo speedy, y a pesar de las quejas de muchos, a mi siempre me anduvo de diez, nunca un drama. Incluso me he llegado a quedar sin telefono pero la conexion seguia andando :D Salu2!!

Eso de cual anda mejor depende mucho de la zona, si vivís al lado de la centralita obviamente que te tenes que poner ADSL, te va a andar de 10 la conexión de 20MB!!!!! Ahora si te pasa como a mi que estoy en el centro de un triangulo donde cada centralita esta a 5km solo tengo cablemodem que me funcione bien, el ADSL no me funciona ni a 1MB, ahora si la empresa de cablemodem sobrevende la conexión en mi zona, y bueno estoy al horno!!!!

Mas allá de la empresa lo que hace falta es que te entreguen un modem ethernet!!! Arnet en una epoca te daba los pirelli que los podías utilizar de routers también. Igualmente por lo que leo tu problema no es la VPN en si, si no la conexión a internet!!!!

---

