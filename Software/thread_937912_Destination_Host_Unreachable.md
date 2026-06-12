---
title: "Destination Host Unreachable"
date: 2008-10-04
forum: Software
---

### Post by sofocles92 on 2008-10-04
En las ultimas horas creo que he aprendido mucho y he dormido muy poco. El problema es que mi nueva instalación de Ubuntu 8.04 no se conecta a Internet. He probado de todo. Actualmente la configuración es IP fija y todos los datos parecen están bien.

Para llegar a esto (siguiendo la ayuda) cambié el la entrada del aliases "alias net-pf-10 ipv6" a "alias net-pf-10 off" y en el grub le puse la opcion pci=noacpi

Si hago ping al localhost: bien
Si hago ping a la ip de la máquina: bien
Si hago ping a la puerta de enlace: DESTINATION HOST UNREACHABLE

Haciendo lshw -c network me da (entre otras cosas)
RTL-8169 Gigabit Ethernet
logical name eth0

Wireless interface
logical name wlan0

No se si podría haber alguna incompatibilidad con la placa.

Pido, por favor, si alguien puede ayudarme. Me dolería profundamente tener que volver a instalar el XP.

Si me pedís los datos de iwconfig u otros decidme, por favor, las lineas que os interesan porque si no tengo que teclear todo ya que estoy en otro ordenador.

Muchas gracias.

Sof
Pd.- Juro que me he tirado dos días buscando en Google y este y otros foros. He tratado de hacer todo lo que he encontrado que parecía relacionado pero no he conseguido grandes avances... o si, no se, me da la sensación de que no tendría que estar muy lejos de conseguirlo. Ojalá.

---

### Post by ariel on 2008-10-04
En el 99.999999% de los casos, la interfaz ethernet en linux anda "out of the box", usando dhcp (ip dinamica)

La primera pregunta seria: cuando conectas el cable de la ethernet a tu PC, se prende la lucecita (LED) de conexion que esta pegada al conector? (si no es asi, puede ser que el problema sea de cableado)

Si la lucecita se prende, podes postear la salida de:

> ifconfig -a

Te va a dar informacion sobre todas las interfaces de red; fijate el parrafo asociado a tu ethernet (probablemente eth0)

> ip route

Este te va a mostrar adonde apunta la ruta default (deberia apuntar a la ethernet; ej:
> ip route
192.168.1.0/24 dev ath0  proto kernel  scope link  src 192.168.1.200 
169.254.0.0/16 dev ath0  scope link  metric 1000 
default via 192.168.1.1 dev ath0  metric 100 


Otra que podes hacer es:

> dmesg | tail -f

... y desconectar el cable de la ethernet, esperar unos segundos y reconectar; vas a ver en tiempo real si el kernel se esta quejando por algo (postea la salida si ves errores)

---

### Post by sofocles92 on 2008-10-04
Gracias por contestarme.

Mi conexión es wifi. He hecho todo lo anterior y no noto nada raro (aunque, claro, es la primera vez que llego "tan lejos" en linux).

He probado el modo itinerante, dhcp e ip estática. Con esta última me he quedado porque me da que tiene que ser por aquí.

ip route lo que sale como default es mi puerta de enlace. O sea, el modem cable: 192.168.0.1

Entrando en el modem aparece mi máquina como cliente conectado, con su ip si bien es cierto que al cabo de algunos minutos de inactividad en vez de la ip pone ERROR aunque sigue saliendo la mac addres de mi maquina.

En fin, que llevo dos días sin apenas dormir. Se me entumecen las piernas y no progreso. Es tal la desesperación (uso internet para trabajar) que me estoy bajando el live CD de "Ultima Linux" con el portatil que me han prestado por si es un problema de compatibilidad de Ubuntu con mi hardware.

Me fastidia molestar pero ojalá me siguieran ayudando un poco más.

Gracias

Sof

---

### Post by luks911 on 2008-10-04
¿A ver si entendí bien? Querés conectarte con el wifi y no podés. Si es así, se me ocurre que Ubuntu no está detectando tu placa. Ejecutá

```
iwconfig
```

para ver el listado de dispositivos wifi activos. Pegá el resultado acá. Y, para adelantar un paso, también pega el resultado de 

```
lspci
```

que entre otras cosas va a mostrar el modelo de tu placa. A partir de ahí, y si no me equivoqué desde el principio, alguien va a poder ayudarte a hacer funcionar el wifi.

Saludos

---

### Post by sofocles92 on 2008-10-04
Nuevamente gracias por darme esperanza :)

