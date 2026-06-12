---
title: "Restringir conexiones de localhost a localhost"
date: 2008-10-13
forum: Software
---

### Post by jclevien on 2008-10-13
Hola que tal,

Estoy intentando restringir conexiones TCP que van de localhost a localhost.
Un usuario logueado no puede conectarse a cierto rango de puertos, solo a uno en particular que yo necesite.

He probado el Firestarter conectándome a Webmin desde localhost, pero igual me deja hacerlo!, aún no permitiendo ni la salida ni la entrada al puerto 10000!

Es como que el firewall no se sitúa antes de realizar la conexión, por favor, si alguien sabe como hacer esto, le agradeceré si me puede dar una mano.

Gracias.


Juan

---

### Post by jclevien on 2008-10-13
Probé el Guarddog, pero tampoco funcionó.



Juan

---

### Post by rober-mpp on 2008-10-13
localhost no es mas que un alias para 127.0.0.1, que representa la maquina en la que se esta trabajando. Esta representacion quiere decir que no se utiliza la placa de red para comunicarse con ella. El sistema operativo maneja automaticamente esta interfaz sin llegar a poner una sola trama ethernet en la placa de red. Con esto te quiero decir que, desconociendo como trabaja iptables, si este solo bloquea tramas/datagramas/paquetes que vienen/van a la placa de red, es posible que localhost nunca sea filtrado. Lo que podes probar para ver esto es, justamente, utilizar en lugar de localhost o 127.0.0.1, tu ip de red. Al poner tu ip de red se realiza toda la comunicacion con la placa de red y el lookup de tu mac en la red, etc,etc. En este caso la regla para iptables deberia ser algo como: "bloqueame todo lo que venga de mi ip al puerto tal". Sin embargo, estoy practicamente seguro de que se debe poder bloquear el localhost.

Suerte con eso :)

---

