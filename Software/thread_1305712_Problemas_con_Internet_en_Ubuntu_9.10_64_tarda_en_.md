---
title: "Problemas con Internet en Ubuntu 9.10 64 tarda en cargar paginas"
date: 2009-10-30
forum: Software
---

### Post by madbyte on 2009-10-30
Buenas, 

Estuve usando Ubuntu 9.04, 32 bits, y nunca tuve problemas con internet, peeeero hoy después de instalar la version 9.10, 64 bits, parece que algun problema hay con los DNS, por ejemplo Firefox tarda demasiaaaaaaado en cargar las paginas y Google Earth me tira errores de conexión que nunca tuve usando la 9.04, y no un es problema de velocidad, ya que puedo bajar archivos a máxima velocidad, solo tarda demasiado en resolver las direcciones.  Alguien sabe algo de esto??

Muchas gracias.

Agrego:
Tengo también XP e internet anda de 10.
Tengo un red WiFi armada con un router inhalambrico, con los DNS de opendns.

Encontré esto: 
[http://ubuntuforums.org/showthread.php?t=1272161](http://ubuntuforums.org/showthread.php?t=1272161)

---

### Post by madbyte on 2009-10-30
Esto resolvió el problema de Firefox:

*[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)*

*By default, when Firefox 3.5 is installed, web pages are loaded slowly and it looks like IPv6 DNS lookups is the cause. However, you can go to [about:config](about:config) and change network.**dns.disableIPv6 to true, the problem gets fixed.*
 
Sigo sin solución para Google Earth.

Saludos

---

### Post by madbyte on 2009-11-02
[SIZE=2]Bien... seguí los pasos indicados en esta pagina [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10) para deshabilitar el ipv6 y después de seguir las instrucciones el Google Earth salió andando. Aca están los pasos que me funcionaron a mi:

Editar */etc/default/grub* y cambiar 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

a:
[B]GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

[/B] Hacer luego:
[B]sudo update-grub

[/B] Para finalizar realizar los siguientes cambios para evitar demoras:[B]

Hacer en Firefox:
[/B]about:config y cambiar **network.dns.disableIPv6** a **true **(mi primer post)

**y por  último ssh:**
Editar */etc/ssh/ssh_config* o *~/.ssh/config* y agregar al final de los hosts

[B]host *

AddressFamily inet[/B]

saludos[/SIZE]

---

### Post by Tosh78 on 2009-11-03
Muchas gracias! Estaba buscando algo de esto porque tengo el mismo problema que vos. Voy a probarlo!

---

### Post by rubioo on 2009-11-03
Gracias, a mi tambien me tarda mas que antes.
Voy a probar haber si funciona :)

---

### Post by mama21mama on 2009-11-03
Si usan speedy o sus ips usan de puente a telefonica, parece que anda mal.
Eso me pasa a mi y otros, yo uso opendns con speedy pero hace unos días el servicio esta pésimo; pongo una pagina y debo recargar nuevamente para que se visualice. Intente llamar a soporte y no te atienden. Creo que esta caido un nodo importante y es como domino para las pymes que se cuelgan de ese nodo.

---

### Post by rubioo on 2009-11-03
Yo tengo speedy :/

---

### Post by madbyte on 2009-11-03
En mi caso no era problema del ISP, sino *DNS lookups *generados por el ipv6 produciendo demoras para resolver direcciones. Algunas páginas demoraban hasta 30 segundos o más en cargar, y si las mismas tenían referencias a otros sitios, como por ejemplo Google Analytics demoraban el doble. Estas demoras causaban también que el Google Earth por ejemplo me diera errores por time out diciendo que no se podía conectar al servidor.
Tengo una red wifi al cual se conectan 2 máquinas con XP, otra con Ubuntu y hasta un Nokia N85 y con la única que tuve problemas fue con la que tiene Ubuntu 9.10, en los equipos restantes cualquier página o dirección entran al toque. Asi que seguí los pasos sugeridos para deshabilitar el ipv6 y ahora anda todo perfecto. Y como dije en mi primer post, antes tenía instalado Ubuntu 9.04 y nunca tuve problemas con internet, fue cuando cambié a KK. (aclaro por las dudas que no actualicé, compre disco nuevo e instale Ubuntu 9.10 desde cero)