No se me ocurre ahora como copiar y pegar desde una máquina a otra pero lo resumo:

iwconfig:

lo
eth0
wmaster0
Todas las anteriores "no wireless extensions"

wlan0
Empieza por IEEE 802.11g ESSID:"R-wlan5D"
Mode:Managed etc, etc con Frequency y todo eso
...
Encryption key:3230-etc
...
termina en Missed Beacon:0

Si hace falta lo copio entero pero por el momento tiene que ser a mano :frown:

lspci:
Sale el modelo de mi placa que es
Realtek Semiconductor Co., Ltd RTL-8169 Gigabit Ethernet (rev 10)

Espero que tus palabras sean proféticas Luks

Un abrazo

Sof

---

### Post by luks911 on 2008-10-04
En primer lugar, me equivoqué. Pero no es tan malo: Ubuntu sí está detectando la placa wifi.
Ahora, ¿qué pasa si hacés click en el ícono de redes (arriba del escritorio a la derecha)? ¿Se despliega un listado en el que aparece la red wifi a la que te querés conectar?
Si aparece y clickeas en ella para tratar de conectarte, ¿qué pasa?

---

### Post by sofocles92 on 2008-10-04
> **luks911 said:**
> En primer lugar, me equivoqué. Pero no es tan malo: Ubuntu sí está detectando la placa wifi.
Ahora, ¿qué pasa si hacés click en el ícono de redes (arriba del escritorio a la derecha)? ¿Se despliega un listado en el que aparece la red wifi a la que te querés conectar?
Si aparece y clickeas en ella para tratar de conectarte, ¿qué pasa?

Cuando le doy al icono solo sale la opción "configuración manual" (esta configurado como IP estática). Si lo pongo en modo itinerante si sale el nombre de mi red. Entonces pulso sobre ella y tengo que introducir la clave de red. La pongo pero no pasa nada... al cabo de un rato se abre la ventana otra vez para introducir la clave. La clave es correcta (wep128) y he probado todas las opciones por si acaso, pero nada.

ASí que he dejado la configuración IP estática que funcionaba perfectamente en Windows XP.

Pero ya ves, los demonios de Windows deben haberse enfadado y me boicotean mi entrada en Linux.

Estoy viendolo todo muy crudo.

Estoy pensando si acaso hay un bug en Ubuntu con mi tarjeta de red. Si hago un ethtool eth0 después de mostrar todos los datos de mi Realtek RTL-8169 (correctos) hay un parametro que dice "link detected: no".

La verdad es que ando perdido y algo más que desesperado. He leido casi infinitas respuestas de foros en todos los idiomas. Añadido a que se muy poco de Linux... empiezo a darme cuenta de porque Linux no es el SO mayoritario. Un usuario de Windows de toda la vida se empieza a encontrar con estos problemas y sale echando pestes. No será mi caso (siempre he soñado con tener Linux y que todo fuera maravilloso y tal y tal) pero, por el momento, ando bastante desanimado.

En fin, perdona el rollazo pero es que estoy con los nervios que se pueden pinchar aceitunas ](*,)

Saludos cordiales,

Sof

---

### Post by luks911 on 2008-10-04
Vamos, a no desesperar. Tampoco soy un experto en linux ni en redes, pero hay un par de cosas que se me ocurren.
1) No sé para qué sirve ethtool, pero no debe funcionarte porque al pasarle el parámetro eth0 le estás preguntando por la conexión cableada y no por el wifi.
2) Parece que el problema es con el cifrado de la red. Probá abrirla totalmente desde el router y tratar de conectarte, al menos como prueba.
3) A algunos (tal vez es tu caso) les trae problemas el Network Manager (el ícono de redes desde el que querés conectarte). Una buena alternativa es reemplazarlo por WICD. [Acá]("http://ubunlog.wordpress.com/2008/06/13/wicd-gestiona-facilmente-tu-conexion-wireless/") hay un tutorial sobre él. Si no tenés internet en la máquina con Ubuntu, podés descargar un paquete deb de WICD desde [acá]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=629280") para llevarlo a tu máquina en un pendrive.

