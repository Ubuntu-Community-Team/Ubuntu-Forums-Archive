---
title: "no conecta wifi ubuntu 9.04 y si uso pppoeconf deja de gestionar la red wifi"
date: 2009-08-16
forum: Software
---

### Post by crynof on 2009-08-16
Hola

Ojala lean lo que escribi xD

, tengo un problema al conectarme al internet Wifi
Mi coneccion es mediante un router wifi que lo estoy usando como switch, por q el internet que tengo viene de otro router sin wifi y por eso hago pasar el internet por ese switch wifi.
Bueno ese no es el problema, sino que la coneccion es ADSL, necesito usuario y password para coenctarme, lo que e hace otro inconveniente.
Sucede que cuando quiero conectarme a mi red, coloco la pass wpa y se queda intentando conectar, pero al rato dice que la red esta desconectada, osea no se conecta, tambien probe con otra red que no es mia, que estaba sin clave, y tampoco conecta.
Otra cosa, cuando le doy conectar a mi red y la esta buscando, me voy a pppoeconf y configuro mi usuario y pass, y el internet me funciona, pero solo mientras esta intentando conectar, pero lamentablemente de todos modos desiste y la da por desconectada al rato, aun cuando el internet este funcionando.
Si reinicio el pc, despues de haber configurado con el pppoeconf, en el networkmanager, en la parte de redes inalambricas me dice un lindo "El dispositivo no esta sinedo gestionado", por lo q tengo q ir a etc/networks/interfaces, borrar su config, reiniciar y ahi recien puedo volver a ver las redes, pero si vuelvo a configurar el pppoeconf, pasa lo mismo y las pierdo.
Me di cuenta que la red wifi, solo conecta bien cuando cambio el DHCP automatico, por la opcion, red local, pero esto no me soluciona el problema, por que donde uso adsl, de todas maneras al reiniciar, me va a dejar de gestionar las redes.

Lo mas curioso es que yo antes habia usado por bastante tiempo el Ubuntu 9.04 sin problemas, conectaba todo bien y automatico, tanto instalado como con el live cd, pero hace unos dias formatee, lo reinstale y no hay caso, ni con Live cd ni instalado se conecta bien.
Si fuese un bug, y se actualizo con el internet, al usar el mismo live cd que use hace tiempo, deberia andar bien la coneccion no?, por q el live cd no se modifica y esta tal cual como lo habia utilizado hace meses.
Que podra ser, alguien sabe por que se produjo es eproblema de un rato para otro??
Saludos y muchas gracias
disculpen por hacerlos leer tanto xd

---

### Post by la.blaia on 2009-08-18
Hola, me pasa algo parecido el wifi funcionaba bien, tanto WPA comp WEP, reinstalé el ubuntu 9.04 y dejaron de funcionar las redes wireless. He probado con distintas tarjetas. Todas funcionabian bien bajo linux. Instalé el Debian y pasa lo mismo. Con las lives-CD de ubuntu también. Pero probé un live-CD basado en SLAX y conseguí conectarme. He probado a configurar manualmente la conexión pero sigue igual. Si alguien me puede ayudar. Gracias.

---

### Post by pablo.s on 2009-08-18
Prueba con WICD.
Gestiona mejor las redes
WIFI que NetworkManager.

---

### Post by guillermolisi on 2009-08-18
> **pablo.s said:**
> Prueba con WICD.
Gestiona mejor las redes
WIFI que NetworkManager.
La instalacion del WiCD desinstala el NM. Comento para que no se sorprendan.

---

