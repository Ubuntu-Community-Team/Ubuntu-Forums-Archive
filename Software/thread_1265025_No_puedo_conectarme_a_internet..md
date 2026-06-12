---
title: "No puedo conectarme a internet."
date: 2009-09-12
forum: Software
---

### Post by el amo de la palabra on 2009-09-12
Hola, les pido paciencia que soy nuevo y no entiendo nada. Uso xp hace rato, habia oido de linux pero nunca lo habia conseguido, ahora lo descargue, lo instale y no puedo conectarme a internet. Estoy en mi trabajo en el campo, tengo una conexion satelital de la que usa el estado bonaerense, como habilito el proxi ó los puertos para conectarme, me enseñaron a hacerlo en xp, pero he probado de todo en ubuntu y no hay manera. Espero noticias, gracias.

---

### Post by gmunioz on 2009-09-13
Hola el a......:

Por favor pon datos.

Ejecuta en consola, Aplicaciones --> Accesorios --> Terminal

sudo lspci

sudo ifconfig

Y pega las salidas en el post

Además explica como te conectas, particularmente no

tenga idea a que te refieres con:

*conexion satelital de la que usa el estado bonaerense*

Respecto del proxy, pon los datos del mismo tambien.

---

### Post by el amo de la palabra on 2009-09-13
Hola Gabriel, muchas gracias por tu asistencia.

Hice lo que me pediste y salio todo esto:
administrador@ubuntu:~$ 

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
administrador@ubuntu:~$ sudo ispci 
[sudo] password for administrador:  
sudo: ispci: command not found 
administrador@ubuntu:~$ sudo ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:06:4f:7f:45:7a   
          inet dirección:10.142.100.49  Difusión:10.142.100.63  Máscara:255.255.255.192 
          dirección inet6: fe80::206:4fff:fe7f:457a/64 Alcance:Vínculo 
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:4659 (4.6 KB) 
          Interrupción:17 Dirección base: 0xec00  
 
lo        Link encap:Bucle local   
          inet dirección:127.0.0.1  Máscara:255.0.0.0 
          dirección inet6: ::1/128 Alcance:Anfitrión 
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:0  
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B) 
 
administrador@ubuntu:~$  

Trabajo en el campo, en una reserva natural provincial, soy guardaparque. Aca en el puesto nos colocaron este año una antena satelital de telecom y nos dejaron un gabinete lleno de equipos, a saber: un modem (DATUM SYSTEM PSM 500L - satellite modem), otro aparato que no se lo que es, dice: Sisco System - Sisco 1800 y lo que creo es un router, donde se conecta la pc.
Esto quedo instalado cuando no teniamos pc. Cuando la conseguimos, tuvimos que habilitar la pc para que funcionase y nos guiaban por telefono (solo hay celulares con muy poca señal)
Lo primero que hicimos fue entrar al explorador/herramientas/opciones de internet/Conexiones/Configuracion de LAN, tildar usar un servidor proxi para la LAN, ingresar direccion y puerto y tildar no usar proxi para conexiones locales.
Creo que eso fue todo. Intente seguir estos pasos con el mozilla, en ubuntu, pero no me funciono, entre en todos los lugares que tenian algo que ver con red e incorpore la IP, la mascara, el puerto, pero el explorador que me decia que el proxi esta rechazando el envio, u otras veces que no reconocia o no habia proxi, algo así. En otra parte me decia que las opciones debian cambiarse en gnome, pero no sabia como entrar.
Muchas gracias por tu tiempo y espero haberte dado los datos necesarios para ayudarme a solucionar este problema. En mi casa tambien instale el ubuntu, pero creo que una version mas nueva, anda de maravillas. Chau, un abrazo.

---

### Post by josecuervo86 on 2009-09-13
Hola, amo de la palabra. El primer comando que te dijo gabriel es:

```
sudo lspci
```

es con l (L) no con i (I) por eso te pone "command not found"

Segundo, la forma mas simple por la que configuro la conexión es mediante:

```
sudo pppoeconf
```

Fijate si poniendo eso en un terminal podes configurarla. Te va a pedir el nombre de usuario de la red y la contraseña (que calculo que tenes)

---

### Post by gmunioz on 2009-09-13
Hola el a....:

Felicitaciones por tu trabajo.

1- Efectivamente, Cisco System - Cisco 1800
es un router de grandes prestaciones.

