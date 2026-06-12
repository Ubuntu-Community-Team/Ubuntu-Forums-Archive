---
title: "[SOLVED] MLDonkey: ¿como hacerlo funcionar?"
date: 2008-12-24
forum: Software
---

### Post by andy_91 on 2008-12-24
hola a todos, instale mldonkey-server (mlnet) y sancho-gui. Hasta ahi todo barbaro, pero cuando le doy a un archivo para descargarlo se me queda ahi y no se descarga.

lo mismo me pasaba en windows con el emule, por eso nunca use amule ni esos por que no se como se activan para descargar.

antes usaba shareaza y se conectaba solo a la red edonkey

otra cosa como le agrego mas redes??? es que solo me figura la donkey

desde ya gracias

---

### Post by Mauro22 on 2008-12-25
Te conectas a traves de un router?


Si es asi, existe la posibilidad de tener que abrir los puertos para que se enlace la conexion. Al menos el emule lo pide.


Tambien hay ISP que restrigen el uso de esos puertos.

---

### Post by andy_91 on 2008-12-25
a ok y como lo hago, conm shareza no mme lo pedia :confused:

---

### Post by Mauro22 on 2008-12-25
depende del router...


Tenes que entrar a la web del router con el navegador y "forwardear" (seria como abrir, pero se le llama forwarding) los puertos que necesitas a tu ip

---

### Post by luks911 on 2008-12-25
> **andy_91 said:**
> hola a todos, instale mldonkey-server (mlnet) y sancho-gui. Hasta ahi todo barbaro, pero cuando le doy a un archivo para descargarlo se me queda ahi y no se descarga.

lo mismo me pasaba en windows con el emule, por eso nunca use amule ni esos por que no se como se activan para descargar.

antes usaba shareaza y se conectaba solo a la red edonkey

otra cosa como le agrego mas redes??? es que solo me figura la donkey

desde ya gracias

¿Vos decís que clickeas en un link ed2k y no se agrega? Si eso acá[0] hay una guía que usé para amule, desconozco si sirve para mldonkey. Seguramente también se puede copiar el enlace y pegar en algún lado (digo algún lado porque no conzco mldonkey).
te paso tabién un par de links sobre cómo conectar aMule con buenos servidores[1] y a la red Kademlia[2]. Sí, ya sé que son para aMule, pero te pueden servir los datos o capaz que podés encontrar la forma de adaptarlo. El amule me funcionó muy bien con eso.

