---
title: "Ayuda con servidor de Correos"
date: 2013-06-28
forum: Software
---

### Post by agxmohamed on 2013-06-28
Que tal comunidad, mi nombre es lucas, soy relativamente nuevo en el tema de linux pero me gusta mandarme de cabeza.

Tema:

Acabo de montar un web Server + mail server. Anda todo perfecto no viene por ahi mi consulta.

Consulta:

El mail server funciona perfectamente no tengo ningun drama, peeeeeero, me tope con una traba muuuuuuuuuuuy grande, y es que mi ISP (fibertel) bloquea el puerto 25 (no para el envio) sino para la recepcion. Llame me comunique con fibertel y me dijeron que "podrian" llegar a darme una solucion con las soluciones corporativas que tienen y que igualmente no era seguro que pudieran darme una solucion a lo que yo necesita.

Problema:

¿Cual es el problema?

Para realizar el envio, ninguno, saco al postfix por cualquier otro puerto.
¿Problema?, cualquier otro web server va a intentar conectarse al mio por el puerto 25 y el mismo no responde. Estoy buscando informacion por todos lados si es que existe alguna forma de desviar las peticiones que vienen externas al puerto 25, pero aun no pude encontrar exactamente lo que quiero, encuentro el tipico error de que si no puedo enviar, salir por otro puerto, pero mi problema basicamente es ese. 

Si a alguno le paso este inconveniente y tiene alguna solucion me podria orientar para donde es que lo tengo que hacer? porque hace aproximadamente ya unos 6 meses que vengo intentando encontrar una solucion y no la puedo encontrar. Si alguno sabe algo, o sabe de algun tema que se haya tratado por favor le pido si me puede asesorar un poco.


Desde ya muchas gracias :D

---

### Post by guillermolisi on 2013-07-06
El tema es mas complejo aun ya que por el solo hecho de operar el servidor de e-mail a traves de un bloque de IPs publicado como dinamico los demas servidores (que esten bien configurados) rechazaran lo que envies. Esto ocurre aun cuando tu ISP no te cambie la IP a traves del tiempo (como suele hacer Fibercoorp con algunas empresas cuando venden la solucion "IP fija", solo configuran en su DHCP la IP asignada a la MAC de la placa de red que recibe la conexion publica usando una IP de un bloque conocido como dinamico e informado por los ISPs para generar una base de datos al cual acceden los servidores de e-mail y DNS).

En mi caso opte por utilizar GoogleApps, pero ya no es una opcion valida porque no hay mas cuentas gratuitas.

Por otra parte son muy pocos y cada vez menos los servidores de e-mail que usan el port 25 para Internet ya que muchos han optado por usar SSL/TLS al estilo Google para, entre otras cosas, combatir el spam.

Adicionalmente, hay que generar los registros SPF y DKIM y crearlos en el DNS que uses para que (de nuevo) los servidores bien configurados no reboten tus mensajes por mala verificacion del origen.

---