Espero que algo de esto sirva.

Saludos

EDITADO: Si te llega a servir el Wicd y lo instalás con el deb, después sí agregá el repositorio así se actualiza automáticamente.

---

### Post by sofocles92 on 2008-10-05
=D>

Casi lloro... de alegría.

Muchas gracias Luks. Estoy en Internet. Me encanta el Wicd.

Estoy tan emocionado que se me ha pasado hasta el sueño (hoy dormí solo 3 horas). Aun me queda una cosa como en un capítulo de Friends en el que los chicos encontraron un canal porno en la tele y no se atrevían a apagarla por si se iba. No se que pasará al reiniciar... pero ya lo comprobaré. El caso es que ahora SE que puedo conectarme. Y eso ya es mucho después del infierno que he pasado :)

Bueno, te debo una. De informática no se pero si tienes alguna duda médica (ojalá que no) me tienes a tu disposición.

Un abrazo, amigo.

-Sof-

Pd.- Luego que reinicie editaré el post con [SOLUCIONADO]

---

### Post by sofocles92 on 2008-10-05
Bueno, tenemos un  éxito parcial.

He conseguido ver una pagina web y por un rato hacer ping a la puerta de enlace resultó exitoso.

Ahora con el Wicd se conecta. Si entro en el router (con otra PC) aparece la IP de la máquina con Ubuntu como cliente. Y, sin embargo, el ping a la puera de enlace no es exitoso ni puedo navegar por internet.

Misterio.

Como dije al menos se que me he conectado antes y seguramente podré hacerlo. Estamos cerca. Supongo.

¿Te importa seguir ayudándome?

Gracias.

-Sof-

---

### Post by sofocles92 on 2008-10-05
Una cosa más que me llama la atención. El Wicd NO modifica el archivo "interfaces". La información de la máquina que veo en el panel del modem la pilla del archivo interfaces y no la que pongo en el Wicd... a pesar de que este último dice que está conectado a la red.

Me ha resulado muy curioso.

Espero que sirva para algo esa info.

Gracias

-Sof-

---

### Post by luks911 on 2008-10-05
Bien, ya tenemos algo. Como te decía, tampoco soy experto y ni siquiera uso WICD, así que estoy un poco a ciegas. Pero quedan cosas por probar.
1) Descansa un poco ;)
2) Si WICD dice que estás conectado y aun así no podés navegar, probá lo siguiente:
Ejecutá en una terminal
```
route
```
Si en efecto estás conectado, debería devolverte algo así
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     *               255.255.255.0   U     0      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 ath0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ath0

