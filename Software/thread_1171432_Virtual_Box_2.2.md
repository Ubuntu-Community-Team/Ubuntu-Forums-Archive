---
title: "Virtual Box 2.2"
date: 2009-05-27
forum: Software
---

### Post by rony3 on 2009-05-27
Hola.
Pues he instalado Virutal Box 2.2 sobre Ubuntu 9.04 y todo perfecto salvo una dudilla con la red.
Puedo acceder desde la maquina virtual creada (Windows XP ) a internet y a los servicios que tengo instalados sobre Ubuntu (anfitrion) sin problema ninguno, pero a la inversa no, es decir, desde ubuntu ni siquiera puedo hacer ping a la direccion de la maquina virtual aún estando en el mismo rango de IP's (192.168.1.34,192.168.1.35).
He probado a cambiar el modo de red de la configuracion de la maquina virtual  a NAT y tampoco. En este ultimo caso, aunque me asigna para las maquinas virtuales direcciones ip en otro rango (10.0.2...) tengo el mismo problema: No puedo acceder a al windows xp virtual desde ubuntu. En este ultimo modo al hacer un ping desde la terminal de ubuntu me sale algo como "packet filtering". Entiendo que los packetes que vengan de según qué direccion son descartados, lo que no se es qué es lo que hay que modificar para que esto no ocurra. He leido por ahi algo sobre las herramienas bridge utils y en estos momentos estoy consultado el manual (la parte de red) de virtual box 2.2 y los modos de funcionamiento, pero por si alguien lo  ha probado y sabe algo antes de ponerme a toquetear nada escribo esto aqui.

Gracias.

---

### Post by guillermolisi on 2009-05-27
> **rony3 said:**
> Hola.
Pues he instalado Virutal Box 2.2 sobre Ubuntu 9.04 y todo perfecto salvo una dudilla con la red.
Puedo acceder desde la maquina virtual creada (Windows XP ) a internet y a los servicios que tengo instalados sobre Ubuntu (anfitrion) sin problema ninguno, pero a la inversa no, es decir, desde ubuntu ni siquiera puedo hacer ping a la direccion de la maquina virtual aún estando en el mismo rango de IP's (192.168.1.34,192.168.1.35).
He probado a cambiar el modo de red de la configuracion de la maquina virtual  a NAT y tampoco. En este ultimo caso, aunque me asigna para las maquinas virtuales direcciones ip en otro rango (10.0.2...) tengo el mismo problema: No puedo acceder a al windows xp virtual desde ubuntu. En este ultimo modo al hacer un ping desde la terminal de ubuntu me sale algo como "packet filtering". Entiendo que los packetes que vengan de según qué direccion son descartados, lo que no se es qué es lo que hay que modificar para que esto no ocurra. He leido por ahi algo sobre las herramienas bridge utils y en estos momentos estoy consultado el manual (la parte de red) de virtual box 2.2 y los modos de funcionamiento, pero por si alguien lo  ha probado y sabe algo antes de ponerme a toquetear nada escribo esto aqui.

Gracias.
La VM con XP deberia estar en red via bridge, no NAT, y tenes que configurar la placa de red que usa WinXP dentro de la misma red en donde se encuentra Ubuntu.

Es decir, si Ubuntu esta en 192.168.1.1 con mascara 255.255.255.0 tu XP virtualizado deberia usar 192.168.1.x (donde x no es ni 0 ni 1)con la misma mascara que Ubuntu.

Como puerta de acceso por defecto pone la IP del Ubuntu.

Esto deberia poder ser resuelto sin acudir a bridge-utils.

---

### Post by rony3 on 2009-05-27
> **guillermolisi said:**
> La VM con XP deberia estar en red via bridge, no NAT, y tenes que configurar la placa de red que usa WinXP dentro de la misma red en donde se encuentra Ubuntu.

Es decir, si Ubuntu esta en 192.168.1.1 con mascara 255.255.255.0 tu XP virtualizado deberia usar 192.168.1.x (donde x no es ni 0 ni 1)con la misma mascara que Ubuntu.

Como puerta de acceso por defecto pone la IP del Ubuntu.

Esto deberia poder ser resuelto sin acudir a bridge-utils.

Hola,

