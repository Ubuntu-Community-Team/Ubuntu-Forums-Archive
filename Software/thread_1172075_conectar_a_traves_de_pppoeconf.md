---
title: "conectar a traves de pppoeconf"
date: 2009-05-28
forum: Software
---

### Post by latin0 on 2009-05-28
Hola es la primera vez q me veo en la necesidad de postear una consulta en el foro ya que googleando y buscando en el antiguo foro no llegue a dar con la solucion en concreto.

El problema es el siguiente. Antes de actualizar a la version 9.04 conectaba mi pc a internet mediante el comando pppoeconf desde la terminal de esta forma cada vez q cargaba el SO estaba siempre conectado.
Al actualizar a la nueva version el network manager me indicaba que el dispositivo no estaba gestionadolo que causaba que tras reiniciar la PC no pudiera volver a conectar.

al revisar con ifconfig las direcciones IP la interfaz ppp0 me da una direccion publica valida sin embargo la eth0 me la muestra en blanco impidiendome incluso ver los demas equipos del grupo de trabajo. modifique el archivo interfaces de la carpeta etc/network dejandolo asi.

auto lo  
iface lo inet loopback 

con esto el network manger vuelve a gestionar el dispositivo permitiendo reconfigurar las conexion DSL sin embargo a pesar de de marcar la checkbox "conectar automaticamente" me pide cada vez q prendo el pc la contraseña root a pesar de que le doy a la opcion de siempre permitir. se que es solo por comodidad de no tener que marcar la conexion cada vez que entro como en windows ya que me conecto a traves de un modem. mi archivo de interfaces cuando lo tengo con el pppoeconf me queda asi

auto lo  
iface lo inet loopback  

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

y solo puedo conectar a internet de esta forma dentro de la sesion actual, tras reiniciar el equipo se produce la complicacion de tener que hacer lo expuesto mas arriba.
se que solo es problema de configuracion o de conflictos entre ambos modos de conectar a la red ya que de ambas formas lo puedo hacer.

bueno para no hacer mas largo el post agradeceria si alguien me puede indicar como configurar, ya sea por el network manager o mediante comando, la conexion de forma automatica, cosa que tras cargar el SO ya este conectado sin tener que requerir una accion por parte del usuario. de antemano muchas gracias. mientras seguire buscando a ver si doy con la solucion en la red.

saludos ubunteros

---

### Post by moreback on 2009-05-28
Network-Manager te pide contraseña para acceder al anillo de seguridad donde está almacenada los datos de login de tu cuenta de ADSL. Normalmente lo hace sólo la primera vez, pero el acceso al anillo no está abierto cuando **logeas sin contraseña** en Ubuntu, por eso te pide siempre la contraseña.

¿El login de Ubuntu (GDM) no te pide contraseña? ¿Entras directo?

Saludos.

---

### Post by Carlos C on 2009-05-29
latin0, por favor para la próxima vez publica tu thread en el sub-foro adecuado.

Saludos y espero que tu problema se solucione.

---