```
En el ejemplo, que es de mi máquina, 192.168.1.1 es mi puerta de enlace. En la misma ubicación debería aparecer la tuya si estás conectado. Si aparece y aún no navegás, es posible que a) sea un problema de DNS o b) que tu máquina no tenga asignada una IP. Si no aparece la puerta de enlace pasá al punto 3.
a) Para comprobar los DNS, fijate dónde los tenés configurados: ¿en las opciones de WICD? ¿en el router? Esos datos deberían estar bien. Podés hacer una prueba enviando un ping a un número de ip en lugar de una dirección web.
```
ping - c 5 64.233.161.99
```
Si funciona, es porque hay algo mal con los DNS.
b) En cuanto a la IP. Fijate que al ejecutar
```
ifconfig
```
en la información de tu dispositivo de red (si mal no recuerdo era wlan) entre otros datos debe figurar "inet dirección: número_de_IP_de_tu_máquina".
Si falta la IP revisá qué tipo de conexión usás, ¿dinámica o estática? En el primer caso tiene que estar habilitado el servidor DHCP de las opciones del router para que le asigne una IP a tu máquina cuando se conecte. Si es estática debés pasarle al WICD tu IP.

3) Si entre los datos que devuelve el comando route no está la puerta de enlace, entonces no estás conectado al router. Leyendo por ahí veo que pueden aparecer algunos problemas con WICD y las claves WEP. Para verificarlo: fijate a) que el mismo tipo de encriptación sea el que está configurado en el router y en el WICD, b) que estás escribiendo bien la clave, c) por raro que parezca leí que en algunos casos necesitaron escribir la clave WEP en el WICD entre comillas (""), podrías probarlo, y d) directamente empezar por abrir la red y luego cambiar el tipo de cifrado, a WPA, por ejemplo.


Uf, espero que toda esta parrafada sirva de algo.
Saludos

---

### Post by ariel on 2008-10-05
> **sofocles92 said:**
> Nuevamente gracias por darme esperanza :)

No se me ocurre ahora como copiar y pegar desde una máquina a otra pero lo resumo:

iwconfig:

lo
eth0
wmaster0
Todas las anteriores "no wireless extensions"

wlan0
Empieza por IEEE 802.11g ESSID:"R-wlan5D"
Mode:Managed etc, etc con Frequency y todo eso
...
Encryption key:3230-etc
...
termina en Missed Beacon:0

Si hace falta lo copio entero pero por el momento tiene que ser a mano :frown:

lspci:
Sale el modelo de mi placa que es
Realtek Semiconductor Co., Ltd RTL-8169 Gigabit Ethernet (rev 10)

Espero que tus palabras sean proféticas Luks

Un abrazo

Sof


Es todo un poco confuso. El chipset RTL8169 es el de la placa ethernet onboard de tu pc, no tiene *nada que ver* con wifi.

Saber que chipset WIFI tenes (y que driver el kernel esta usando) va a ayudar. Para averiguarlo, podes postear la salida de 
```
sudo lshw -class network
```El problema de que la conexion anda por un rato y despues se corta, puede venir por el lado del driver, o por el lado de dhcp.

Yo te recomendaria que no uses IP estaticamente configurada en la interfaz wifi. 

Si queres que la PC tenga siempre la misma IP, podes configurar una asignacion "static dhcp" en el router; cualquier router mas o menos moderno te permite configurar una tabla con MAC addresses y direcciones IP asociadas. Asi, en ubuntu poder dejar la configuracion "dhcp" que viene por default, y a la vez estar seguro de que la maquina recibe siempre la misma IP asignada por el router. Esta es la configuraion que yo uso (con wifi Atheros en mi PC) desde hace años sin ningun problema.

---

### Post by sofocles92 on 2008-10-05
Bueno, vamos paso a paso. Te puedo asegurar que todas tus "parrafadas" me sirven mucho porque, al menos, voy ganando experiencia en esto. Y estoy seguro de que se tiene que resolver.

1) Gracias, he salido a pasear un rato. Me ha sentado bien.

2) route

Sale la primera linea igual que la tuya (excepto que en mi caso es 192.168.0.0).
La segunda linea "link-local" no me sale
La tercera "default" 192.168.0.1 y todo lo demás igual
(Obviamente Interfaz es wlan0)

a) DNS

Las tengo configuradas en Widc y también en el modem.

Cualquier intento de ping que no sea al localhost o a la ip de mi máquina con Ubuntu produce "Destination Host Unreachable"

El mismo ping en un portatil desde el que te escribo con windows XP funciona correctamente.

b) ifconfig

Efectivamente, en wlan0, inet dirección: 192.168.0.134 (correcto)

Ahora está configurado como estática. Probé con DHCP y, una vez, por un rato breve, también tuve conexión. Normalmente no pilla IP, alguna vez si (y aún así sigue sin conexión a internet). Como dije, una sóla vez, navegué un rato y me dió tiempo a configurar Evolution y bajarme algún correo. No lo volví a conseguir. :confused:

3) Como salió correctamente en el "route" la puerta de enlace, así que estoy conectado al cacharro ¡yuuupi!. Pero de internet nada de nada. Claves y encriptación están bien. **PERO CUIDADO QUE AQUÍ VIENE LO GRACIOSO** No sólo he puesto comillas sino que incluso he puesto una clave aleatoria y SIEMPRE dice que se conecta. Estoy absolutamente seguro de que la clave está activada en el modem. Desde windows xp no se puede entrar sin la clave...

Mi modesta opinión: creo que hay algo más controlando la conexión. Mira...

Hice un /etc/init.d/networking restart y al reiniciar reconfiguró las network interfaces y lo hizo en modo DHCP (lo que no figura en la configuración del Wicd). Es más, dice:
"There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072

Pilló la ip 192.168.0.10 y ya había conexión a internet.

Pero desapareció al darle a desconectar al Wicd.

Sigo: **dejo desconectado Wicd**. Vuelvo a hacer /etc/init.d/networking restart ..... vuelve a pillar la misma ip y tengo conexión a internet.

Creo que aquí hay algo importante :) Ahora es cuestión de "fijar" esa forma de conectar.

Ahora he sido yo el de la parrafada. Pero casi es apasionante esto. Estás siendo un guía excelente.

Falta muy poco.

Espero impaciente tu próxima clase magistral :popcorn:

-Sof-

---

### Post by sofocles92 on 2008-10-05
[MAS DATOS]

Al cabo de tres o cinco minutos ya no puedo navegar. No se si es por inactividad (mientras escribía el post anterior en el portatil)o pasa de todas formas. Ahora voy a probar a seguir navegando seguido. He vuelto a hacer el /etc/init.d/networking restart y ha seguido el mismo comportamiento. DHCP, pilla la ip y ya entro a internet.

Miro el Wicd y detecta que estoy conectado. Pero no lo ha hecho el programa porque está todavía configurado como estática y con otra ip.

También me queda la duda de si cuando apague el equipo y vuelva a encenderlo se comportará igual.

Saludos

-Sof-

---

### Post by luks911 on 2008-10-05
Nada de clase magistral que lo mío es bien amateur, je.
Por lo que decís, haría dos cosas: por un lado, cambiar el cifrado WEP por algún otro, porque o no cumple su función o genera algún conflicto, o ambas.
Y por otro, como sugería Ariel más arriba, usaría una conexión dinámica por DHCP, que es lo que mejor funciona. A ver si con eso va.

EDITADO: Por lo del corte de la conexión, fijate si existe la posibilidad de que esté configurado el router para hacerlo cuando la conexión queda inactiva. Si es así, generalmente se cambia en el router.

---

### Post by sofocles92 on 2008-10-05
Ante todo disculpas mil. Estoy tan concentrado en esto que no me fijé que se había incorporado Ariel. Gracias a los dos.

Bueno, la conexión se pierde a los 10 minutos aún estando navegando activamente.

Voy a configurar el Wicd como DHCP. Pero parece claro que hay otros archivos de información que configuran la conexión. Quizá no se desinstaló todo lo del Net-Manager (no me acuerdo como se llamaba) de la instalación por defecto.

Al volver a hacer /etc/init.d/.... restart recupero la conexión.

Lo dicho, voy a configurar el Wicd y también voy a reiniciar (cruzo los dedos) a ver que pasa.

Os invitaría a tomar algo o a una barbacoa aunque sospecho que estamos algo lejos. Es lo que tiene Internet. Es que el mundo es un pañuelito con esto de interenet :)

Bueno, gracias de nuevo. Ya queda muy poquito para que empiece a relajarme con Ubuntu. Supongo.

-Sof-

---

### Post by luks911 on 2008-10-05
Es por mi amateurismo que no sé si hay otro archivo que afecte la configuración, pero para asegurarte de que no queden rastros del network-manager podés ejecutar
sudo aptitude purge network-manager
eso elimina los archivos de configuración del programa. Sólo de ese, así que debería ser seguro. Ciertamente, no sé cómo lo desinstala el WICD por lo que puede que haya algo de eso.

---

### Post by sofocles92 on 2008-10-05
Esto es aleatorio, o lo parece. Reinicié y ya no funciona. El /etc/init.d/.... restart hace lo mismo, trata de conseguir una dirección vía DHCP pero ahora no lo consigue y se queda sleeping.

Conecto via Wicd configuración estática y siempre dice que está conectado. Pero no va internet. Ahora hago otra vez el restart y dice que Network is down.

Configuro Wicd sin ip estática. Hago el /etc/...... restart y FUNCIONA otra vez. Tengo internet.

Desconecto desde el Wicd (configuración sin ip estática). Le vuelvo a dar a conectar y se queda "Obteniendo dirección ip..." De ahí no pasa.

Cancelo.

Lo hago con /etc/...... restart y tampoco pilla nada. ... Sleeping.

Vuelvo a hacer /etc/..... restart. Nada.

Cambio configuración de Wicd a ip estática. No le doy a conectar.

Hago /ec/....restart y termina encontrando ip... pero de todas formas no va internet.

Conecto con Wicd (ip estática). Dice que conectó. No accedo a internet. En este estado haciendo /etc/.... restart : Network is down.

Desconecto Wicd (recordemos, configurado como ip estática). Otra vez /etc/..... restart (estos comandos ya no se me van a olvidar más) :) y ¡hala! pilla ip (DHCP) y tengo internet.

He llegado a una especie de confuso bucle infinito.

Siento el rollo. ¿Sacais algo claro de esto?

Lo del purge todavía no lo he hecho. Por no precipitarme.

Ya me direis.

-Sof-

---

### Post by luks911 on 2008-10-05
Mmmm... si no entendí mal, la combinación que funciona es WICD en dinámica (o sea por dhcp) y luego networking restart.
Configurando wicd con conexión dinámica y sin ejecutar el networking restart, ¿funciona? Si no, una posibilidad (tal vez un tanto primitiva, pero que puede servir) es agregar el comando al archivo rc.local. Es un script que se ejecuta al inicio. Deberías hacer
```
sudo gedit /etc/rc.local
```

agregar la línea con el comando, es decir
```
/etc/init.d/networking restart
```

y guardar.

En cuanto a la intermitencia de la conexión. Si permanece, leí en Ubuntu-es alguien que lo solucionó instalando Rutilt. Sería un reemplazo para WICD, tal vez ayude. Igual tal vez habría que descartar alguna otra cosa antes.
Para Rutilt hay un tutorial [acá]("http://ubuntuforums.org/showthread.php?t=554089") (en inglés).

EDITO: una corrección importante, rutilt está en los repositorios así que no es necesario hacer lo que dice el tutorial para instalarlo. Lo instalas con synaptic o con sudo aptitude install rutilt. Para configurarlo no sé si hace falta todo lo del tuto. Es posible que tampoco y sea más sencillo.

---

### Post by sofocles92 on 2008-10-06
La combinación que funciona y parece que no se corta es exactamente esta:

Wicd configurado como IP ESTATICA. Se conecta automáticamente al iniciar pero no puedo acceder a internet. Entoces le doy a desconectar y hago /etc/init.d/networking restart. ---> Se conecta como DHCP, pilla otra IP y ya funciona internet. Y, por lo que parece, sin intermitencias. Y si hay algún corte (que parece que lo hay alguna vez) se recupera repitiendo el restart.

Vamos, no es que sea una forma de conectarse que de sensación de que el usuario controla el SO pero dada mi condición de novato y los problemas para llegar hasta aquí puedo, como se dice, "darme con un canto en los dientes". Ya llegará el momento en que corrija eso. Por lo pronto estoy experimentando Linux y me está gustando bastante. Eso si, hay que aprender muchas cosas. Pero eso también me gusta.

Desarrollando lo que dices. Si configuro Wicd como DINÁMICA y le doy a conectar se queda colgado esperando IP y no pasa de ahí. Raro. Pero me suena a que la forma de conectar efectiva es vía /etc/..... restart. Lo que no se es de dónde saca la configuración porque el archivo "interfaces" no tiene ahora mismo más información que las dos lineas de "lo".

Voy a hacer el script que dices a ver si me ahorro abrir la terminal cada vez que inicio y teclear el comando.

Seguiré informando. Me ha servido mucho la ayuda. Gracias de nuevo.

-Sof-

---

### Post by sofocles92 on 2008-10-06
Por cierto. Ya que puedo ahora copiar y pegar adjunto lo que sale al hacer el restart.

Antes de desconectar el Wicd:

```
root@sofocles-desktop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4364
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:89:68:da
Sending on   LPF/wlan0/00:11:50:89:68:da
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:89:68:da
Sending on   LPF/wlan0/00:11:50:89:68:da
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.10 from 192.168.0.1
DHCPREQUEST of 192.168.0.10 on wlan0 to 255.255.255.255 port 67
receive_packet failed on wlan0: Network is down
Terminated
Failed to bring up wlan0.
                                                                         [ OK ]

