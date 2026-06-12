---
title: "Conexión de red y Virtual Box"
date: 2008-06-06
forum: Software
---

### Post by Simbiosys on 2008-06-06
Yo instalé WXP en virtualbox pero no logro hacer que acceda a mi red local, por defecto tengo asignada la ip 10.2.1.1 (o similar) y nada que ver con el rango utilizado en mi red...(siempre hablando de la MAQUINA VIRTUAL) cuando voy a la configuración de red, veo que está como DHCP (pero hay algo que estoy haciendo mal o no tengo configurado, porque el servidor DHCP local, es imposible que asigne esa dirección).
Si le asigno una ip manualmente, no funciona. ¿Que hago mal? 

Por motivos laborales utilizo un entorno de desarrollo francés y para correr el cliente necesito hacerlo desde windows, con Wine no funciona 100% bien. Asi que me instalé la VirtualBox pero tengo este problema de red... entonces no puedo acceder al servidor de desarrollo mediante el cliente.

Tengo Ubuntu HH 8.04

MUCHAS GRACIAS!!!!!!! :)

---

### Post by Simbiosys on 2008-06-10
Perdón que insista.
¿Es muy obvia mi pregunta? porque estoy intentando realizar de varias maneras hacer funcionar esto, seguí ya mas de 4 guías... y nada. 

¿Alguien tiene idea de como puedo hacer un debug, a ver que me está faltando?

Gracias de nuevo!!!!!

---

### Post by faktorqm on 2008-06-10
Hola, bueno no se que queres hacer, perdoname pero no te entiendo. Si queres hacer una red, basta con que pongas direcciones ip del mismo rango en ambas. ejemplo: 192.168.1.1 en virtual, con mascara 255.255.255.0 y en la real 192.168.1.2 con la misma mascara. Ahi ya estas en red, pero no podes hacer nada. Si queres compartir supongo que vas a necesitar samba o nfs. Si queres routear internet vas a tener que hacerlo desde el iptables o el firestarter, aunque no se si se puede. (no soy ducho en vbox). Y asi sucesivamente. Salu2!!

---

### Post by Simbiosys on 2008-06-11
> **faktorqm said:**
> Hola, bueno no se que queres hacer, perdoname pero no te entiendo. Si queres hacer una red, basta con que pongas direcciones ip del mismo rango en ambas. ejemplo: 192.168.1.1 en virtual, con mascara 255.255.255.0 y en la real 192.168.1.2 con la misma mascara. Ahi ya estas en red, pero no podes hacer nada. Si queres compartir supongo que vas a necesitar samba o nfs. Si queres routear internet vas a tener que hacerlo desde el iptables o el firestarter, aunque no se si se puede. (no soy ducho en vbox). Y asi sucesivamente. Salu2!!

Fak, gracias por tu respuesta (siempre dispuesto!!!) :guitar:

Te cuento que no es tán sencillo el tema de las maquinas virtuales... estuve leyendo un cacho, básicamente para que la VirtualBox tenga acceso a mi LAN, tengo que tener definida una placa de red "virtual" y asignarsela a la VirtualBox (sería un dispositivo virtual). Luego, hay que crear un bridge entre el dispositivo virtual y el físico (eth0)... pero la verdad es que no estoy logrando obtener buenos resultados, tuve que restaurar archivos un par de veces porque de meter mano me he quedado sin el pan y sin la torta. 

Dejo algunos de los links que estuve mirando:
- [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)
- [http://ubuntuforums.org/showthread.php?t=558971](http://ubuntuforums.org/showthread.php?t=558971)

La verdad que no doy pie con bola, si me pueden tirar alguna soga estaré más que agradecido... es hasta ahora el único límite que tengo laboralmente para usar ubuntu 100%, todavia sigo conectandome por escritorio remoto a una pc con windows xp... quiero divorciarme!!!

Saludos :)

---

### Post by faktorqm on 2008-06-11
Bueno hace una cosa, vos asegurate de crear la placa de red virtual, asegurate de que te ande en el vbox y luego vemos lo de internet o lo que necesites. salu2!

