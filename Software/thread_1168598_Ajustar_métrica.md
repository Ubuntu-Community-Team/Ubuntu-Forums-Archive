---
title: "Ajustar métrica"
date: 2009-05-24
forum: Software
---

### Post by JUTGtgRB7z on 2009-05-24
Hola a todos. Tengo dos conexiones a internet una a través de un Cablemodem Motorola sb5101surfboard que pasa por un router wifi y otra através de un Pirelli Discuss que está conectado por USB a mi PC. El problema que tengo es que no se como elegir la conexion del Pirelli como predeterminada o desactivar el Motorola ya que este lo uso a traves de la red wifi nada mas. Según tengo entendido esto se hace con la métrica pero no se como ajustarla.

---

### Post by guillermolisi on 2009-05-24
> **pmzerdan said:**
> Hola a todos. Tengo dos conexiones a internet una a través de un Cablemodem Motorola sb5101surfboard que pasa por un router wifi y otra através de un Pirelli Discuss que está conectado por USB a mi PC. El problema que tengo es que no se como elegir la conexion del Pirelli como predeterminada o desactivar el Motorola ya que este lo uso a traves de la red wifi nada mas. Según tengo entendido esto se hace con la métrica pero no se como ajustarla.
A ver si entiendo bien.

Tenes dos conexiones distintas a Internet, una a traves de Cablemodem y otra a traves del Pirelli (que supongo es ADSL).

Vos queres dejar de usar una de las dos y que todo el intercambio "wired" vaya por el Pirelli mientras el WiFi salga por el Cablemodem. Es asi ?

Si es asi tenes podrias cambiar el default gateway en las maquinas que estan cableadas, ya que deberan salir por el Pirelli (que seria el defult gateway) mientras las maquinas enla red inalambrica saldrian por otro gateway distinto.

Esta es una forma, que no contempla load balancing ni switching transparente. Solo acceso a cada conexion segun estes en la red cableada o en la inalambrica.

---

### Post by JUTGtgRB7z on 2009-05-24
> **guillermolisi said:**
> A ver si entiendo bien.

Tenes dos conexiones distintas a Internet, una a traves de Cablemodem y otra a traves del Pirelli (que supongo es ADSL).

Vos queres dejar de usar una de las dos y que todo el intercambio "wired" vaya por el Pirelli mientras el WiFi salga por el Cablemodem. Es asi ?

Si es asi tenes podrias cambiar el default gateway en las maquinas que estan cableadas, ya que deberan salir por el Pirelli (que seria el defult gateway) mientras las maquinas enla red inalambrica saldrian por otro gateway distinto.

Esta es una forma, que no contempla load balancing ni switching transparente. Solo acceso a cada conexion segun estes en la red cableada o en la inalambrica.

Es así como lo interpretaste ¿me podrias explicar como hacerlo?

---

### Post by guillermolisi on 2009-05-24
> **pmzerdan said:**
> Es así como lo interpretaste ¿me podrias explicar como hacerlo?
Editas la configuracion de la interface cableada de una y otra maquina (supongo que estas usando Network Manager o algun otro gestore de redes, sino hay que editar un archivo a mano).

Donde figura la IP de la puerta de enlace por defecto le pones la IP de tu modem/router al cual llegas con los cables de red a esas maquinas.

Con eso deberia ser suficiente y no deberia interferir con la red inalambrica ya que el router inalambrico se conecta por otra interface de red a la notebook, por ejemplo.

Si no fui suficientemente claro, hacemelo saber.

---

### Post by JUTGtgRB7z on 2009-05-28
> **guillermolisi said:**
> Editas la configuracion de la interface cableada de una y otra maquina (supongo que estas usando Network Manager o algun otro gestore de redes, sino hay que editar un archivo a mano).

Donde figura la IP de la puerta de enlace por defecto le pones la IP de tu modem/router al cual llegas con los cables de red a esas maquinas.

Con eso deberia ser suficiente y no deberia interferir con la red inalambrica ya que el router inalambrico se conecta por otra interface de red a la notebook, por ejemplo.

Si no fui suficientemente claro, hacemelo saber.

Perdon por mi ignorancia pero entendí todo y me quedó asi:
[IMG]http://i437.photobucket.com/albums/qq94/pmzerdan/Varios/Capturadepantalla.png[/IMG]
Lo que sigue pasando es que se conecta por defecto a la otra red. Por el momento recurrí a desconectarla hasta encontrar la solucion.

---

