---
title: "Problemas para conectarme a internet"
date: 2011-06-06
forum: Software
---

### Post by marcelo_bur on 2011-06-06
Hola. Desde hace un tiempo tengo problemas para conectarme a internet con Ubuntu y, en los últimos días, se volvió definitivamente imposible. Como he comentado en alguna ocasión estuve usando ubuntu "instalado dentro de Windows", por mucho tiempo sin ningún problema, aunque de vez en cuando despues de una actualización desparecía el grub y lo reinstalaba. Pero es la primer vez que tengo problemas con la conección a internet, la cual funciona en Windows y, por otra parte, compare los datos de la conección en ambos sistemas y son idénticos. 
De todas formas, y como ya me sugirieron que lo mejor es instalar Ubuntu en una partición aparte, opté por esto y hace un rato apenas terminé de instalar Ubuntu 10.04 como se debe, en una partición dedicada del disco. Mientras se instalaba no hubo ningún problema, descargo todo lo necesario desde la red y todo salió muy bien.
Cuando inicio por primera vez noto que había olvidado configurar como idioma el Español y, si bien que esté en inglés no me causa mayor molestia, me dispuse a cambiar el lenguaje, para lo cual debía descargarlo desde la red. Y, oh sorpresa, veo que no pasa nada.... Abro el navegador, por primera vez, trato de ver una página, y nada.... el mismo problema.
Paso a Windows y la conección funciona, vuelvo a Ubuntu, y aunque segun el router y segun el Network Manager todo esta funcionando, nada me abre y me tira error 105, es más, parece como que luego de intentar conectarme desde Ubuntu se bloquease todo, las otras computadoras pierden tambien la coneccion y en ocasiones es incluso necesario reiniciare el modem para volver a tener conección en todas las pc. En la mia en Windows, pero, la más curioso, es que la que usa mi hija, con Ubuntu 8.04, solo tiene problemas cuando yo de alguna forma **"mato"** la conección al intentar usar mi Ubuntu 10.04.
Estoy más perdido que turco en la neblina, en la semana voy a ir a charlar este asunto con el técinico que se ocupa de mis computadoras, a ver que opina, si puede ser el router o que diablos.
Entretanto si alguien tiene alguna idea, sugerencia, luckyvenga, será muy bienvenida.
Saludos

---

### Post by marcelo_bur on 2011-06-06
PD:

Otro detalle que note cuando todavía se conectaba, aunque con problemas... Cuando la conección se cortaba, cada vez más seguido, todas la paginas comunes tiraban ERROR 105, sin embargo y para mi aún más misteriorso, si estaba subiendo algo a mi servidor o a Terabox, esto no se cortaba, seguia normalmente hasta terminar, eso si, luego no había forma de volver a conectar. Y lo mismo sucedía con el programa de mensajería instantanea, no era afectado en tanto no se lo cerrase pero, una ves cerrado, no era posible volver a conectarse.

Saludos

---

### Post by biale on 2011-06-06
> En la mia en Windows, pero, la más curioso, es que la que usa mi hija, con Ubuntu 8.04, solo tiene problemas cuando yo de alguna forma "mato" la conección al intentar usar mi Ubuntu 10.04.

Error por dirección de IP idéntica para ambas máquinas (duplicada)? Si fuera así cualquiera de las dos que apagues resuelve el problema.

---

### Post by marcelo_bur on 2011-06-06
Hola Biale. No creo que sea ese el problema, durante mucho tiempo todo funcionó bien en las mismas condiciones, y ahora también funciona bien cuando mi máquina corre con Windows y el de mi hija con Ubuntu 8.04, incluso otra hija mayor y que vive al lado de nuestra casa siempre usó su notebook con windows vista, y las tren andaban bien. 
No le encuentro una explicación, pensé en mal funcionamiento del router, pero en ese caso el problema no distinguiria entre sistemas operativos, o al menos eso creo. Por el mismo motivo tiendo a descartar problemas de mi ISP, Speedy. Alguien me comentó sobre problemas con las derivaciones a otros teléfonos, asi que compré cable nuevo y tire una conección directa desde la bajada de la calle al modem, y todo igual. También alguien me comentó que tenía problemas de cortes en Speedy y se lo solucionaron cambiandole el filtro de la terminal que alimenta el modem, pero tampoco me cierra, porque supongo que en ese caso la conección tendría problemas en cualquier sistema operativo. 
Sigo dando vueltas, buscando en la red, preguntando, pero no encuentro nada concreto.
Saludos

---