### Post by faktorqm on 2008-10-13
Hola, la unica duda que me queda es que si localhost no se refiere a la interfaz de loopback de la pc... por lo tanto, nunca va a buscar en la placa de red "real" los paquetes. Podrias probar de poner en el iptables: (no se manejar front-end's para iptables) 

```
iptables -A INPUT -i lo -j DROP
```
```
iptables -A OUTPUT -o lo -j DROP
```

Eso te bloquea todas las cosas entrates/salientes de tu loopback. Te aclaro que _NO SE_ que puede pasar luego de que ejecutes ese comando, pero si se te rompe todo, no te preocupes, alcanza con reniciar para volver a donde estabas antes. te digo esto por que ubuntu usa cosas sobre localhost, pero bueno, sera cuestion de probar... Salu2!

---

### Post by DanielSentinelli on 2008-10-13
-----BEGIN PGP SIGNED MESSAGE-----

Mmmm... en términos generales, inhibir la comunicación de localhost a
localhost no es una de las mejores ideas (a no ser que tengas bien
claro lo que estás haciendo), porque algunos programas usan este tipo
de conexiones como parte de su funcionamiento normal.

Para ver que programas están esperando recibir conexiones en localhost,
podés usar el comando:

$ sudo netstat -lntp | grep 127\.0\.0\.1

la última columna contiene el PID y nombre del programa.

Si hacés algo de lo que te sugiero a continuación, es altamente
probable que esos programas dejen de funcionar correctamente. Para las
siguientes indicaciones asumo que no hay ningún firewall funcionando y
que no has ingresado manualmente ninguna regla de netfilter/iptables.

Para hacer exactamente lo que estás pidiendo (esto es, bloquear las
conexiones TCP de localhost a localhost) tendrías que usar una orden
como:

$ sudo iptables -A INPUT -s 127.0.0.1 -d 127.0.0.1 -p tcp -j DROP

o

$ sudo iptables -A OUTPUT -s 127.0.0.1 -d 127.0.0.1 -p tcp -j DROP

Dado que la conexión "sale y vuelve a entrar" al propio equipo, la
primera regla la bloquearía cuando "entra" y la segunda cuando "sale".
Con una sola alcanza, si usaras las dos no es un problema.

Pero ojo, porque 127.0.0.1 no es la única dirección IP en que responde
la interface de loopback. Proba a hacer:

$ ping 127.12.34.56

(¿Sorprendido?)

Así que quizás lo mejor en tu caso sería bloquear directamente todo el
tráfico de la interface de loopback, independientemente de la dirección
de origen y/o destino que use, que es exactamente lo que hacen las
reglas que te sugirió faktorqm, solo que él bloquea todo tipo de
tráfico y no solo TCP. Para ser más selectivos (igual que antes, con
una sola alcanza):

$ sudo iptables -A INPUT -i lo -p tcp -j DROP

Ahora para permitir la conexión en un único port tendrías que agregar
antes que esta una regla específica que permita las conexiones. Por
ej, si quisiéramos permitir las conexiones al port 12345/tcp la regla
sería:

$ sudo iptables -A INPUT -i lo -p tcp --dport 12345 -j ACCEPT

En definitiva, las siguientes reglas combinadas y en este orden
producen este efecto sobre las conexiones entrantes a la interface de
loopback: se permiten al port 12345/tcp, se bloquean a todos los demás
ports tcp, se permiten todos los demás tipos de conexiones no tcp (udp,
icmp, arp, etc).

$ sudo iptables -A INPUT -i lo -p tcp --dport 12345 -j ACCEPT
$ sudo iptables -A INPUT -i lo -p tcp -j DROP
$ sudo iptables -A INPUT -i lo -j ACCEPT

Insisto en que es posible que esto altere el funcionamiento normal de
algunos programas, por lo que se requieren reglas adicionales
específicas para cada uno de ellos.

Estas reglas van a estar activas hasta que rebootees el equipo (o
purgues las reglas de netfilter/iptables). La forma de hacerlas
permanentes depende de si estas manejándote con scripts propios o usas
algún framework de firewall.

Asumiendo una instalación más o menos default de Ubuntu 8.04 desktop,
si estuvieras usando ufw tendrías que modificar el archivo

/etc/ufw/before.rules

reemplazando donde dice:

> # allow all on loopback
> -A ufw-before-input -i lo -j ACCEPT
> -A ufw-before-output -i lo -j ACCEPT

por, por ejemplo:

> # permitir 12345/tcp y todos los otros protocolos en loopback
> -A ufw-before-input -i lo -p tcp --dport 12345 -j ACCEPT
> -A ufw-before-input -i lo -p tcp -j DROP
> -A ufw-before-input -i lo -j ACCEPT
> -A ufw-before-output -i lo -j ACCEPT

Espero que todo esto te sirva para lo que estás intentando hacer.

-----BEGIN PGP SIGNATURE-----
Version: PGP 8.1

iQCVAwUBSPQEyjj/MqMeN4stAQHPQQQAqLeeyDjfkH/ehTMJZHd4H+HBlxURg7c7
LdcydHGCINMy2xHeasC1qt/7e6OBhHLrM+KhQ9ctnoGllP+F48D+Kp3O44A22up9
AdrNzopw4YGqp2zHOzlGI/8qbdUgu3RMy8qS4Vl3W4DN+oaJOGY5xK+c/7IcTvOf
oMo3AfGD304=
=HEbU
-----END PGP SIGNATURE-----

---

### Post by faktorqm on 2008-10-15
> **DanielSentinelli said:**
> 
Pero ojo, porque 127.0.0.1 no es la única dirección IP en que responde
la interface de loopback. Proba a hacer:

$ ping 127.12.34.56

(¿Sorprendido?)


Me había olvidado, la máscara de subred de la loopback es 255.0.0.0 entonces tenes muchas direcciones posibles.

```

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  [COLOR="Red"]Máscara:255.0.0.0[/COLOR]
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1874 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:94244 (92.0 KB)  TX bytes:94244 (92.0 KB)

```

Esto es lo que devuelve (una parte) el comando ifconfig. Aclaramos tus dudas? Salu2!

---