[0] [http://www.gubuntu.es/2008/06/19/amule-hardy-firefox-3-y-los-enlaces-e2k-%C2%A1por-fin-solucionado-el-problema/](http://www.gubuntu.es/2008/06/19/amule-hardy-firefox-3-y-los-enlaces-e2k-%C2%A1por-fin-solucionado-el-problema/)
[1] [http://p2p.technoburger.net/emule-server](http://p2p.technoburger.net/emule-server)
[2] [http://p2p.technoburger.net/kad-network](http://p2p.technoburger.net/kad-network)

---

### Post by andy_91 on 2008-12-25
que enlaces??? yo solo lo uso para buscar musica y descargarla.

basucamente es el programa que solo se usarlo haciendo clic, por que de redes no me entra ni el nombre

por entrar al router te referis a eso que pones la ip en el firefox y te sale una especie de pagina web :confused: por que si es eso ya lo intente y no pude entrar

---

### Post by luks911 on 2008-12-25
> **andy_91 said:**
> que enlaces??? yo solo lo uso para buscar musica y descargarla.
Ah, me refería a links que hay en foros/páginas y que al clikear te agregan una descarga al programa. Por ejemplo, en un foro encontrás el disco XX con un link ed2k lo clikeas o lo copias y pegás donde corresponde y comenzás a bajarlo con el programa P2P.

Te sigo recomendando los links que te pasé para usar buenos servidores.

> **andy_91 said:**
> por entrar al router te referis a eso que pones la ip en el firefox y te sale una especie de pagina web :confused: por que si es eso ya lo intente y no pude entrar

Esto no lo dije yo pero sí, entiendo que Mauro22 se refiere a eso. ¿Qué router tenés y cómo trataste de ingresar a la configuración? En el mío, por ejemplo, entro a [http://192.168.1.1](http://192.168.1.1), pero eso, igual que el usuario y la contraseña para ingresar puede variar según marca y modelo.

---

### Post by andy_91 on 2008-12-25
si el mio es igual que el que tenes vos (me refiero a la direccion para entrar, pero no pero en lugar de entrar se queda cargando), voy a ver esa webs por lo de los servidores tal vez funcione :p

****************EDIT***************

nada que ver la interface :( mala suerte para mi

---

### Post by luks911 on 2008-12-25
> **andy_91 said:**
> si el mio es igual que el que tenes vos (me refiero a la direccion para entrar, pero no pero en lugar de entrar se queda cargando), voy a ver esa webs por lo de los servidores tal vez funcione :p

****************EDIT***************

nada que ver la interface :( mala suerte para mi

De todos modos, ¿qué router es (marca y modelo)? Tal vez también se pueda entrar por telnet, en una terminal
```
telnet 192.168.1.1
```

---

### Post by andy_91 on 2008-12-25
el modem es un zyxel p-600 series

---

### Post by luks911 on 2008-12-25
> **andy_91 said:**
> el modem es un zyxel p-600 series

Joder, tenemos el mismo router o uno de la mima línea. Es raro que no quiera entrar al configurador web. En una terminal ejecutá route y fijate que ip te devuelve en la columna "pasarela", esa tiene que ser la del router, o sea la puerta de enlace o gateway.

---

### Post by andy_91 on 2008-12-25
> **luks911 said:**
> Joder, tenemos el mismo router o uno de la mima línea. Es raro que no quiera entrar al configurador web. En una terminal ejecutá route y fijate que ip te devuelve en la columna "pasarela", esa tiene que ser la del router, o sea la puerta de enlace o gateway.
me devuelve dos * una abajo del otro :confused:

---

### Post by Hei Ku on 2008-12-25
postea el resultado de ifconfig.

---

### Post by luks911 on 2008-12-25
> **andy_91 said:**
> me devuelve dos * una abajo del otro :confused:

> **Hei Ku said:**
> postea el resultado de ifconfig.

Y el de route también ya que estás. A mí me devuelve 3 filas, las primeras 2 con * y la tercera tarda unos segundos más en aparecer, es donde aparece el router (por si sirve el dato).

---

### Post by andy_91 on 2008-12-25
[QUOTE=iconfig]eth0      Link encap:Ethernet  direcciónHW 00:01:6c:d3:d1:8c  
          dirección inet6: fe80::201:6cff:fed3:d18c/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:165739 (161.8 KB)  TX bytes:29374 (28.6 KB)
          Interrupción:16 Dirección base: 0xe800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1234 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:61700 (60.2 KB)  TX bytes:61700 (60.2 KB)

ppp0      Link encap: Protocolo punto a punto  
          inet dirección:201.255.120.65  P-t-P:200.63.148.121  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:158601 (154.8 KB)  TX bytes:22277 (21.7 KB)[/QUOTE]

 no sale ninguna fila mas me tira el andy@ubuntu-desktop:~$

---

### Post by Hei Ku on 2008-12-26
Estas conectado por VPN a otra red? 
Porque aparece una red punto-a-punto que no debería estar en condiciones normales.

---

### Post by luks911 on 2008-12-26
¿O tenés el router en modo bridge (vos hacés que se conecte)?

---

### Post by andy_91 on 2008-12-26
si yo pongo al usuario y la contraseña, para que entre con el pppoeconf

---

### Post by luks911 on 2008-12-26
> **andy_91 said:**
> si yo pongo al usuario y la contraseña, para que entre con el pppoeconf

Ah, ok, está en modo bridge. Por un lado, no sé si es eso lo que causa que no puedas entrar al configurador web (no lo sé de ignorante que soy), pero acá[0] hay un instructivo de Telefónica para ponerlo en modo router, con eso seguro te olvidás de tener que conectarlo vos cada vez (fijate que si tenés Telecomo los datos de VPI y VCI hay que cambiarlos por 0 y 33, respectivamente). En el instructivo empieza hablando de Win, pero hacés lo mismo en una terminal y ya.
Por otro lado, capaz que antes de hacer eso querés verificar si es en efecto un problema de puertos cerrados. Debe haber más opciones pero se me ocurre usar algúna scanner que haya en la web[1] y acá[2] un tutoria para hacerlo con nmap. La lista que usa Mdonkey, acá[3].

[0] [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)
[1] [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)
[2] [http://linuteca.com/escanear-puertos-con-nmap/](http://linuteca.com/escanear-puertos-con-nmap/)
[3] [http://www.guia-ubuntu.org/index.php?title=MLDonkey#Puertos](http://www.guia-ubuntu.org/index.php?title=MLDonkey#Puertos)

---

### Post by andy_91 on 2008-12-27
andy@ubuntu-desktop:~$ telnet 192.168.1.1
Trying 192.168.1.1...

eso me duvuelve el terminal y se queda ahi, es lo mismo que ,me pasa con el firefox y el kazehakase

---

### Post by luks911 on 2008-12-27
:confused: Una vez que tuve que reconfigurarlo me hacía eso pero sí pude entrar por el telnet enchufándolo en una máquina con Win, ni idea de por qué. Y lo peor es que todavía no sabemos si es efectivamente un problema con los puertos.

---

### Post by andy_91 on 2008-12-27
ni idea, y maquina con win no tengo

---

### Post by andy_91 on 2008-12-27
ya desinstale mldonkey me rendi XD ahora voy a buscar algun otro programa que funcione

************edit*************

actualmente usando frostwire

---