2- Segun lo que informa lspci, tu placa de red 
ya esta configurada y funcionando:

```
La placa esta reconocida como:
eth0 

su mac address es 
00:06:4f:7f:45:7a

Tiene la dirección IP
10.142.100.49 

Con máscara de red:
255.255.255.192
```


Esto significa que estas conectado y la
tarjeta esta configurada por dhcp
si no puedes navegar es porque te falta
únicamente configurar el proxy

3 - El proxy se configura en forma individual

a- En firefox:
```
Editar --> Preferencias --> Avanzadas --> Red
--> Configuración --> Configuración manual del proxy
--> Usar el mismo proxy para todos los protocolos
y colocando los parámetros que te haya dado en Proxy HTTP
de forma como por ejemplo 10.142.100.63 y en Puerto por
ejemplo 8080
```

b- En Synaptic:
```
Configuración --> Preferencias --> Red 
--> Configuración manual del proxy y repites los parámetros
en ambos items http y ftp
```

c- En el sistema
```
Sistema --> Preferencias --> Proxy de la red
-->Configuración manual del proxy
--> Usar el mismo proxy para todos los protocolos
y colocando los parámetros que te haya dado en Proxy HTTP
de forma como por ejemplo 10.142.100.63 y en Puerto por
ejemplo 8080
```

d- si bien con esto puede ser suficiente, a veces es necesario
además:

Editar los archivos: 

```
a-   /etc/bash.bashrc
sudo gedit  /etc/bash.bashrc
Poner las siguiente lineas al final de este archivo

        export HTTP_PROXY=http://username:password@proxyserver.net:port/
        export HTTPS_PROXY=http://username:password@proxyserver.net:port/
        export FTP_PROXY=http://username:password@proxyserver.net:port/


```
```
b- /etc/environment
sudo gedit /etc/environment
Poner las siguientes lineas al final de este archivo

         HTTP_PROXY=http://username:password@proxyserver.net:port/
         HTTPS_PROXY=http://username:password@proxyserver.net:port/
         FTP_PROXY=http://username:password@proxyserver.net:port/
```

```
username es el nombre de usuario autorizado, si no existe no va nada
password es su contraseña, si no existe usuario no va nada y tampoco @
proxyserver.net es la dirección IP del proxy
port es su puerto

Por ejemplo: HTTP_PROXY=http://10.142.100.63:8080
```

---

### Post by el amo de la palabra on 2009-09-13
Gracias Gabriel y Jose, acabo de salir de franco, así que ahora estoy en casa. En unos días cuando vuelva, probare todo esto que me pasaron, todavia tengo muchas dudas en la forma de entrar al terminal y me da temor hacer lio. Pero bueno, de alguna forma hay que aprender, total, explotar no va a explotar. Pruebo y les aviso, gracias nuevamente y un abrazo. Ah, otra cosa, curoseando descubri no recuerdo donde, una ventana, donde una de las pestañas era PING, esto era algo que me habian pedido hacer para probar la maquina, cuando la conectamos, bueno hice ping en ubuntu y el resultado fue 5 paquetes enviados, 5 paquetesa recibidos, todo en milisegundos, lo menciono por si es un dato de interes. Chau.

---

### Post by guillermolisi on 2009-09-13
> **el amo de la palabra said:**
> Gracias Gabriel y Jose, acabo de salir de franco, así que ahora estoy en casa. En unos días cuando vuelva, probare todo esto que me pasaron, todavia tengo muchas dudas en la forma de entrar al terminal y me da temor hacer lio. Pero bueno, de alguna forma hay que aprender, total, explotar no va a explotar. Pruebo y les aviso, gracias nuevamente y un abrazo. Ah, otra cosa, curoseando descubri no recuerdo donde, una ventana, donde una de las pestañas era PING, esto era algo que me habian pedido hacer para probar la maquina, cuando la conectamos, bueno hice ping en ubuntu y el resultado fue 5 paquetes enviados, 5 paquetesa recibidos, todo en milisegundos, lo menciono por si es un dato de interes. Chau.
Si con el ping no tuviste perdida de paquetes se entiende que conexion con otro puno de la red, que no mencionas cual fue, hay.

Cuando mencionas que no podes conectarte a Internet, precisamente no podes con ningun servicio o solo no podes navegar, por ejemplo ?

---

