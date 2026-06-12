---
title: "Fibertel en ubuntu, problema"
date: 2008-10-14
forum: Software
---

### Post by gonzalo4018 on 2008-10-14
Hola, no puedo hacer funcionar internet en Ubuntu!

Busque miles de soluciones en internet y no hay nada :S. Saque la info desde XP, DNS, puertos, etc... y no va, a ver si me pueden ayudar, porque tengo que reiniciar la pc todo el dia :mad:

---

### Post by Hernán-Amaya on 2008-10-15
danos mas datos, que modem tenes? como conectas el modem a la pc?

---

### Post by nahuel_89p on 2008-10-15
Te cuento, yo tengo fibertel y ubuntu y siempre me anduvo perfectamente y automaticamente... bastaba con correr el livecd para navegar por internet sin problemas con el firefox. Mi conexion es la tipica del fiber, el cable coaxil al modem, y del modem un cable de red hasta la placa de red. Si usas USB no sabria decirte, porque puede que tengas qie instalar el software del modem, y es probable que no tengan drivers para linux. Bah, supongo, fijate de que marca es el modem, entra a la pagina oficial, y checkea por software.
De ultima, si tenes placa de red, abandona el cable usb y hace la conexion via cable red porque de este modo ubuntu te detecta la conexion automaticamente y no tenes que hacer nada para navegar. Asumo que estas con usb justamente por eso, de otro modo te funcionaria automaticamente.
La otra posibilidad es que no te detecte la placa de red.

---

### Post by gonzalo4018 on 2008-10-15
> **nahuel_89p said:**
> Te cuento, yo tengo fibertel y ubuntu y siempre me anduvo perfectamente y automaticamente... bastaba con correr el livecd para navegar por internet sin problemas con el firefox. Mi conexion es la tipica del fiber, el cable coaxil al modem, y del modem un cable de red hasta la placa de red. Si usas USB no sabria decirte, porque puede que tengas qie instalar el software del modem, y es probable que no tengan drivers para linux. Bah, supongo, fijate de que marca es el modem, entra a la pagina oficial, y checkea por software.
De ultima, si tenes placa de red, abandona el cable usb y hace la conexion via cable red porque de este modo ubuntu te detecta la conexion automaticamente y no tenes que hacer nada para navegar. Asumo que estas con usb justamente por eso, de otro modo te funcionaria automaticamente.
La otra posibilidad es que no te detecte la placa de red.


Uso la misma conexion que vos, no se cual sera el problema que no lo detecta, el modem es Webstar. 
al no andar, configure la red, entre a firefox, y como que quiso entrar una pagina, pero no pudo, tardo 1 o 2 minutos en aparecer lo de la conexion...


Les paso exactamente los datos que me aparece en Win XP

Dirección física: 00-1F-C6-B5-15-62
Dirección IP: 190.17.102.217
Máscara de subred: 255.255.255.0
Puerta de enlace predeterminada: 190.17.102.1
Servidor de DHCP: 172.20.2.12
Concesión obtenida: 15/10/2008 19:38:33
La concesión caduca: 16/10/2008 1:38:33
Servidores DNS: 200.49.130.29, 200.49.130.28, 200.49.130.34, 172.20.2.12
Servidor WINS: 


Todo esto lo pase a la parte de red de Ubuntu y no funciono.

---

### Post by jpmorelli on 2008-10-15
Gonzalo, yo tengo Fibertel y la conexión es fácil, pero no tenés que pasar todos los datos que lees de Win a Ubuntu porqu seguramente también estás asignando la IP como fija y poniendo la dirección que te asignó el DHCP, mientras que tenés que dejar que la conexión sea la que decide eso.
Más claro, andá a la configuración de red de Ubuntu y decile a la conexión de tu interfaz de red que haga todo automático( IP asignada por DHCP ), no deberías tener problemas.
Igualmente cualquier cosa podés postear un screen de como tenés la configuración para poder tener más datos.
No te preocupes que lo vas a sacar, todos aprendemos cada vez más.
Suerte !

---

