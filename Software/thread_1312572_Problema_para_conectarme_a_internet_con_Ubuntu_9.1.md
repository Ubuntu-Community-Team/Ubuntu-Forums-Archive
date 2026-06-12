---
title: "Problema para conectarme a internet con Ubuntu 9.10"
date: 2009-11-03
forum: Software
---

### Post by Danikomdq on 2009-11-03
Ayer actualicé de Ubuntu 9.04 a 9.10. Fue todo perfecto y sin problemas.
Único detalle: "desapareció" la conexión a internet, la vuelvo a crear, pero simplemente no se conecta. Cuando intenta hacerlo se queda colgado. 
La conexión del modem a la placa de red funciona, al menos eso es lo que dice, pero es imposible entrar a internet. 
¿Alguna idea de lo que puede estar pasando?
Gracias

---

### Post by guillermolisi on 2009-11-03
> **Danikomdq said:**
> Ayer actualicé de Ubuntu 9.04 a 9.10. Fue todo perfecto y sin problemas.
Único detalle: "desapareció" la conexión a internet, la vuelvo a crear, pero simplemente no se conecta. Cuando intenta hacerlo se queda colgado. 
La conexión del modem a la placa de red funciona, al menos eso es lo que dice, pero es imposible entrar a internet. 
¿Alguna idea de lo que puede estar pasando?
Gracias
Proba poniendo una IP en lugar de una URL en el navegador web. Si te conecta con el site entonces el tema pasa por la falta o mala asignacion de los servidores DNS.

Cuando decis"desaparecio" la conexion a Internet, a que te referis precisamente, al icono del NManager ? al contenido del /etc/network/interfaces ?

---

### Post by Danikomdq on 2009-11-03
> **guillermolisi said:**
> Proba poniendo una IP en lugar de una URL en el navegador web. Si te conecta con el site entonces el tema pasa por la falta o mala asignacion de los servidores DNS.

Cuando decis"desaparecio" la conexion a Internet, a que te referis precisamente, al icono del NManager ? al contenido del /etc/network/interfaces ?

La conexión ADSL para ingresar al servicio de internet no estaba.

---

### Post by guillermolisi on 2009-11-03
> **Danikomdq said:**
> La conexión ADSL para ingresar al servicio de internet no estaba.
Hay reportes sobre el tema y por ahora quienes estan sufriendo ese problema lo estan resolvieron usando pppoe o reconfigurando el modem para que funcione como router y haga el discado el mismo equipo ([http://ubuntuforums.org/showthread.php?t=1308608](http://ubuntuforums.org/showthread.php?t=1308608))

---

### Post by Danikomdq on 2009-11-03
> **guillermolisi said:**
> Hay reportes sobre el tema y por ahora quienes estan sufriendo ese problema lo estan resolvieron usando pppoe o reconfigurando el modem para que funcione como router y haga el discado el mismo equipo ([http://ubuntuforums.org/showthread.php?t=1308608](http://ubuntuforums.org/showthread.php?t=1308608))

OK, gracias.
Hago la prueba y aviso como me fue
Otra vez gracias

---

### Post by Fak89 on 2009-11-03
Si si, yo tengo el mismo problema y lo estoy manejando con el pppoe..
Simplemente en una consola pone:
> pppoeconf

Segui los pasos y seguramente despues ya tenes internet.
Saludos!

---

### Post by mama21mama on 2009-11-03
Que proveedor tenes?. Diste pocos datos

yo con speedy siempre use

> sudo pppoeconf
le doy todo que si

usuario: user@speedy
clave:   password

---

### Post by Danikomdq on 2009-11-04
> **mama21mama said:**
> Que proveedor tenes?. Diste pocos datos

yo con speedy siempre use


le doy todo que si

usuario: user@speedy
clave:   password

Tengo el servicio de una cooperativa telefónica de Mar del Plata, Copetel. 
Intenté a través de consola a través de sudo pppoeconf, y no funcionó. 
Por un momento pensé que sería un problema con el modem, pero reconoce que está conectado a la placa de red y sobre la misma línea el teléfono funciona perfectamente.

---

### Post by Danikomdq on 2009-11-10
Problema solucionado hace unos días, como dijeron varios: 
[INDENT]**sudo pppoeconf** [/INDENT]
y después decir siempre *SI*
La conexión se realiza de forma automática al arrancar la máquina.

Gracias a todos por la ayuda

---

### Post by Tosh78 on 2009-11-10
Me alegro de que hayas resuelto el problema. Te aconsejo que marques el thread como Solved, asi ya sabemos que este problema fue resuelto.

---