```

Después de desconectar el Wicd:

```

root@sofocles-desktop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 7691
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:89:68:da
Sending on   LPF/wlan0/00:11:50:89:68:da
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:89:68:da
Sending on   LPF/wlan0/00:11:50:89:68:da
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.0.10 from 192.168.0.1
DHCPREQUEST of 192.168.0.10 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.10 from 192.168.0.1
bound to 192.168.0.10 -- renewal in 263772 seconds.
                                                                         [ OK ]


```

---

### Post by sofocles92 on 2008-10-06
Más datos para regocijo de la audiencia :) y a modo de resumen:

A internet sólo puedo acceder si antes se ha conectado el Wicd configurado como IP ESTATICA. Lo desconecto y hago el restart. Esa es la secuencia que da resultado.

Cualquier otra no funciona.

---

### Post by luks911 on 2008-10-06
No sé mucho, pero es bien raro lo que te pasa. Por el archivo interfaces creo que no tenés que preocuparte, porque por lo que vi en mi caso no se modifica. 
Luego, probaría como te decía más arriba verificar que no quede nada de la configuración del network-manager con
```
sudo aptitude purge network-manager
```

Y desinstalaría con el mismo comando

```
sudo aptitude purge wicd
```

y lo volvería a instalar para probar directamente con la conexión dinámica, a ver si hay algún cambio.

Y como última opción, si con lo anterior no hay éxito, lo desinstalaría de nuevo y probaría con el rutilt que te comentaba más arriba. 

Ah, no sé si el dato lo pasate antes, pero ¿qué versión de Ubuntu usás 32 o 64 bits? ¿Y pegarías aquí el resultado del comando lspci, para saber exactamente qué wifi tenés?

Un saludo

---

### Post by sofocles92 on 2008-10-06
Te confieso una cosa: me da algo de miedo pugar lo que pueda quedar del network-manager y desinstalar el wicd. Porque ahora, aunque no me gusta la forma de conectarme... al menos se conecta y puedo trabajar:-?

Es que lo he pasado realmente mal estos días pasados. Tomé la impulsiva decisión de eliminar "definitivamente" el Xp e instalar Ubuntu. Luego al no poderme conectar me entró el pánico.

Claro que conociéndome, terminaré por hacer lo que dices (seguramente en los próximos minutos o, posiblemente después de disfrutar del día de hoy con internet) :)

Ya te comentaré.

Por lo pronto ahí va el lpsci:

```