### Post by gonzalo4018 on 2008-10-15
ok, gracias, ahora lo pruebo y te digo...
Sino reinstalo ubuntu, y hago lo que me decis.

---

### Post by eldragon on 2008-10-15
> **gonzalo4018 said:**
> ok, gracias, ahora lo pruebo y te digo...
Sino reinstalo ubuntu, y hago lo que me decis.

no deberia de ser necesario.

primero, fijate que tiene tu archivo /etc/network/interfaces

deberia decir algo asi:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

```

si tiene mas cosas (o menos). hace una copia de seguridad de ese archivo, y crea uno igualito a lo que puse.

despues, hace
```

$ sudo /etc/init.d/networking restart

```

para reinicar la red.

para poder ver que configuró la tarjeta de red. hace
```

$ ifconfig

```

eso solo te deberia de sobrar para tener internet con fibertel conectado por cable ethernet a tu tarj de red.

suerte.

---

### Post by gonzalo4018 on 2008-10-15
Bueno, recien intente con tu solucion Jmorelli, y nada tampoco:(, Gracias igual. Ahora intento con lo tuyo, Eldragon
Una solucion debe haber, o sino estoy haciendo algo mal, no puede ser que no tenga internet!!!:mad::mad::mad:

---

### Post by gonzalo4018 on 2008-10-15
> **eldragon said:**
> no deberia de ser necesario.

primero, fijate que tiene tu archivo /etc/network/interfaces

deberia decir algo asi:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

```

si tiene mas cosas (o menos). hace una copia de seguridad de ese archivo, y crea uno igualito a lo que puse.

despues, hace
```

$ sudo /etc/init.d/networking restart

```

para reinicar la red.

para poder ver que configuró la tarjeta de red. hace
```

$ ifconfig

```

eso solo te deberia de sobrar para tener internet con fibertel conectado por cable ethernet a tu tarj de red.

suerte.


No me funciono!

Esto esta bien
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

```


El problema lo tengo en el segundo paso:

```

$ sudo /etc/init.d/networking restart