---

### Post by Simbiosys on 2008-06-12
Hola Fak, la vBox anda de 10. Si la configuro como NAT tengo internet (pero no red local) y es ese el motivo por el cual debo hacer todo el enrollo de la placa de red virtual y el bridge.

La verdad es que como soy un desentendido, no se como asegurarme de que la placa de red virtual y el bridge funcionen... :mad:

---

### Post by eldragon on 2008-06-12
te cuento que yo no instale nada del estilo, use la configuracion de red como se le canto, me asigna el ip de otra subred como a vos, pero simplemente tengo acceso a la red local y a internet. veo las pcs en mi casa, accedo a ellas.

no se que es lo que te falta a vos, instalaste el guest aditions?

---

### Post by Simbiosys on 2008-06-12
A mi me asigna una dirección 10.0.0.2 que es un rango totalmente diferente al que tengo en mi red. (Esto si tengo como configuración NAT) sí tengo internet pero no acceso a la LAN.

¿Podrías poner un pantallazo de la configuración de red de tu vBox?
El guest aditions lo tengo instalado...

---

### Post by jsartti on 2008-06-12
Hola,

Si la idea es acceder a la red local, la configuración de red debe ser "host" y no "nat". En las versiones 1.5.6 y 1.6.0 de vbox agrega dos scripts en el inicio (vboxdrv y vboxnet) que configuran automáticamente el bridge entre la tarjeta virtual y la real.
En las versiones anteriores el script tenés que crearlo vos, pero en la ayuda de vbox está explicado clarito como hacerlo (en inglés, pero clarito).

Espero que esto te ayude.

Saludos desde Montevideo, Uruguay

Juan

---

### Post by eldragon on 2008-06-12
la verdad que no se a que te estas refiriendo con un pantallazo de las configuraciones de la red.

en la VM, no hice nada, lo deje auto y dhcp, si mal no me equivoco, el virtualbox arma un dhcp para las maquinas virtuales y hace de puente entre tu red local y la red virtual. y lo hace transparentemente.

probaste buscando alguna pc de tu red directamente? en direccion: //nombre

asi me muevo yo directamente. de todos modos, prefiero mantener un disco virtual lo suficientemente chico, y guardo todas mis cosas directamente en una carpeta compartida en la pc host. de esta manera no dependo de tener el guest funcionando para acceder a mis archivos.

---

### Post by Simbiosys on 2008-06-12
Juan, gracias por tu respuesta.

La versión que tengo instalada de vBox es la 1.6.0 (sin saber absolutamente nada de virtual box ni de puentes o redes virtuales) me mandé a modificar cosas. Voy a revisar de restaurar todo y volver a probar... pero me interesaría saber si existe alguna manera de corroborar todas las cosas que nombramos (bridge, placa virtual, etc).

Otra cosa: utilizo ubuntu desde hace 15 días... estoy muy contento pero este tema es el unico que me tiene atado a windows :(

Gracias por tu interes, un saludo y vamo arriba la celeste!

---

### Post by ariel on 2008-07-02
> **Simbiosys said:**
> Yo instalé WXP en virtualbox pero no logro hacer que acceda a mi red local, por defecto tengo asignada la ip 10.2.1.1 (o similar) y nada que ver con el rango utilizado en mi red...(siempre hablando de la MAQUINA VIRTUAL) cuando voy a la configuración de red, veo que está como DHCP (pero hay algo que estoy haciendo mal o no tengo configurado, porque el servidor DHCP local, es imposible que asigne esa dirección).
Si le asigno una ip manualmente, no funciona. ¿Que hago mal? 

Por motivos laborales utilizo un entorno de desarrollo francés y para correr el cliente necesito hacerlo desde windows, con Wine no funciona 100% bien. Asi que me instalé la VirtualBox pero tengo este problema de red... entonces no puedo acceder al servidor de desarrollo mediante el cliente.

Tengo Ubuntu HH 8.04

MUCHAS GRACIAS!!!!!!! :)

