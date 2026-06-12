---
title: "Problema con conex. inalambrica HP Mini 100e"
date: 2011-07-18
forum: Software
---

### Post by memors on 2011-07-18
Hola cabros, soy nuevo en Linux, con algunas pocas experiencias pasadas, por porblemas con controladores y ahora tengo un netbook, el HP Mini 100e. Acabo de instalar ubuntu a través de WUBI.. todo marchaba exelente hasta el momento en que no me pescaba la conexion a internet  de forma inalámbrica (ahora estoy conectado a red alámbrica desde  Ubuntu).. He indagado en muchas partes pero no he dado con ningun  resultado..
Piano piano: Cuando voy a el icono (que está entre el  medidor de batería y el selector de volumen en la esquina superior  derecha), despliego las opciones de conexion y me encuentro que en la  seccion de redes inalambricas aparece el siguiente mensaje: "Redes  inalambricas      la red inalambrica está desactivada por el interruptor  fisico"... con dos dedos de frente, me doy cuenta que el interruptor  fisico es aquel que tiene la antena caracteristica de wifi, y se activa y  desactiva con el boton fn+f12 y claro, enciende y apaga una luz  blanca... en windows funciona a la perfeccion, se activa y desactiva la  conexion inalambrica con esto, pero con ubuntu, tambien se enciende y  apaga la lucecilla, pero no se enciende la conexion :C

Cualquier ayuda es ampliamente agradecida

---

### Post by papibe on 2011-07-18
Una idea: quizás exista una opción en el BIOS para dejar siempre prendida la conexión inalámbrica.

Saludos.

---

### Post by memors on 2011-07-18
> **papibe said:**
> Una idea: quizás exista una opción en el BIOS para dejar siempre prendida la conexión inalámbrica.

Saludos.

Probando..

---

### Post by memors on 2011-07-18
nada :C
naipe naipe, en la bios no encontre niuna opcion referida a la conexion inalámbrica

---

### Post by papibe on 2011-07-18
Mala cosa. ¿Cómo está tu lectura del inglés? Encontré un [thread ]("http://ubuntuforums.org/showthread.php?t=1793994")con problema similar y una solución. Revisa si ti HP tiene la misma tarjeta inalámbrica que en esa conversación. Ojalá te sirva.

Buena suerte.

---

### Post by memors on 2011-07-18
pucha, asi como de entradita, no tiene la misma tarjeta wireless.. pero vamos viendo

Gracias peñi C:

---

### Post by memors on 2011-07-18
pucha, la conclusion de ese hilo, fue que la conexion se activaba simplemente con alt+12, en vez de Fn+f12..en mi caso no funcionó :C

---

### Post by papibe on 2011-07-18
Que tarjega tiene tu HP? Con estos comandos se puede ver:
```
$ lshw -C network
```
y
```
$ lspci
```
Saludos.

---

### Post by memors on 2011-07-18
> **papibe said:**
> Que tarjega tiene tu HP? Con estos comandos se puede ver:
```
$ lshw -C network
```y
```
$ lspci
```Saludos.

piano piano..

$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network DISABLED      
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 10
       serial: 18:f4:6a:9b:cf:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=0 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:e000(size=256) memory:fe900000-fe903fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 68:b5:99:64:bb:e6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.6 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:e0004000-e0004fff memory:e0000000-e0003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



y con el otro comando, vamos al grano: 
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

---

### Post by memors on 2011-07-18
cabros, no será un atao' del teclado que no lo pesca bien al hacer la combinacion de fn+f12 simplemente enciende el receptor inalambrico?

---

### Post by papibe on 2011-07-18
Por casualidad el sistema no te ofrece instalar un driver de hardware?  Revisa en System > Administration > Hardware Drivers (perdón pero mi Ubuntu está en inglés).

---

### Post by memors on 2011-07-18
pucha, no se donde está eso.. creo que tengo la ultima version de ubuntu, ya que lo instalé con wubi..

---

### Post by patraicio on 2011-07-19
Si tienes Ubuntu 11.04 (con una barra de tareas superior y otra en el lado izquierdo de la pantalla que posee solo iconos) anda a la esquina superior derecha y pulsa el botón de Apagar>Configuración del Sistema>(mira el lado izquierdo de la ventana que se acaba de abrir)Grupos>Hardware>Controladores Adiocionales

---

### Post by silex89 on 2011-07-22
Hace tiempo experimenté el mismo problema usando GNOME 2, y me di cuenta que el interruptor físico está... "bypasseado"? y que aunque la luz y el interruptor estén encendidos, el wifi no se iba a activar si no iba al network manager y activaba la opción de redes inalámbricas desde el software. Actualmente mi Kubuntu tiene la misma maña, es cosa de activar la casilla de usar redes inalámbricas en tu network manager y, por lo menos a mi, me funciona :)


Suerte :D

---

### Post by memors on 2011-08-17
lo cierto es que probé todo, y nada..
lamentablemente, me desilucioné un kilo..no quiero saber mas de ubuntu, la vez anterior tambien estuve MESES tratando de configurar como corresponde mi tarjeta de video pero nada...

Creo que Win7 es la mejor respuesta a un SO esstable, confiable, amigable... todo lo que esperaba de ubuntu hecho windows..

por eso creo que hay que pagar por windows.. por la calidad del producto final, libre de complicaciones y universal..

Gracias por su ayuda muchachos!

---

### Post by ReivajCL on 2011-09-10
Yo tengo en mi netbook ubuntu tambien es un HP modelo 110-3523la y la conexion inalambrica va exelente y el boton para activar y desactivar la tarjeta inalambrica tambien funciona bien , claro que a diferencia de ti yo en la bios tengo que los F1 , F2 etc funcionen como multimedia, supongamos apreto directamente el F5 para el volumen etc y si kieroo apretar F1 ahii ocupo la tecla fn.
Todo me lo detecto de inmediato inclusive las teclas multimedia lo que me sorprendio.
Instale el ubuntu 11.04 desde un pendrive, ocupo el unity que tiene muchos detractores jaja pero para un net va muy bien se ahorra mucho espacio.
Realmente recomiendo ubuntu para los netbooks por tema de rendimiento, pero si te acomoda mas otro OS es tu decision, Saludos

---

### Post by charlymx on 2011-09-15
Hola al parecer es el driver o del teclado o de la tarjeta de red no esta funcionando correctamente intenta lo siguiente a ver si a ti te funciona a un amigo así lo solucionamos tenia el mismo problema.
en el menu de ubuntu en Administracion vas a ver la opcion de controladores adicionales entras   y automáticamente buscara los controladores  que te faltan y uno de ellos será el de la tarjeta de red una vez que  aceptes la instalación reinicias y ¡¡¡¡¡listo te podrás conectar a  internet inalámbrico.
suerte....:P

---

### Post by V A M P I R O on 2012-07-08
Camarada, tengo el mismo equípo, y este mini tuto me sirvió de una [http://www.ubuntu-es.org/node/158836](http://www.ubuntu-es.org/node/158836).

Saludos.

---