### Post by biale on 2011-06-06
Es muy facil de verificar: un ipconfig /all a Windows y un ifconfig a Linux. Lo primero es descartar un error de configuracion.

---

### Post by marcelo_bur on 2011-06-07
Hola Biale, yo ya había comparado parámetros mediante el modo gráfico y todo estaba igual en ambos sistemas operativos, ahora lo he hecho como tu dices

Ubuntu me dio información más detallada, pero la verdad es que se me escapa si allí puede haber algún problema:

Este es el ifconfig de Ubuntu 10.04 instalado ayer en una partición dedicada:

```
marcelo@marcelo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:97:93:2f:50  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fe93:2f50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1342 (1.3 KB)  TX bytes:11665 (11.6 KB)
          Interrupt:31 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

marcelo@marcelo-desktop:~$ 
```

Y este es el resultado del ipconfig en Windows XP (no se puede copiar y pegar, asi que tome una captura de pantalla)

Espero que los que saben encuentren algo en esto. Yo hoy, en un acto que puede clasificarse ya de desesperado, cambié el cable de red, esperando un milagro, pero está visto que los milagros o bien no existen o son extremadamente escasos...

---

### Post by marcelo_bur on 2011-06-07
Creo que la imagen anterior del ipconfig/all no se lee bien, asi que aisle y aumente lo que importa del screenshot

Lo que no entiendo es eso de la "concesión", claro que nunca había tirado estos comandos en Windows, en realidad solo supe de su existencia y aprendí a usar algunos desde que comencé a utilizar Ubuntu...

---

### Post by guillermolisi on 2011-06-07
Las dos maquinas, la que corre Windows y la que corre Ubuntu, tienen la misma IP, 192.168.1.102.
Si ambas estan funcionando a la vez, habra problemas en la red.

Aunque no se usen en forma simultanea, lo aconsejable es que cada maquina tenga su propia IP, entendiendo por maquina el mismo harware pero otro sistema operativo o distintos hardware y SO.

---

### Post by marcelo_bur on 2011-06-07
Hola Guillermo.
No se trata de dos máquinas distintas, sino de la misma máquina. Anoche hice el Screenshot del ipconfig/al en Windows, donde la conección anda perfectamente,l y que es la que uso en este momento.
Para no generarle problemas a la máquina de mi hija, que estaba usando la suya con Ubuntu 8.04 sin ningún problema, opté por esperar hasta hoy por la mañana temprano para abrir Ubuntu y hacer un ifconfig. Además debo agregar que esta mañana, al hacerlo, mi hija dormía y su máquina estaba apagada, sin embargo no me pude conectar.
Esta mañana llevé la máquina a lo del técnico que siempre me ayuda con estas cosas, para descartar problemas en el hardware de la maquina y problemas en mi conección. El uso una antena inalambrica USB para conectase a su modem. Inició con windows y todo anduvo a la perfeccion, solo necesito instalar los drivers, y la máquina navegó sin problemas. Luego pasamos a Ubuntu, reconoció automáticamente el dispositivo inalambrico y con un par de clics se conectó, sin necesidad de instalar ningún driver. Pero el resultado fue el mismo que en mi casa, no abre las páginas. Lo cual según yo veo, y según la impresión del técnico, no implica que no esté conectada a internet, el servidor reconoce la máquina, pero es incapaz de abrir una página, todo indica que la esta versión de Ubuntu, la 10.04.2 viene con algún problema de configuración. Ahora dudo entre cambiar de 10.04 a 11.04 o bien retroceder a la 8.04, a ver que pasa. Con el técnico se reviso el hardware de mi máquina y todo funciona bien y está en condiciones, el problema es de software y especificamente en Ubuntu. No puedo descargar actualizaciones por la simple razón de que no tengo acceso a internet y, si existe otro modo de hacerlo, lo desconozco.
Así que, por el momento y aunque me siento muy raro luego de usar Ubuntu por dos años, no me queda otra que sufrir nuevamente con Windows XP, no olvidar hacer un scaneo completo de la máquina con frecuencia con el antivirus y todas esas delicias con que Windows nos obsequia.
Sigo leyendo y buscando, algo encontré donde en una situación similar parece que tenía algo que ver que no se actualizaba la dirección MAC, pero el post no explica muy bien como lo solucionaron por lo que no me sirve de gran cosa, salvo para ahondar mi busqueda por ese lado.
Saludos

---

### Post by marcelo_bur on 2011-06-07
> **guillermolisi said:**
> Las dos maquinas, la que corre Windows y la que corre Ubuntu, tienen la misma IP, 192.168.1.102.
Si ambas estan funcionando a la vez, habra problemas en la red.