```

empieza a cargar todo, y en el final me aparecen negaciones...
algo como

No recibed, o algo asi, si queres pongo una foto de como sale.

---

### Post by llove on 2008-10-16
hola probaste algo simple como reiniciar el modem despues de salir de xp y antes de que bootee ubuntu??? . suerte.

---

### Post by rojojuan on 2008-10-16
Iniciando con un cd live podés entrar?.
En Fibertel, con cualquier cd live entro sin problemas con ese modem.

---

### Post by gonzalo4018 on 2008-10-16
> **llove said:**
> hola probaste algo simple como reiniciar el modem despues de salir de xp y antes de que bootee ubuntu??? . suerte.

No, reiniciaba el modem ya adentro desde Ubuntu, ahora pruebo.

> **rojojuan said:**
> Iniciando con un cd live podés entrar?.
En Fibertel, con cualquier cd live entro sin problemas con ese modem.

No probe, ahora me fijo y te digo que pasa.

---

### Post by fmsismo on 2008-10-16
Tenes luz de link cuando enchufas la placa.
[INDENT]< sudo ethtool eth0[/INDENT]
[INDENT][INDENT]>	Supported ports: [ TP ]
>	Supported link modes:   10baseT/Half 10baseT/Full 
>	                        100baseT/Half 100baseT/Full 
>	                        1000baseT/Half 1000baseT/Full 
>	Supports auto-negotiation: Yes
>	Advertised link modes:  10baseT/Half 10baseT/Full 
>	                        100baseT/Half 100baseT/Full 
>	                        1000baseT/Half 1000baseT/Full 
>	Advertised auto-negotiation: Yes
>	Speed: 100Mb/s
>	Duplex: Full
>	Port: Twisted Pair
>	PHYAD: 1
>	Transceiver: internal
>	Auto-negotiation: on
>	Supports Wake-on: g
>	Wake-on: g
>	Current message level: 0x000000ff (255)
>	**Link detected: yes**
[/INDENT][/INDENT]

La placa te la reconoce ubuntu?
[INDENT]>< ifconfig -a[/INDENT]
Te debería listar las placas que tiene tu equipo?
Es la misma placa que estas usando para el windows y linux?  Porque el modem de fibertel si le cambias la placa sin reinicarlo no anda.

Cuando lo enchufas que ip te da?
Probaste una ves que lo tenes enchufado hacer
[INDENT]< sudo /etc/init.d/networking restart[/INDENT]

Saludos

[I]Convenciones:
'<' comando a ingresar por consola
'>' output de la consola[/I]

---

### Post by gonzalo4018 on 2008-10-16
> **fmsismo said:**
> Tenes luz de link cuando enchufas la placa.
[INDENT]< sudo ethtool eth0[/INDENT]
[INDENT][INDENT]>	Supported ports: [ TP ]
>	Supported link modes:   10baseT/Half 10baseT/Full 
>	                        100baseT/Half 100baseT/Full 
>	                        1000baseT/Half 1000baseT/Full 
>	Supports auto-negotiation: Yes
>	Advertised link modes:  10baseT/Half 10baseT/Full 
>	                        100baseT/Half 100baseT/Full 
>	                        1000baseT/Half 1000baseT/Full 
>	Advertised auto-negotiation: Yes
>	Speed: 100Mb/s
>	Duplex: Full
>	Port: Twisted Pair
>	PHYAD: 1
>	Transceiver: internal
>	Auto-negotiation: on
>	Supports Wake-on: g
>	Wake-on: g
>	Current message level: 0x000000ff (255)
>	**Link detected: yes**
[/INDENT][/INDENT]

La placa te la reconoce ubuntu?
[INDENT]>< ifconfig -a[/INDENT]
Te debería listar las placas que tiene tu equipo?
Es la misma placa que estas usando para el windows y linux?  Porque el modem de fibertel si le cambias la placa sin reinicarlo no anda.

Cuando lo enchufas que ip te da?
Probaste una ves que lo tenes enchufado hacer
[INDENT]< sudo /etc/init.d/networking restart[/INDENT]

Saludos

[I]Convenciones:
'<' comando a ingresar por consola
'>' output de la consola[/I]


No lo detecta...




Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
	Link detected: NO




--------------------------------------------------------






eth0      Link encap:Ethernet  direcciónHW 00:1f:c6:b5:15:62  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:13647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:819948 (800.7 KB)  TX bytes:0 (0.0 B)
          Interrupción:20 Dirección base: 0xdead 

eth0:avahi Link encap:Ethernet  direcciónHW 00:1f:c6:b5:15:62  
          inet dirección:169.254.6.9  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Interrupción:20 Dirección base: 0xdead 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1431 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:72020 (70.3 KB)  TX bytes:72020 (70.3 KB)




[INDENT]< sudo /etc/init.d/networking restart[/INDENT]
ya probe y tampoco. :S

---

### Post by fmsismo on 2008-10-16
Bueno, ya sabemos porque no anda!

Fijate que pasa si llevas a tu placa a 10mb.  Hay algunos modems que no autonegocian bien o solo funcionan a 10mb.

Proba ejecutando en la consola:

< sudo ethtool -s eth0 speed 10 duplex full autoneg off

Ahí apagas la autonegociación forzas la placa a que trabaja a 10mb/s fullduplex.  En una de esas levanta (me paso eso mismo que a vos con un openbsd y fibertel hace unos años).

Saludos

---

### Post by chalito on 2008-10-16
De hecho la autonegociacion en ethernet suele andar para el ogt en varias placas (y no solo en ubuntu, me paso en un laburo instalando una red de win2k con switches 3com de los caritos), siempre es mejor apagarla. A veces no agarra incluso aunque el link sea perfectamente bueno. Lo recomendable es, como postearon mas arriba, desactivarla y probar primero en 10mbps, full duplex, y si anda bien, ya sabes que al menos con eso a 10mbps andas. 
Después proba ponerlo a 100mbps, full duplex. Lo mas probable es que ande tambien, porque en general las implementaciones de autoneg hacen lo que se les canta y terminan andando para el traste, no porque el link sea malo.
saludos

---

### Post by gonzalo4018 on 2008-10-16
Probe con el live y tampoco, ni con reiniciar el modem cuando bootea el SO... ahora intento lo que ustedes me dicen...

---

### Post by gonzalo4018 on 2008-10-16
Nada. Voy a probar con Fedora a ver que pasa.
Gracias igual.

---

### Post by faktorqm on 2008-10-16
```
eth0 Link encap:Ethernet direcciónHW 00:1f:c6:b5:15:62 
ARRIBA DIFUSIÓN MULTICAST MTU:1500 Métrica:1
RX packets:13647 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000 
RX bytes:819948 (800.7 KB) TX bytes:0 (0.0 B)
Interrupción:20 Dirección base: 0xdead 