root@sofocles-desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:03.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:03.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:03.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

Es la versión de 32 bits.

Hasta luego,

-Sof-

---

### Post by luks911 on 2008-10-06
Lo de reinstalar es cuestión de perder el miedo. Purgar el network-manager no tiene que traer problemas porque no lo estás usando. 
Y una cosa más, en los dispositivos listados no veo ninuno que sea wifi, ¿es por usb el que usás? ¿qué te devuelve el comando lsusb?

Saludos

---

### Post by sofocles92 on 2008-10-06
Otra cosa (de no poca importancia). Estoy comprobando que la velocidad de transferencia de datos o la velocidad de mi conexión es 10 veces menor que la que tenía con Windows Xp. Tengo una conexión por cable de 6 Mb de bajada y los distintos test que he hecho en ninguno paso de 500k

Aquí también hay algo raro. El hardware es el mismo.

La alegría de conseguir conectarme me hizo obviar que todo iba bastante más lento que de costumbre. De hecho, cuando estoy descargando algo (con el gestor de actualizaciones, por ejemplo) ya la navegación por internet se hace casi imposible (por lenta).

Esto se está convirtiendo en un caso para Sir Linux Holmes. [optimist mode on] Cuestión de ver el lado divertido y aceptar el reto. Esto se va a solucionar si o si [optimist mode off]