Aunque no se usen en forma simultanea, lo aconsejable es que cada maquina tenga su propia IP, entendiendo por maquina el mismo harware pero otro sistema operativo o distintos hardware y SO.


Y me olvidaba... no tengo idea de como se hace para asignar a cada sistema operativo o maquina distinta una IP diferente.

Saludos

---

### Post by biale on 2011-06-07
Bien, tu hija usa Hardy, no debería estar usando la misma dirección IP. O sea que la salida del comando ifconfig en esa máquina NO debe contener algo como "... inet addr:192.168.1.102 ..." 

Conviene postear la salida del comando ifconfig de la máquina de tu hija y que sabemos que funciona. Tambien los contenidos del archivo  
"/etc/resolv.conf" y ya que estamos del comando "sudo route -n"

Para la maquina Ubuntu Lucid, igualmente nos faltan los contenidos de "/etc/resolv.conf" y del comando "sudo route -n".

De acuerdo con el ipconfig de Windows observo que el router esta asignando dos veces su propia direccion 192.168.1.1 como DNS y eso SI puede molestar.

Mientras tanto: asegurante de cortar la energia electrica [o sea apagar] del (1) todas las CPUs, (2) del modem de telefonica y del (3) router si son equipos separados. Luego los volves a conectar, primero telefonica, luego router (si existe) y por ultimo CPU/s.

---

### Post by fmsismo on 2011-06-07
Hola estas usando el network-manager (el entorno gráfico) o lo configuraste desde la consola ( /etc/network/interfaces)?

 proba de hacer ping a una ip en internet como 

< ping 8.8.8.8

Deberías obtener

> PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
> 64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=29.5 ms
> 64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=29.0 ms
> 64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=29.0 ms
> 64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=30.1 ms
> 64 bytes from 8.8.8.8: icmp_seq=5 ttl=57 time=29.4 ms
> 64 bytes from 8.8.8.8: icmp_seq=6 ttl=57 time=29.5 ms

Lo cancelas con ctrl+c

Si eso no anda proba hacer un ping al broadcast de tu red.

< ping -b 192.168.1.255

Y copianos que te devuelve

También ejecuta en la consola

< ip route show

Y copianos que te devuelve

Por último 

< cat /etc/resolv.conf

Y que te devuelve.

---

### Post by marcelo_bur on 2011-06-07
[B]"Bien, tu hija usa Hardy, no debería estar usando la misma dirección IP. O sea que la salida del comando ifconfig en esa máquina NO debe contener algo como "... inet addr:192.168.1.102 ..."

Conviene postear la salida del comando ifconfig de la máquina de tu hija y que sabemos que funciona. Tambien los contenidos del archivo
"/etc/resolv.conf" y ya que estamos del comando "sudo route -n"

Para la maquina Ubuntu Lucid, igualmente nos faltan los contenidos de "/etc/resolv.conf" y del comando "sudo route -n".

De acuerdo con el ipconfig de Windows observo que el router esta asignando dos veces su propia direccion 192.168.1.1 como DNS y eso SI puede molestar.

Mientras tanto: asegurante de cortar la energia electrica [o sea apagar] del (1) todas las CPUs, (2) del modem de telefonica y del (3) router si son equipos separados. Luego los volves a conectar, primero telefonica, luego router (si existe) y por ultimo CPU/s."[/B]

------------------------------------------------------------------------------------------

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

marcelo@natalia-desktop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:11:5b:9b:71:be  
          inet dirección:192.168.1.102  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::211:5bff:fe9b:71be/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1957 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1662 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          RX bytes:2468462 (2.3 MB)  TX bytes:166052 (162.1 KB)
          Interrupción:17 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          Paquetes RX:932 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:932 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          RX bytes:46600 (45.5 KB)  TX bytes:46600 (45.5 KB)

marcelo@natalia-desktop:~$ sudo route -n
[sudo] password for marcelo: 
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
marcelo@natalia-desktop:~$ 

---------------------------------------------------------------------------------------------

etc/resolv.conf:

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4693
#
### END INFO

search private


nameserver 192.168.1.1
nameserver 192.168.1.1
nameserver 200.63.155.185

-----------------------------------------------------------


En mi máquina, corriendo windows


Imagen al pie


--------------------------------------------------------------------

En mi máquina corriendo Ubuntu 10.04

marcelo@marcelo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:97:93:2f:50  
          inet addr:192.168.1.27  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fe93:2f50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1702 (1.7 KB)  TX bytes:21868 (21.8 KB)
          Interrupt:31 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