eth0:avahi Link encap:Ethernet direcciónHW 00:1f:c6:b5:15:62 
inet dirección:169.254.6.9 Difusión:169.254.255.255 Máscara:255.255.0.0
ARRIBA DIFUSIÓN MULTICAST MTU:1500 Métrica:1
Interrupción:20 Dirección base: 0xdead
```

Ahi no le esta diciendo que no tiene IP? Le pusiste IP como te recomendaron antes? Un amigo cada vez que se pasa a o desde gnu/linux a windows tiene que apagar el modem, y volverlo a prender (parece que hay un tema con la renovacion de la mac) y ahi le anda, de ninguna otra manera le anda. un misterio. Me parece muy muy raro que no te levante la placa de red. Salu2!

---

### Post by gonzalo4018 on 2008-10-16
> Ahi no le esta diciendo que no tiene IP? Le pusiste IP como te recomendaron antes? Un amigo cada vez que se pasa a o desde gnu/linux a windows tiene que apagar el modem, y volverlo a prender (parece que hay un tema con la renovacion de la mac) y ahi le anda, de ninguna otra manera le anda. un misterio. Me parece muy muy raro que no te levante la placa de red. Salu2!

La verdad ni idea.. es muy raro

---
---

una pregunta... cuando instale fedora... me va a aparecer el Grub para iniciar con Windows, no?

---

### Post by faktorqm on 2008-10-17
No sé, preguntá en el foro de Fedora ;)

---

### Post by fmsismo on 2008-10-17
Probaste en deshabilitar la autonegociación de la placa.  Es muy factible que con otra distro te pase lo mismo.

Si ya tenes el ubuntu instladado proba haciendo 

    sudo ethtool -s eth0 speed 10 duplex full autoneg off

(es un parametro que cuando reinicias se borra).

Si esto te funciona podemos configurar tu equipo para que quede fijo.

Abrazo

---

### Post by gonzalo4018 on 2008-10-17
ya habia probado y nada, intente otra vez y tampoco...

---

### Post by gonzalo4018 on 2008-10-18
Y si instalo la 7.10? podria solucionarse?

---

### Post by devoriana on 2008-10-20
> **gonzalo4018 said:**
> Hola, no puedo hacer funcionar internet en Ubuntu!

Busque miles de soluciones en internet y no hay nada :S. Saque la info desde XP, DNS, puertos, etc... y no va, a ver si me pueden ayudar, porque tengo que reiniciar la pc todo el dia :mad:

Hola Gonzalo! yo soy hipersuperextranovata en Ubuntu, cada día estoy más enamorada de este sistema, y tengo problemas para conectar mis compus en casa (ver mi Thread: "Conexion inalambrica entre dos PCs - por favor ayuda" de hace una semana), con el agravante de que una no es mía, es de mi mamá y no puedo sacarle windows XP porque si le meto mano a su PC creo que muere infartada....
En esa PC es donde está la conexión de fibertel a internet, y como hasta ahora no pude darle en la tecla a hacer la red inalámbrica con mi notebook (que tiene Ubuntu) opté por usar su conexión cuando ella no utiliza su PC (muy práctico, dirás, pero bueno, las ayudas en mi Thread son para expertos y yo no lo soy...).
Yo lo que hago cada vez que uso la conexión fiber es apagar el modem, sacar el cable de red de la PC y conectarlo a mi notebook apagada a la placa de red. cuando la enciendo reconoce automáticamente la conexión y navego de maravillas.
Tal vez esto sea un consejo de perogrullo y vos ya lo probaste sin éxito, pero espero te sea de utilidad.
Sorry por el "llanto" previo.
Devo

---

### Post by devoriana on 2008-10-20
> **gonzalo4018 said:**
> Y si instalo la 7.10? podria solucionarse?

ah! me olvidaba! tengo la útilma versión de Ubuntu (8.04).
saludos
Devo

---

### Post by Mtkr on 2008-10-21
Hola buenas, te comento, yo tengo telecentro que basicamente lo mismo, hace tiempo que queria instalar linux definitivamente, pero como nunca me andaban las conexiones a internet o era muy engorroso, para buscarlo, porque si bien hay muchos datos en internet primero tenes que conectarte.
Bueno lo que no me queda claro es vos tenes el moden en tu casa o te lo pasa internet tu vecino (via cable o wireless via router).
Yo que tengo muy poca experiencia en ubuntu me pude conectar sin dramas iniciando con el live cd y bueno tambien sin dramas ni siquiera configuraciones una vez instalado. Es mas un amigo trajo a casa su notebook con placa wireless y con el live cd tambien conecto.
Pregunta en Win la conexion te anda bien ?

---

### Post by eldragon on 2008-10-21
que tan cara es una tarj de red? yo compraria 1 y a otra cosa.

---

### Post by chalito on 2008-10-22
A todo esto, que modelo de placa de red es?

podrías pastear el output de lspci?

---

### Post by erdosain9 on 2008-10-23
Hola.  Mirá yo tengo Fibertel, puedo decirte que me funcionó perfecto desde el primer momento con ubuntu.

Dos cosas (yo lo tengo así y funciona):
si la conexión es directa deja la red en "modo itinerante"...
y la siguiente que involucra la anterior es que si tenés una máquina con windows y luego la apagas y le conectás el cable a una con ubuntu sin reiniciar el modem internet no funciona.  
Por ahí estás probando en windows y luego sin reiniciar el modem lo conectás a ubuntu... así a mí no me funciona.  Mi modem es webstar 2100 (si mal no recuerdo). (y Viceversa)
Así que acordate de reiniciar el modem cada vez que cambies de S.O.
saludos

---

### Post by vk-cdg on 2008-10-24
> **erdosain9 said:**
> ... si tenés una máquina con windows y luego la apagas y le conectás el cable a una con ubuntu sin reiniciar el modem internet no funciona.  
Por ahí estás probando en windows y luego sin reiniciar el modem lo conectás a ubuntu... así a mí no me funciona...

El problema no es que cambies de SO sino de PC, al cambiar de PC cambia la MAC (dirección física de la placa de red) y eso es lo que queda "grabado" en el modem, solo al reiniciarlo se vacía esa lista.

Yo tengo en mi PC windows y linux y puedo levantar uno u otro y no tengo que hacer nada de eso.

---

### Post by erdosain9 on 2008-10-24
ejmmmm, bueno, si... cada día se aprende algo nuevo (con mucha suerte!).  Bueno, en fin, la mac entonces...

---

### Post by Bruce M. on 2008-12-30
Hola gente,

Yo tengo Fibertel y tengo problemas.  Antes con "Flash" todo era perfecto. Cuando "Fibertel" comprado Flash", comencé a tener problemas. 

Cada día (a medio día hasta la noche) tengo que recomenzar mi máquina o la red varios veces.

```
bruloo@bruloo:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
bruloo@bruloo:~$
```

/etc/network/interfaces (ver: [Howto: Ethernet connection without a GUI]("http://cafelinux.org/xubuntuforums/index.php?PHPSESSID=7b7b4300a1733baa0f1b077b7ec6243e&topic=145.0"))
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

y /etc/resolv.conf
```
nameserver 200.49.130.20
nameserver 200.49.130.21
nameserver 200.49.130.32
nameserver 172.20.2.12
```
Algo está agregando la entrada #4, el número máximo de entradas es 3 por este archivo.

Creo que por eso yo tengo problemas, pero no puedo buscar una solución.

Que puedo hacer?

Gracias
Bruce
Xubuntu 8.10-64bit

---