Saludos,

-Sof-

---

### Post by sofocles92 on 2008-10-06
Si, tengo un adaptador Belkin conectado al usb que es el que envía y recibe la señal al modem.

lsub:

```
root@sofocles-desktop:~# lsusb
Bus 008 Device 004: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 03f0:c302 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by luks911 on 2008-10-06
Tal vez tendríamos que haber empezado por aquí :P Revisá [este hilo]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=632750") aparentemente tiene idas y vueltas, pero finalmente lograron solucionarlo. Son sólo dos páginas, aunque en inglés. Es alguien con el mismo dispositivo que empezó con un problema similar o igual: veía redes pero no se conectaba.

---

### Post by sofocles92 on 2008-10-06
Todavía me pierdo bastante en el manejo de Ubuntu. Si, parece similar el caso. Tengo que leerlo todo despacito y entenderlo bien lo que me llevará un poco de tiempo. Creo que el resumen del procedimiento es este ¿no?:

Instalar ndiswrapper y ndisgtk. Usar ndisgtk para remover el driver activo (que debería ser rt2500usb) para luego instalar el rt2500usb.inf desde el CD del Belkin.

Luego hay que editar /etc/modules

Lo que se puede hacer con el comando

nano /etc/modules

Y añadir "ndiswrapper"

Para que se cargue al inicio y luego hacer modprobe ndiswrapper para activar el wireless en la sesión actual. (Para lo que imagino se podrá hacer un script que lo haga automáticamente y no estar abriendo la terminal cada vez que se inicia).

**Otra posible solución que se me ocurre:** cambiar el adaptador Belkin por otro que no de problemas.

Lo que pasa es que aún tengo que estudiar como se instala nuevo hardware y los drivers en Ubuntu. Pero supongo que no es difícil.

Me tomará algunos días tener algo de experiencia en estas cosas.

Te iré contando lo que vaya haciendo.

Pd.- Purgué el Network-Manager. Eliminó algún archivo. Entonces haciendo /etc/init.d/networking restart ya no se conectaba. Así que puse los datos para conexión por DHCP en el "interfaces" y sí funcionaba. Ahora es independiente de Wicd porque salí de la aplicación y el restart funcionaba. Sigue lenta la conexión. Igual es por lo del adaptador.

---

### Post by luks911 on 2008-10-06
Ufff, acabo de leerlo... mi inglés todavía no es tan bueno como debería. Sí, es tal cual cómo lo decís. Sólo dos aclaraciones pequeñas, para cargar el módulo en la sesión actual al final del proceso el comando debe ir con sudo delante porque tiene que ser ejecutado como root, o sea
```
sudo modprobe ndiswrapper 
```
Y segundo: luego no hace falta script, una vez que ponés ndiswrapper en el archivo modules, el módulo se carga en cada inicio.

Espero que funcione

---

### Post by sofocles92 on 2008-10-07
¡Hecho! He instalado el controlador de windows para el adaptador Belkin con ndiswrapper y FUNCIONA.

Se conecta automáticamente con Wicd y la velocidad de navegación es óptima.

Muchas gracias. Sin tu ayuda muy probablemente no lo hubiera conseguido. Busqué de todo menos lo del adaptador. Y, por el camino, en tres días he aprendido más de Linux que (seguro) con dos meses en una academia.

Es una cosa muy grande contar con comunidades así y gente dispuesta a ayudar desinteresadamente.

Un abrazo.

-Sof-

---

### Post by luks911 on 2008-10-07
Me alegro de que funcione. También aprendí, por ejemplo, que siempre hay que empezar revisando que el dispositivo esté bien instalado y con los controladores correctos, jaja :lolflag:

Otro abrazo

---

