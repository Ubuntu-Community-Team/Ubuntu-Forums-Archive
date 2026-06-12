---
title: "Deluge problematico"
date: 2008-10-25
forum: Software
---

### Post by ArgentinoGuy on 2008-10-25
Hola Gente,

ultimamente estoy teniendo un problema del tipo WTF!!! con el Deluge, resulta que lo usé para bajar el spore y lo bajó barbaro y al toque y eso que eran 4 gigas. Bue, resulta que ahora quiero ponerme a bajar algo de musica desde mininova y cuando abro el torrent y empieza a descargarlo me mata la red!!! osea... no me deja la notebook sin conexion, me voltea la conexion del modem scientific atlanta de fibertel.

Bue, no tengo idea que es lo que esta pasando, si alguien tuvo o tiene este problema y se le ocurre como solucionarlo que pase la data please!

Saludos!!!

---

### Post by rojojuan on 2008-10-25
> **ArgentinoGuy said:**
> Hola Gente,

ultimamente estoy teniendo un problema del tipo WTF!!! con el Deluge, resulta que lo usé para bajar el spore y lo bajó barbaro y al toque y eso que eran 4 gigas. Bue, resulta que ahora quiero ponerme a bajar algo de musica desde mininova y cuando abro el torrent y empieza a descargarlo me mata la red!!! osea... no me deja la notebook sin conexion, me voltea la conexion del modem scientific atlanta de fibertel.

Bue, no tengo idea que es lo que esta pasando, si alguien tuvo o tiene este problema y se le ocurre como solucionarlo que pase la data please!

Saludos!!!

Fibertel te lo bloquea y no baja nada.

---

### Post by hictio on 2008-10-25
> 
Fibertel te lo bloquea y no baja nada.


Fibertel bloquea BitTorrent, asi directamente? O mas bien pone un cap al uso de ancho de banda?
Yo use handbrake en Ubuntu y ctorrent en OpenBSD varias veces para bajar cosas en Fibertel sin problemas.
"Sin problemas" quiero decir que no se me bloqueaba la conexion, ni nada muy raro, se iba al demonio la navegacion, por el usio del ancho de banda del torrent, pero era algo normal.

---

### Post by ArgentinoGuy on 2008-10-30
Tendria que estar prohibido por ley que hagan eso :S les kb la choreada de cable :S

---

### Post by spg76 on 2008-10-31
Yo tuve ese tipo de problemas con Deluge. En mi caso resulto ser que tenia demasiadas conexiones "half-open". En las preferencias de Deluge podes modificar el valor.
Aunque tambien puede ser la truchada que hace Fibertel.

---

### Post by lega on 2008-10-31
fijate que hay una actualización en la página de Deluge 1.04 que arregla varios bugs

> Deluge 1.0.4 (31 October 2008)
 Core:
  * Fix #560 force an int value for global max connections
  * Fix #545 use proper values in ratio calculation
  * Fix UPnP again..

 GtkUI:
  * Fix #565 wait for the deluged process to start to prevent defunct processes

 

---