El modo bridge ya lo probé, con los rangos de ip en el mismo segmento tanto para el host anfitrion(ubuntu) como para la maquina virtual(xp). La ip del xp me la da el dhcp del virtual box. Pero como digo más arriba mi problema es cuando quiero conectar desde ubuntu hacia xp , en el otro sentido no tengo ningún problema. Tengo instalado el tomcat  en ubuntu y desde el xp virtualizado puede acceder a él con  [http://192.168.1.33:8080](http://192.168.1.33:8080), siendo 192.168.1.33 la direccion ip de ubuntu que me da mi router. Tambien puede acceder a internet. Lo de el NAT era para ver si me daba algun mensaje o información de porqué no llegan los paquetes desde el ubuntu al xp , como así fue: packet filtering que comento más arriba. 

XP (Virtual)                                                                   
=========                                                                   
 IP: 10.0.2.15                                                                
Máscara de subRed: 255.255.255.0                           
Puerta de enlace predeterminada: 10.0.2.2
Servidor DHCP:10.0.2.2 

Ubuntu (Anfitirion)
  ==============
 IP: 192.168.1.33                                                                 
 Máscara de subRed: 255.255.255.0     

gonzalo@ubuntu-acer:~$ route

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask      Indic Métric    Ref    Uso   Interfaz
192.168.1.0     *               255.255.255.0   U        2          0        0        wlan0
link-local          *               255.255.0.0       U     1000       0        0        wlan0
default         192.168.1.1     0.0.0.0            UG       0        0        0        wlan0
 

[COLOR=Red]DESDE EL XP[/COLOR]:     (ok)               

C:\Documents and Settings\gonzalo>ping 192.168.1.33

Haciendo ping a 192.168.1.33 con 32 bytes de datos:

Respuesta desde 192.168.1.33: bytes=32 tiempo=990ms TTL=127
Respuesta desde 192.168.1.33: bytes=32 tiempo=520ms TTL=127
Respuesta desde 192.168.1.33: bytes=32 tiempo=1050ms TTL=127
Respuesta desde 192.168.1.33: bytes=32 tiempo=493ms TTL=127

Estadísticas de ping para 192.168.1.33:
    Paquetes: enviados = 4, recibidos = 4, perdidos = 0
    (0% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 493ms, Máximo = 1050ms, Media = 763ms

C:\Documents and Settings\gonzalo>tracert 192.168.1.33

Traza a 192.168.1.33 sobre caminos de 30 saltos como máximo.

  1     1 ms    <1 ms    <1 ms  10.0.2.2
  2   480 ms   467 ms   537 ms  192.168.1.33

Traza completa.

[COLOR=Red]DESDE UBUNTU:[/COLOR] (No llega) 

root@ubuntu-acer:/home/gonzalo# ping 10.0.2.2
PING 10.0.2.2 (10.0.2.2) 56(84) bytes of data.
From[COLOR=Red] 192.168.153.1[/COLOR] icmp_seq=1 Packet filtered
^C
--- 10.0.2.2 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

root@ubuntu-acer:/home/gonzalo# ping 10.0.2.15
PING 10.0.2.15 (10.0.2.15) 56(84) bytes of data.
From [COLOR=Red]192.168.153.1[/COLOR] icmp_seq=1 Packet filtered
From [COLOR=Red]192.168.153.1[/COLOR] icmp_seq=2 Packet filtered
^C
--- 10.0.2.15 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1002ms

root@ubuntu-acer:/home/gonzalo# tracert 10.0.2.2
traceroute to 10.0.2.2 (10.0.2.2), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.637 ms  2.720 ms *    [COLOR=Red]// Direccion ip de mi router adsl [/COLOR]
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * [COLOR=Red]192.168.153.1[/COLOR] (192.168.153.1)  34.654 ms !X *
root@ubuntu-acer:/home/gonzalo# tracert 10.0.2.15
traceroute to 10.0.2.15 (10.0.2.15), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.306 ms  1.974 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * [COLOR=Red]192.168.153.1[/COLOR] (192.168.153.1)  34.879 ms !X *
root@ubuntu-acer:/home/gonzalo# 

Seguiré mirando , porque la  [COLOR=Red]192.168.153.1 [COLOR=Black]no se qué direccion es.[/COLOR][/COLOR] No se si es que mi router no sabe llegar a la interfaz virtual del xp porque no la  tiene en su tabla de enrutamiento o los paquete se filtran una vez que llegan al virtual box  y no hace nat  para convertir las 192.168.1.0 en las 10.0.2.0. Además me aparecen más interfaces al hacer un ifconfig -a : pan0, vboxnet0 y wmaster0.

Gracias.

---

### Post by uidb4056 on 2009-05-27
Debes revisar la configuración del Firewall en XP para permitir la respuesta al ping (ICMP)

---

### Post by rony3 on 2009-05-27
> **uidb4056 said:**
> Debes revisar la configuración del Firewall en XP para permitir la respuesta al ping (ICMP)

Pues sí, era el firewall del XP.
Como nunca le hago mucho caso...


Gracias

---

### Post by aledruetta on 2009-05-28
Perdón ¿y cómo resolviste lo del firewall de windows?

---

### Post by rony3 on 2009-05-28
> **aledruetta said:**
> Perdón ¿y cómo resolviste lo del firewall de windows?

¿Desactivar el firewall de Windows ? 
Inicio => Panel de Control => Centro de Seguridad => FireWall de Windows: Desactivado [no se recomienda], jeje

Saludos.

---

### Post by aledruetta on 2009-05-28
> **rony3 said:**
> ¿Desactivar el firewall de Windows ? 
Inicio => Panel de Control => Centro de Seguridad => FireWall de Windows: Desactivado [no se recomienda], jeje

Saludos.


ahhhh... qué problema... no sé si me animo...

---

### Post by rony3 on 2009-05-29
> **aledruetta said:**
> ahhhh... qué problema... no sé si me animo...

Si te refires a que no sabes si animarte a instalar el Virtual Box 2.2, yo seguí al pié de la letra los dos siguientes enlaces y me va perfecto:

[http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-22-en-ubuntu-904-desde-repositorios/](http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-22-en-ubuntu-904-desde-repositorios/)

[http://hyanetworks.com/wordpress/2009/05/06/activar-puertos-usb-a-la-maquina-virtual-de-virtual-box-en-ubuntu-904-jaunty](http://hyanetworks.com/wordpress/2009/05/06/activar-puertos-usb-a-la-maquina-virtual-de-virtual-box-en-ubuntu-904-jaunty)

---

### Post by aledruetta on 2009-05-31
> **rony3 said:**
> Si te refires a que no sabes si animarte a instalar el Virtual Box 2.2, yo seguí al pié de la letra los dos siguientes enlaces y me va perfecto:

[http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-22-en-ubuntu-904-desde-repositorios/](http://www.marlonj.com/blog/2009/04/instalacion-virtualbox-22-en-ubuntu-904-desde-repositorios/)

[http://hyanetworks.com/wordpress/2009/05/06/activar-puertos-usb-a-la-maquina-virtual-de-virtual-box-en-ubuntu-904-jaunty](http://hyanetworks.com/wordpress/2009/05/06/activar-puertos-usb-a-la-maquina-virtual-de-virtual-box-en-ubuntu-904-jaunty)


En realidad, me refería a que no me animo a desactivar el firewall en windows. Pero gracias por la info, de todos modos,
saludos,
Alejandro.

---

### Post by Mister X on 2009-06-01
> **aledruetta said:**
> En realidad, me refería a que no me animo a desactivar el firewall en windows. Pero gracias por la info, de todos modos,
saludos,
Alejandro.

podes agegar excepciones para permitir determinados puertos

---

### Post by aledruetta on 2009-06-01
> **Mister X said:**
> podes agegar excepciones para permitir determinados puertos

En Windows uso ZoneAlarm Free. En Zone aparecen las siguientes reglas predeterminadas:

```
Adaptador Ethernet PCI AMD PCNET Family - Minipuerto del administrador de paquetes / 192.168.1.101/255.255.255.0 / Adapter Subnet / Internet

DHCP Server / 10.0.2.2 / IP Adress / Trusted

DNS Server / 201.6.0.115 / IP Adress / Trusted
```Las opciones que tengo para agregar son:

```
Host/Site
IP Adress
IP Range
Subnet
```¿Alguna de esas sirve para agregar puertos?

Otra duda, 

Si el firewall de windows permite ver en ubuntu ¿por qué no permitiría, con esa configuración que tiene, ver desde ubuntu?

Saludos y muchas gracias,
Alejandro.

---

