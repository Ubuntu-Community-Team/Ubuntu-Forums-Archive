---
title: "Ubuntu Server 9.10 + Webmin 1.530 - Problemas de desconexion intermitentes."
date: 2011-02-09
forum: Software
---

### Post by quedefantasma on 2011-02-09
Estimados, 

Tengo como indica el titulo un servidor con Ubuntu server 9.10 + webmin 1.510 este servidor brinda acceso a internet para una red mixta ubuntu / windows mediante squid, iptables, etc...tambien se sirven algunas webs basicas con apache y esta a prueba instalado un e-groupware. La red consta de unas 20 maquinas.

Todo funciona de maravillas, cuando funciona...

Intermitentemente, y sin periodicidad (a veces 3 o 4 veces por día...otras veces transcurren días sin este problema) y sin razón aparente hasta el momento, este equipo se desconecta de las redes (tiene instaladas dos placas de red, una a la red local y otra a internet) y deja a los usuarios sin servicio...y tampoco deja ingresar al webmin por ip-local.

El equipo sigue funcionando, pero las conexiones solo se re-establecen tras reiniciar el equipo...

Por donde comienzo a investigar el problema? Logs? que tipo de Logs pueden darme algun indicio de esto? Se escuchan ideas y sugerencias...

Muchas Gracias.

Mariano

---

### Post by Wiredfixer on 2011-02-09
Revisar los Logs...
 /var/log/messages

Sin embargo, yo creo que haria falta verificar que hardware de red tienes operando, ya que todo puede apuntar a que en realidad tengas un problema por ese rumbo.

Dices que el equipo esta siendo usado como Proxy, te recomiendo que cheques la carga del sistema por un lado, y por otro lado.. Estas usando Algun graficador para los logs? A veces me ocurria en un server de eBox (ahora Zentyal) que el graficador se comia el proceso del equipo y me desconectaba.

 Tambien verifica tus dispositivos de red, switches y otras cosas, que no vayan a estar enviando malas señales que te colisionen tus Ethernet o tu red en si.

---

### Post by guillermolisi on 2011-02-09
Cuando el server queda "sordo", lo hace sobre las dos interfaces de red o solo sobre una ?

Fijate si en /var/log/dmesg se registra algo.

Podes monitorear las dos placas de red con el comando iftop
```
sudo iftop -i eth0
```por ejemplo.

Edit: Alguna razon para no actualizar ese servidor a 10.04 ? En poco tiempo mas se quedara sin soporte (actualizaciones)

---

### Post by quedefantasma on 2011-02-10
> **Wiredfixer said:**
> Revisar los Logs...
 /var/log/messages

Sin embargo, yo creo que haria falta verificar que hardware de red tienes operando, ya que todo puede apuntar a que en realidad tengas un problema por ese rumbo.

Dices que el equipo esta siendo usado como Proxy, te recomiendo que cheques la carga del sistema por un lado, y por otro lado.. Estas usando Algun graficador para los logs? A veces me ocurria en un server de eBox (ahora Zentyal) que el graficador se comia el proceso del equipo y me desconectaba.

 Tambien verifica tus dispositivos de red, switches y otras cosas, que no vayan a estar enviando malas señales que te colisionen tus Ethernet o tu red en si.

Hola, gracias por tu respuesta...voy a mirar estos logs que me decis.

Si, es probable que sea un problema de hard y ojala! ya veremos... No estoy usando ningun graficador por el momento. Yo supongo que el resto de los dispositivos funcionan bien...ya que en general la red esta funcionado muy bien salvo por esto del proxy de internet.

---

### Post by quedefantasma on 2011-02-10
> **guillermolisi said:**
> Cuando el server queda "sordo", lo hace sobre las dos interfaces de red o solo sobre una ?

Fijate si en /var/log/dmesg se registra algo.

Podes monitorear las dos placas de red con el comando iftop
```
sudo iftop -i eth0
```por ejemplo.

Edit: Alguna razon para no actualizar ese servidor a 10.04 ? En poco tiempo mas se quedara sin soporte (actualizaciones)

Hola Guillermo, gracias por tu respuesta.

Buena pregunta! Todavia no lo probe... cuando se queda sordo, seguro lo hace en la placa lan...voy a probar la otra, ver los logs y el comando que me indicas.

Pensaba hacer el upgrade en estos dias... en el camino surgió esto.

---

### Post by quedefantasma on 2011-02-18
Estimados, lamentablemente no tuve tiempo / opción de poder mirar los logs y otros comandos que me recomendaran...(Los usuarios de la red se ponen un tanto nerviosos si no funciona el proxy de internet...Uds. saben como es esto)

Lo que si pude comprobar fue que solamente la interfaz interna era la que se quedaba sorda...pude accesar el equipo por la interfaz externa...resultado: cambio de placa de red, problema de hardware.

El equipo esta ahora funcionando sin problemas.

Muchas gracias a todos por la ayuda.

---