Saludos

---

### Post by N3RI on 2009-11-16
tenía el mismo problema y seguí estas instrucciones y aparentemente se ha solucionado.
En mi caso, en la misma máquina tengo windows xp y funcionaba perfecto, además otra máquina con ubuntu 9.04 que andaba bien y una netbook que por wifi también funcionaba, al igual que el celular y la palm.

Me puse a investigar cuál era el problema y noté que tanto el torrent como el empathy, amule, todo andaba bien, incluso si intentaba descargar un archivo desde una página, bajaba a máxima velocidad.

Pero las páginas tardaban mucho en aparecer, se quedaban "cargando" un buen rato.


Ahora, la pregunta es... al desactivar el IPv6... ¿nos estamos perdiendo de algo? Es una solución definitiva o es mejor seguir investigando y dejar esto como estaba lo antes posible?

Saludos

> **madbyte said:**
> [SIZE=2]Bien... seguí los pasos indicados en esta pagina [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10) para deshabilitar el ipv6 y después de seguir las instrucciones el Google Earth salió andando. Aca están los pasos que me funcionaron a mi:

Editar */etc/default/grub* y cambiar 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

a:
[B]GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

[/B] Hacer luego:
[B]sudo update-grub

[/B] Para finalizar realizar los siguientes cambios para evitar demoras:[B]

Hacer en Firefox:
[/B]about:config y cambiar **network.dns.disableIPv6** a **true **(mi primer post)

**y por  último ssh:**
Editar */etc/ssh/ssh_config* o *~/.ssh/config* y agregar al final de los hosts

[B]host *

AddressFamily inet[/B]

saludos[/SIZE]

---

### Post by guillermolisi on 2009-11-16
> **N3RI said:**
> 
Ahora, la pregunta es... al desactivar el IPv6... ¿nos estamos perdiendo de algo? Es una solución definitiva o es mejor seguir investigando y dejar esto como estaba lo antes posible?

Saludos
Salvo que tu ISP ya cuente con servicio IPv6 y lohayas contratado (cosa que sabrias porque impactaria en tu instalacion y en tu bolsillo), no te perdes de nada.

Cuando este disponible, volves a activarlo y listo.

---

### Post by djgus on 2009-11-16
Los ISP de Argentina dan servicio al usuario final con IPv4, por lo tanto si usas IPv6 lo unico que va a pasar es que tu maquina intente navegar pero la pila de protocolos no va a resolver nada ya que del lado del ISP hay otro protocolo corriendo, por lo tanto despues de varias colisiones tu maquina dice AHH.. tengo que volver a IPv4 y entonces resuelve todo bien, por eso es la demora.
Por ahora nada se pierde.

---

### Post by N3RI on 2009-11-16
> **guillermolisi said:**
> Salvo que tu ISP ya cuente con servicio IPv6 y lohayas contratado (cosa que sabrias porque impactaria en tu instalacion y en tu bolsillo), no te perdes de nada.

Cuando este disponible, volves a activarlo y listo.

tengo speedy 2 play, el servicio de televisión on demand. 

Pero calculo q estos cambios sólo afectan a la PC y mientras está dentro de ubuntu, no creo q afecte a las demás máquinas de la red (como el decodificador del speedy 2 play)

qué servicios IPv6 existen?

gracias x las respuestas

---

### Post by guillermolisi on 2009-11-16
> **N3RI said:**
> 
qué servicios IPv6 existen?

gracias x las respuestas
Esta es una pregunta ideal para la seccion Comunidad, no para este thread :)

---

### Post by madbyte on 2009-11-16
> **N3RI said:**
> tengo speedy 2 play, el servicio de televisión on demand. 

Pero calculo q estos cambios sólo afectan a la PC y mientras está dentro de ubuntu, no creo q afecte a las demás máquinas de la red (como el decodificador del speedy 2 play)

qué servicios IPv6 existen?

gracias x las respuestas

Sólo agrego que si queres usar ipV6 también vas a necesitar un router compatible, el que tengo yo no viene con ipv6 ni tiene un upgrade del firmware que lo soporte por ahora.

Saludos

---

