---
title: "Usar Ubuntuone en Lubunu (sin instalar qt)"
date: 2013-12-01
forum: Software
---

### Post by Daniel TL on 2013-12-01
Buenas noches!

Estoy usando Lubuntu 13.10, instalado desde cero (no es una actualización). Quiero usar el servicio Ubuntuone, sin instalar el paquete de librerías qt. Y no he podido :(


Explico mejor mi situación. En este momento, tengo instalados los siguientes paquetes:

daniel@netbook:~$ dpkg -l | grep ubuntuone
ii  python-ubuntuone-client                   13.10-0ubuntu1 
ii  python-ubuntuone-control-panel        13.09-0ubuntu1
ii  python-ubuntuone-storageprotocol     13.10-0ubuntu1
ii  ubuntuone-client                             13.10-0ubuntu1
ii  ubuntuone-client-data                      13.05-0ubuntu1


Y tengo corriendo lo siguiente:

daniel@netbook:~$ ps ax | grep ubuntuon
 4554 ?        Sl     0:06 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon


Verifico el estado del demonio, y observo lo siguiente:

daniel@netbook:~$ u1sdtool -s
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING


Es decir, no está conectado y no sincroniza. Entonces corro los siguientes comandos, uno después del otro:

u1sdtool --start
u1sdtool -c


Pero cuando pido nuevamente el estado del demonio, nada pasa...

daniel@netbook:~$ u1sdtool -s
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING



Y lo confirmo con

daniel@netbook:~$ u1sdtool --current-transfers
Current uploads: 0
Current downloads: 0


Sin embargo, en mi directorio local de Ubuntuone tengo varios archivos que no han sido sincronizados con la nube.

¿Cómo los sincronizo, sin instalar la parafernalia de qt?


En esta netbook tengo Ubuntu desde el 8.10 Lo vine actualizando hasta la versión 13.04, en que decidí hacer una instalación limpia de Lubuntu, ya que si bien hace un par de versiones que venía usando el entorno Lubuntu, Ubuntu seguía ahí, por debajo, y la pobre netbook se arrastraba cada día más. Hasta el momento de la instalación de Lubuntu 13.10 (pisé sólo la partición /, la /home quedó como estaba y no perdí ni mi usuario ni mis archivos) usaba Ubuntuone en background sin problemas, y todo se sincronizada sin problemas. Pero desde que tengo Lubuntu "puro" no pude sincronizar más. Uso también Dropbox y con esa herramienta no tengo problemas.

¿Es posible forzar la sincronización, aunque sea haciendo un script? Reitero: no quiero instalar la paquetería que propone el cliente gráfico oficial, ya que supongo (supongo...) la compu se va a ralentizar de manera innecesaria al instalar todas las dependencias de qt.

Les pido me dejen una sugerencia, una pista como para resolver este problema. Muchas gracias!

---

### Post by Daniel TL on 2013-12-22
Para que quede registrado, les cuento qué hice :)

No pude resolver el problema tal como lo tenía planteado, así que instalé el paquete ubuntuone-control-panel-qt y todas sus dependencia.

A continuación, y como era de esperarse, puede loggearme y sincronizar todo sin problemas. Y en el panel de configuración coloqué que deseo que el demonio se inicie y se conecte con cada reinicio de la PC.

Luego desinstalé ese paquete y varias de sus dependencias qt (claramente, eran aspectos gráficos de "algo" más profundo), reinicié la PC y funciona! Es decir, ya no tengo ese panel qt ni una gran paquetería de esas librería (tenía un par instaladas antes de esta maniobra, así que las dejé ahí) y mi Ubuntuone se conecta y sincroniza en background sin problemas.


Ahora tengo esto:

daniel@netbook:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE


Y estos son los paquetes que tengo instalalados:

daniel@netbook:~$ dpkg -l | grep ubuntuone
ii  python-ubuntuone-client              13.10-0ubuntu1
ii  python-ubuntuone-control-panel       13.09-0ubuntu1
ii  python-ubuntuone-storageprotocol     13.10-0ubuntu1
ii  ubuntuone-client                     13.10-0ubuntu1
ii  ubuntuone-client-data                13.05-0ubuntu1
ii  ubuntuone-control-panel


Y funciona! :)


Por si a algún otro ubuntero le sirve :)

---

