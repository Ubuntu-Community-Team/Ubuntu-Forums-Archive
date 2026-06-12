---
title: "no tengo ninguna red ni puedo configurar una"
date: 2009-03-02
forum: Software
---

### Post by N3RI on 2009-03-02
les cuento, tengo speedy y me vinieron a cambiar el modem por uno wifi. Desde entonces, en la PC de escritorio no tengo internet en ubuntu, pero sí en una partición con windows xp y en la notebook, la palm o cualquier cosa que se conecte por wifi. También si pongo un livecd de ubuntu, se conecta sin configurar nada. El router es un Zyxel wifi (no sé bien el número de modelo) que está ruteado.

En ubuntu, intenté lo siguiente:

1. configurar internet como había hecho con el modem anterior (supuse que me mostraría opciones para dejarlo directo sin poner user y password)pero cuando hago 
**sudo  pppoeconf**
dice que encuentra eth0 y luego busca algo y aparece este error:
> Lo siento, se consultaron 1 interface, pero no
respondió el concentrador de acceso de su proveedor.

Por favor, verifique sus cables de red y del módem.
Otra razón del fallo puede ser también que esté
ejecutándose otro proceso pppoe y que éste esté
controlando el módem.


2. probé haciendo **ifconfig eth0** 
eth0      Link encap:Ethernet  direcciónHW 00:19:d1:84:b0:b0
dirección inet6: fe80::219:d1ff:fe84:b0b0/64 Alcance:Vínculo
ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000
RX bytes:300 (300.0 B)  TX bytes:2568 (2.5 KB)
Interrupción:250 Dirección base: 0x6000
connect: Network is unreachable

3. probé en el icono de red (que tiene una cruz roja) y en "información" dice que no se encontró ninguna red. En la configuración manual, no tengo ninguna red, ni cableada, ni inalámbrica ni DSL.
Pruebo con añadir una nueva conexión cableada (supongo que esa es la opción correcta, no?) y los datos que me pide, no sé bien qué completar.
En Dirección MAC pongo 00:19:d1:84:b0:b0 (también probé con la que está escrita debajo del router)
En MUT dejo Automático
Aceptar y no pasa nada, tampoco reiniciando. Tampoco funciona con DHCP automático.
Entonces agrego más datos, en Ajustes de IPv4 pongo los mismos datos que aparecen cuando pongo el liveCD
IP: 192.16831.2
DNS: 200.51.211.7
No sé qué poner en **ID del cliente DHCP**
Aceptar, reiniciar por las dudas, pero nada pasa, sigue diciendo que no encuentra ninguna red, sigue la cruz roja.
Por cierto, la "conexión cableada" al costado dice "nunca", pero no sé qué es.

4. también probé cosas como hacer ping a todo, google, localhost, la ip del router, nada funciona (no recuerdo ahora dónde anoté el error que daba, pero si quieren lo vuelvo a probar)

Y hasta ahí llegaron mis ideas. En teoría y según la ayuda de ubuntu, según la guía ubuntu, según lo que encontré en google, si el router está ruteado "tendría que conectarse directamente" (como pasa con el LiveCD)

Bueno, les agradezco las sugerencias.

---

### Post by infernus92 on 2009-03-02
te fijaste que este desactivada la opcion de seguridad desde la configuracion de red?
es raro porque yo me conecte a una red... enchufe el conector y empezo a andar sola...
que veersion de ubuntu tenes?

---

### Post by luks911 on 2009-03-03
Sí, es raro. Tengo el mismo router configurado igual y la máquina se conecta sin tocar nada. 
No soy experto en redes, pero se me ocurre mirar el archivo /etc/network/interfaces. El mío tiene estas dos líneas
```

auto lo
iface lo inet loopback
```
Por otro lado, qué te devuelve el comando route y qué pasa si tratás de hacer un ping al router, cuya ip debería ser 192.168.1.1

Ah, y algo más, si el modem está puesto como router (así parece ser si se conecta automáticamente desde el Live CD) no sigas probando con pppoeconf porque no hace falta.

---

### Post by biale on 2009-03-03
¿Lei que en esa misma computadora y arrancando WXP, la red funcionaba bien?

Si es asi, ingresa a WXp y postea la salida del comando de consola

```
ipconfig /all
``` 

Y si en Ubuntu configuras la tarjeta de red en forma estatica (sin DHCP) con esos mismos parametros tendría que andar bien. O sea:

IP, mascara, Def Gateway y DNS

Saludos.

---

### Post by N3RI on 2009-03-03
YA LO SOLUCIONÉ! (no se puede editar el primer post para ponerle un [solucionado]

> **infernus92 said:**
> te fijaste que este desactivada la opcion de seguridad desde la configuracion de red?
es raro porque yo me conecte a una red... enchufe el conector y empezo a andar sola...
que veersion de ubuntu tenes?
la última versión. La opción de seguridad estaba desactivada.

> **luks911 said:**
> Sí, es raro. Tengo el mismo router configurado igual y la máquina se conecta sin tocar nada. 
No soy experto en redes, pero se me ocurre mirar el archivo /etc/network/interfaces. El mío tiene estas dos líneas
```

auto lo
iface lo inet loopback
```
Este era el problema, el archivo tenía la configuración vieja todavía,
Mi interfaces decía:
```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

```
al borrarla y dejarlo igual al tuyo, reinicié y salió andando. 

Era lo que yo suponía nomás, la configuración anterior estaba molestando; pero yo no sabía dónde ir a borrarla. En el icono de red no mostraba ninguna conexión, entonces yo creaba una cableada a mano, pero no pasaba nada. Yo pensé que probando con **sudo pppoeconf** me iba a dar la opción de desactivarla, pero no.

Si vuelve a fallar, ya voy a saber que es porque cuando configuré el modem anterior, en algún lado que ahora no me acuerdo, lo puse para que levante solo esa configuración "auto dsl-provider". Entonces voy a tener que ver dónde está para quitarlo.

Bueno, les agradezco las respuestas. Saludos.

---

### Post by luks911 on 2009-03-03
Genial. Me alegro de que haya servido.

Saludos

---

