---
title: "Pierdo la Conexión despues de Torrentear.."
date: 2009-11-28
forum: Software
---

### Post by alejandro.mc on 2009-11-28
Hola gente. Bueno lo que me pasa es lo siguiente:

A la noche me voy a dormir pero antes abror mi programa para bajar torrents, todo bien, en cinco minutos se conectan todas las seeds y peers necesarias, pero a traves de la noche algo ocurre y a la mañana siguiente cuando voy a ver el programa, si quedan dos seeds y algun peer conectado es mucho, y la velocidad de bajada quedo en 3 o 4 kb cuando al comienzo de la noche iba a 160 kb mas o menos..

Que tengo?

Sistema operativo: Ubuntu 8.04 LTS (pero tambien tengo y me pasa en Windows)
ISP: Arnet 3 megas
Modem Router: Edimax AR-7064Sg+
Software de Torrent: Deluge (en Ubuntu) y Utorrent (en Windows)

Alguien tiene algunas idea??

Saludos!!

---

### Post by Mauro22 on 2009-11-28
En lo demas te anda bien??


Torrent no garantiza que la velocidad sea constante.

---

### Post by Aspergillus on 2009-11-28
la velocidad en gran medida depende de la cantidad de seeds que tenga el torrent y del porcentaje que estan compartiendo dichos seeds, fijate que ya sea en deluge o utorrent generalmente en la parte inferior del programa te muestra esa informacion, en deluge fijo que es en la pestaña de "pares"

---

### Post by alejandro.mc on 2009-11-30
No no el problema tiene que ver con la conexion, se van perdiendo seeds y peers, y es "como si se fuera perdiendo la conexion lentamente". Cierro el deluge al otro dia, intento usar internet, y esta inutilizable o super lenta. La sensacion es que arnet se da cuenta del p2p y te baja la conexion, es la "sensacion".

No se..

Alguna idea?

Saludos!

---

### Post by guillermolisi on 2009-11-30
Por lo pronto pregunto, usas encriptacion de protocolo ? 

Esta es una buena forma de que los ISPs no puedan "leer" que clase de paquetes traficas en la red y no los dropeen al ver que son P2P.

---

### Post by luks911 on 2009-11-30
> **alejandro.mc said:**
> No no el problema tiene que ver con la conexion, se van perdiendo seeds y peers, y es "como si se fuera perdiendo la conexion lentamente". Cierro el deluge al otro dia, intento usar internet, y esta inutilizable o super lenta. La sensacion es que arnet se da cuenta del p2p y te baja la conexion, es la "sensacion".

No se..

Alguna idea?

Saludos!

No descartes la sensación. A un amigo le pasa o pasaba algo parecido con Telecentro: después de un rato bajando torrents normalmente, la conexión se le cortaba. Y yo, con Speedy, que puedo navegar y descargar de servidores locales a hasta 2mb, pero los torrents no superan los 32 KB/s, o sea una conexión de 256k.
Como dice Guillermo, probá cifrando los torrents (Deluge tiene la opción en Preferencias > Red > Cifrado) y cambiando el puerto. Aunque no es seguro que funcione.

---

### Post by alfplayer on 2009-11-30
No se si es problema de ese router, pero algunos modems o routers tienen problemas con un número grande de conexiones. Hay algunos que pueder resolver el problema deshabilitando DHT (obviamente quedando con funcionalidad reducida).

---

### Post by alejandro.mc on 2009-11-30
Si el cifrado (encriptado) esta activado..

El tema es que con DHT activado tendria que funcionar bien, por eso no lo desactivo..no es tipo esencial eso para compartir decentemente?

Algunas ideas mas?

Gracias por todo lo aportado de momento!

Saludos!

ALejandro.

---

### Post by z37a on 2009-12-01
Que modem tenes?, algunos modems viene capados de memoria y cuando establecen varias conexiones simultaneas se cuelgan o empiezan a fallar, aparte claro del filtro, a mi me filtran en Fibertel, cuando supero una cantidad de conexiones se me hace imposible navegar.

---

### Post by alejandro.mc on 2009-12-03
Sistema operativo: Ubuntu 8.04 LTS (pero tambien tengo y me pasa en Windows)
ISP: Arnet 3 megas
Modem Router: Edimax AR-7064Sg+
Software de Torrent: Deluge (en Ubuntu) y Utorrent (en Windows)

---

### Post by guidito73 on 2009-12-03
"En teoría" Arnet no limita P2P. Pero puede que hagan algun rastreo de puertos o algo así.

Podrías probar cambiando periódicamente el puerto del router que tenés abierto. Quizás ayude también limitar el número de conexiones que abre el torrent, para pasar más desapercibido. Habría que fijarse también si el router no tiene problemas saturando la tabla de nateo.

---

### Post by alejandro.mc on 2009-12-04
Mira Arnet no es, porque conozco a alguien ahi y me dijo hace mil años que no limitaban P2P. Y el router tampoco porque en la otra casa funcionaba con Arnet 1 Mega (tambien por lo que Arnet no es).

Me vas a preguntar si el Deluge estaba configurado igual? Creo que si, no se.

Bueno gracias a todos igualmente!

Saludos!

---

### Post by alejandro.mc on 2009-12-12
Solucionado!!

El problema es que aunque tengas el mejor modem-router del planeta hay un numero maximo de conexiones que puede manejar, si pones mas se cuelga. Despues de probar varios dias fijé el numero de conexiones posibles en 300, y por ahora no se cuelga, todo anda super!!

Saludos!!

EDIT: En realidad la solucion vino cuando puse en las Opciones de COnfiguracion del Deluge, en la solapa de Network, en Outbound: Forced y en Inbound: Forced, y donde esta seleccionado "Either" puse "Stream Everything"

---

