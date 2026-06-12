---
title: "Problemas con conexion ADSL en Ubuntu Jaunty"
date: 2009-05-17
forum: Software
---

### Post by atari130xe on 2009-05-17
Hola gente, ayer instalé Ubuntu 9.04 en la PC de un amigo, y todo fué de maravillas hasta que llegué a la parte de conexion ADSL "Miniaplicacion NetWorkManager" hice la configuracion en la pestaña DSL coloqué los datos de usuario y contraseña y tildé iniciar automaticamente, todo bien hasta que reinicié y nada, no conecta y la interface eth0 (conexión cableada) aparece como deshabilitada, clickeo en "Speedy" (es el nombre de la conexion) y queda intentando hasta que sale que no esta conectado, ahora si reinicio una vez mas se conecta, pero si apago la pc sin desconectar primero al encender la PC nuevamente no hay caso no conecta :(, hay alguna manera de "solucionar" ese inconveniente? hasta intrepid con sudo pppoeconf y siguiendo los pasos jamas hubo un problema se apagaba la pc y al reiniciarla se conectaba automaticamente sin ningun problema, pero con Jaunty es un drama, si saben de algo, avisen... gracias!

---

### Post by emiliano_raso on 2009-05-17
> **atari130xe said:**
> Hola gente, ayer instalé Ubuntu 9.04 en la PC de un amigo, y todo fué de maravillas hasta que llegué a la parte de conexion ADSL "Miniaplicacion NetWorkManager" hice la configuracion en la pestaña DSL coloqué los datos de usuario y contraseña y tildé iniciar automaticamente, todo bien hasta que reinicié y nada, no conecta y la interface eth0 (conexión cableada) aparece como deshabilitada, clickeo en "Speedy" (es el nombre de la conexion) y queda intentando hasta que sale que no esta conectado, ahora si reinicio una vez mas se conecta, pero si apago la pc sin desconectar primero al encender la PC nuevamente no hay caso no conecta :(, hay alguna manera de "solucionar" ese inconveniente? hasta intrepid con sudo pppoeconf y siguiendo los pasos jamas hubo un problema se apagaba la pc y al reiniciarla se conectaba automaticamente sin ningun problema, pero con Jaunty es un drama, si saben de algo, avisen... gracias!

Lo mismo pasa en Window$ (al menos aun amigo le pasa eso). Si no desconectas antes de reiniciar o apagar la maquina, despues no conecta.
Y en Jaunty, cuando despues de reiniciar sin haber desconectado pones pppeconf, que pasa?

---

### Post by atari130xe on 2009-05-17
lo intenté con pppoeconf pero termino peor, un desastre me borró "eth0" del miniapplicacion networkmanager applet y no conecto mas, tuve que reinstalar el sis de nuevo :o

---

### Post by josecuervo86 on 2009-05-17
A mi me pasa algo parecido (o tal vez lo mismo :S) Cuando reinicio, y no apago y prendo el modem, no vuelve a conectar. Pero mas alla de eso, la conexion anda 10 puntos.

---

### Post by atari130xe on 2009-05-17
Bueno por lo que estoy viendo en diferentes foros Ubuntu-es, etc no somos los únicos por lo que deduzco que es un bug del sistema, no queda otra...

---

### Post by oktubrer on 2009-05-18
Yo configuré la conexión con pppoeconf, no la desconecto al apagar el sistema e igualmente se conecta al iniciar.
Eso sí, en el applet del networkmanager no tengo nada, ni la conexión dsl ni la ethernet, pero realmente no lo considero necesario.

---

### Post by atari130xe on 2009-05-21
Se puede hacer eso? lo intente y no logre que funcione...

---

### Post by laucha_b on 2009-06-24
Hola, yo tengo el mismo problema y estoy probando: -tener encendido el modem al encender la PC -una vez iniciada la sesión apagar el modem -dejarlo unos minutos (2) apagado -luego volver a prenderlo.  Prueben y después me cuentan, saludos.

---

### Post by emilianx on 2009-07-25
Alguien soluciono este problema o directamente es un bug que no tiene arreglo?

---