Yo uso soporte de redes en una maquina virtual VBox, uso la configuracion default (NAT). Nunca tuve problemas, la maquina virtual puede acceder a cualquier host de la red local, salir a internet, entrar a carpetas compartidas en otras maquinas de la red local, etc.  Esto es en dos hosts ubuntu, uno es mi laptop en la oficina, y el otro un desktop.

Nunca tuve que usar ningun tipo de script o hacer ningun cambio en la configuracion de los hosts. "It just worked"

En tu caso, a lo mejor estas intentando usar en el guest (maquina virtual) una aplicacion especifica o casera que no tiene soporte para NAT.

---

### Post by godzeus on 2008-07-03
Espero no desvirtuar el post con mi comentario, pero me gustaria comentar mi experiencia.
Trabajo en sistemas y un par de meses me dieron una notebook nueva para instalarle lo que quiera, de entrada Ubuntu HH 8.04, y por cualquier cosa,, un virtualbox con un windows liviano. Para que la maquina virtual tenga conectividad a internet, tenia que ejecutar antes un script para levantar un bridge con la eth0 de mi maquina para poder tener internet.
Con esto ponia el bridge en dhcp, y el windows levantaba solo la ip de la red en cuestion, el tema es que despues de unas actualizaciones del kernel, el vbox empezo a comportarse de manera extraña, me colgaba la maquina, se reiniciaba solo, con algunos programas que antes andaban, dejo de andar, muy raro.
Con un compañero de laburo que tenia un problema similar, decidimos probar VMware ver. 1.0.6, se que no es la ultima, pero la version 2 no es muy estable todavia. Con esto se acabaron mis problemas, me creo la cantidad de interfaces necesarias, 1 para dhcp (por aca salgo a internet), y dos adicionales, 1 NAT y 1 Host-only.
No tengo que ejecutar nada, se encarga de configurar todo solo. Si no es condicion que se ejecute solo VBox, te recomendaria que pruebes VMware, ademas el rendimiento de la maquina fisica es superior que con vbox.
Si necesitas ayuda, avisame por aca y nos contactamos..

Saludos:)

---

### Post by gazambuja on 2008-07-05
Hace un tiempo escribi un post en mi blog para hacer exactamente lo que queres utilizando Qemu, pero en general es exactamente lo mismo:

[http://gazambuja.ideas3.com/2008/05/11/virtualizando-servidores-qemu/]("http://gazambuja.ideas3.com/2008/05/11/virtualizando-servidores-qemu/")

básicamente tenes que usar VDE ([http://vde.sourceforge.net](http://vde.sourceforge.net)) para hacer eso fácilmente, y tener x PC virtuales dentro de la red, donde incluso las otras estaciones de tu red podrán acceder a tu pc virtual.

**ACTUALIZADO:** Hay que hacer un par de cositas más que para QEmu, aca escribi como hacerlo: [http://gazambuja.ideas3.com/2008/07/06/vde-y-virtualbox/]("http://gazambuja.ideas3.com/2008/07/06/vde-y-virtualbox/").

Saludos,
Gustavo Azambuja

---

### Post by aelohin on 2008-08-11
Hola que tal, al igual que tu ando en los tramites del divorcio con el XP :lolflag:, y tambien tengo que usarlo por... bueno...

Logre solucionarlo de la siguiente manera, en la configuración de red lo conecte a Host Interface y luego en la parte de abajo la creas, esto crea una tarjeta de red virtual en tu maquina que es la que va a estar en el mismo segemento de IP.

[IMG]http://lh6.ggpht.com/aelohin/SKB5Lmk_jOI/AAAAAAAAALg/c_LF7fGAOBc/vboxred.JPG?imgmax=512[/IMG]

Tambien encontre esto:
[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Simbiosys on 2008-08-20
Che, gracias por tu ayuda... te cuento que yo no tengo esas opciones en mi VirtualBox... visité la pagina oficial y estoy descargando una version mucho mas nueva (1.6.4) yo tengo 1.6.2

Probaré y te cuento... gracias!!

---