marcelo@marcelo-desktop:~$ sudo route -n
[sudo] password for marcelo: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
marcelo@marcelo-desktop:~$ 

---------------------------------------------------------------------------

etc/resolv.conf:

# Generated by NetworkManager
domain private
search private
nameserver 192.168.1.1
nameserver 200.63.155.185

-------------------------------------------------------------------------


**NOTAS:** La ip que aparece ahora la configuró el técnico manualmente en Windows, pero no se porque sigue siendo la misma en Ubuntu.
Fmsismo, lamentablemente olvidé hacer lo del ping porque ando apurado, todas las noches actualizo algunos datos en mi sitio.

Gracias por ayudarme en mi intento de sacar esto adelante, en verdad no me siento nada cómodo usando Windows.

Saludos

---

### Post by biale on 2011-06-07
La maquina Win marcelo-5e71935 se estaba cruzando con natalia en la direccion 192.168.1.102

Desde Lucid Ubuntu: Si haces...
"ping 8.8.8.8" y te responde entonces es casi seguro que el problema esta en los DNS

Editas el archivo: sudo /etc/resolv.conf
así

# Generated by NetworkManager
domain private
search private
# nameserver 192.168.1.1
nameserver 8.8.8.8
nameserver 200.63.155.185

Salvarlo y probar con FFox o lo que sea.

Nota: en este momento los dns de Speedy que tengo son 200.51.211.7 y
208.67.222.222 tambien se podría probar con esos valores.

---

### Post by marcelo_bur on 2011-06-08
Hola Biale, gracias por tus sugerencias, ya voy a intentarlo.
En el apuro olvidé adjuntar la imágen del ipconfig en windows cuando la estaba usando sin ningún problema y al mismo tiempo que la de mi hija corriendo Hardy.
La dejo ahora por si tuviese alguna importancia.
Saludos

---

### Post by marcelo_bur on 2011-06-08
Hola Biale. Inmediatamente hice lo que me sugeriste. El PING obtenía un 100% de resultados positivos sobre 20 envios, asi que me dispuse a modificar inmediatamente el archivo /etc/resolv.conf. Lo edite según tus instrucciones y abri Mozilla, y **¡¡¡¡ALELUYA!!!!!**, aqui estoy nuevamente desde mi Ubuntu. Ya que como es lo más lógico seguiré usando la nueva instalación en su partición dedicada, dejando de lado las "instalaciones dentro de Windows", solo me restan detalle, descargar dos o tres programas que usualmente utilizo, y pavadas similares.

:guitar: ](*,)


Estoy muy agradecido a todos los que me ayudaron a resolver este problema, que me tuvo a maltraer durante más de una semana, llegando incluso a afectar mi actividad laboral, ya que soy algo obsesivo cuando no consigo solucionar un problema.
Esto demuestra una vez más cuan útil es este foro y cuan solidaria es la comunidad Ubuntu.
Nuevamente

[CENTER][SIZE=4][COLOR=Red][B]¡¡¡¡MUCHAS GRACIAS!!!!!
[/B][/COLOR][/SIZE][/CENTER]

---

### Post by biale on 2011-06-08
Era un problema con los DNS. No se se donde salió la direccion 192.168.1.1 como nameserver. También hubo en algún momento dirección duplicada de IP. 

En el ultimo pantallazo aparecen los DNS que usa Windows. 200.51.211.7 y 200.51.212.7

Por las dudas habría que revisar las configuraciones del router y del Network Manager para eth0 en Lucid.

---

### Post by marcelo_bur on 2011-06-08
Hola Biale. 192.168.1.1 es la dirección del router. Las direcciones que  aparecen ahora en los DNS en Windows los configuró manualmente el  técnico, pensando que quizás eso solucionase el problema.
IPv4 en Network Manager esta configurado como AUTOMATICO (DHCP)
Y estas son las configuraciones del router. Miralas y decime si ves algo raro, pero por suerte todo está funcionando perfectamente.
Saludos

---

### Post by marcelo_bur on 2011-06-09
Hola. Un nuevo día, una nueva sorpresa....
Hace apenas unos minutos que encendí mi pc, entro confiado y tranquilo a Ubuntu y, ZAZZZ!!!, de nuevo el mismo problema, lo cual me dejó muy confundido. Lo primero que se me ocurrió hacer es verificar el archvo /etc/resolv.conf y veo que nuevamente estaba con los valores de ayer, lo cual me lleva a la conclusión lógica de que este archivo se genera cada vez que enciendo la pc, cosa que no sabía. Edité el archivo según las instrucciones que me dejó ayer Biale y la máquina funciona nuevamente bien.
Ahora el tema, cuya solución si bien tengo idea por donde buscarla, en verdad no se cual es, es evitar que la máquina genere esos datos que no me permiten navegar al encenderla. Supongo que tendría que modificar algo en el Network Manager, tal vez dejar una configuración manual, en lugar de la automática, pero no tengo idea de los valores que debo colocar.
En mi mensaje anterior dejé pantallazos del Router, hoy tire el comando ip route show y esto es lo que me tiró:

```
marcelo@marcelo-desktop:~$ ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.101  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 
marcelo@marcelo-desktop:~$ 

```

Espero que puedan orientarme para que el problema desaparezca definitavamente sin tener que modificar todos los dias el archivo resolv.conf
Desde ya muchas gracias.
Saludos

---

### Post by biale on 2011-06-09
Por eso había que revisar la configuración del router...

Primero guarda los pantallazos del router como referencia. Conviene cambiar en el router los "Primary DNS IP" y "Secondary DNS IP". Comenza con los valores que uso el técnico: 200.51.211.7 y 200.51.212.7 

Y luego los mas facil es reiniciar Ubuntu. Si por cualquier causa no funciona volve los valores atras.

Tambien se podrían usar los valores de Google, pero pueden ser mas ineficientes: 8.8.8.8 y 8.8.4.4

Luego de reiniciar a Ubuntu y en el applet de Network Manager, "Informacion de la conexion" te dice que valores tomó. 

OT/ Observo que el router tiene configurada seguridad "WEP" en algun momento habria que pensar en cambiarla a WPA - WPA/2  /OT

---

### Post by guillermolisi on 2011-06-09
Marcelo

Edita el archivo /etc/dhcp/dhclient.conf (usando sudo y tu editor de archivos/texto preferido).

Busca una linea como la del ejemplo (sin considerar las direcciones IP que figuran en ella):
```
#prepend domain-name-servers 208.67.222.222,208.67.220.220;
``` borra el signo # (descomentas la linea) y reemplaza las direcciones IP por las de los servidores DNS que queres utilizar, respetando espacios y puntuaciones).

Proba de navegar y si aun asi no funciona, reinicia el servicio de red que deberia salir andando al toque.

Esa instruccion hace que se antepongan esas direcciones IP a las que tu ISP o router te envia, asi no tenes que estar redefiniendo el contenido del archivo resolv.conf con cada reinicio.

Igualmente creo que tambien habria que ajustar algunas cosas en el router, como bien indica Biale.

---

### Post by marcelo_bur on 2011-06-09
Gracias por orientarme, en esto momento se esta ejecutando el gestor de actualizaciones (por primera vez, asi que hay mucho por actualizar...), por lo que no puedo hacer nada, pero voy probar lo que dicen más tarde y luego publico los resultados.
Saludos y gracias

---

### Post by dozycat on 2011-06-09
Otra opcion es asignar las ip en un perfil de red inalambrico.
Boton secundario sobre la interface de red ( parte superior derecha) y escogeeditar conexiones.
Escoge el tab de inalambrica. Y puedes añadir una red  inalambrica o mas facil editas la existente que se conecta a tu red inalambrica y le asignas valores fijos en el tab de ipv4.

Yo lo utilizo para acceder diferentes pools de datos usando la misma red inalambrica y esta tiene dhcp server.

---

### Post by marcelo_bur on 2011-06-09
Parece que el problema quedó resuelto definitivamente.
Dozycat, te agradezco tu ayuda, solo que mi pc está conectada al router por cable, solo mi hija mayor usa la opción inalambrica, porque vive en la casa lindante.
La solución fue editar el archivo /etc/dhcp3/dhclient.conf tal como lo sugirió Guillermo y utilizando los DNS que propuso Biale, los que el técnico configuro en Windows. Una vez hecho esto reinicié, que además debía hacerlo para terminar de instalar las actualizaciones, y por suerte la máquina toma los DNS del archivo modificado y navega bien.
En cuanto a lo de la seguridad WEP luego lo hago, porque me gustaría saber cuales son las diferencias entre una y otra, asi que voy a leer algo antes.
Nuevamente gracias a todos.
Saludos

---

### Post by dozycat on 2011-06-09
Lo que te dije de la red inalambrica tambien se aplica a la red de ethernet, yo tengo diferentes perfiles por ejemplo la casa, dhcp, la oficina y demas. Lo bueno es que solo tengo que conectar el cable y selecciono y puedo cambiar de 192.168.0.102 a 172.30.0.102 o dhcp. Con solo un clik no tengo que editar ningun archivo.

---

