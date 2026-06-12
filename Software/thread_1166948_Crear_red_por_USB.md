---
title: "Crear red por USB"
date: 2009-05-22
forum: Software
---

### Post by Brath-ga on 2009-05-22
Hola de nuevo.

Tengo un cable USB de Conceptronic con el cual se puede formar una red entre dos computadoras en Güindos, pero claro, el driver para hacerlo funcionar no va en Ubuntu.

Todo lo que googleé no me sirve porque es para redes wifi o cable.

Alguien sabe de algún remedio?

Graciñas.

---

### Post by juancarlospaco on 2009-05-22
Anda muy mal realmente, yo compraria un par de plaquitas de Red que es mucho mejor,
inclusive vienen a velocidad de Giga, o Wifi y ni necesitas cables...
No olvidemos que USB es una conexion diseñada para conectar perifericos.
*No creo que ande realmente...*

---

### Post by gmunioz on 2009-05-22
Hola bra....:

Pulsa - Aplicaciones - Accesorios - Terminal

En la consola que se abre ejecuta:

sudo ifconfig eth0 down

sudo modprobe usbnet

sudo ifconfig usb0 *IP-que-asignes* up

Aclaración: 

Esto lo ejecutas en ambas máquinas.

Con el cable conectado

Cambia eth0 por la tarjeta de red que tenga cada una.

Las ips de cada máquina deben ser distintas pero en el mismo rango

Por ejemplo 192.168.1.2 - 192.168.1.3

Saludos.

---

### Post by guillermolisi on 2009-05-22
> **Brath-ga said:**
> Hola de nuevo.

Tengo un cable USB de Conceptronic con el cual se puede formar una red entre dos computadoras en Güindos, pero claro, el driver para hacerlo funcionar no va en Ubuntu.

Todo lo que googleé no me sirve porque es para redes wifi o cable.

Alguien sabe de algún remedio?

Graciñas.
Vos queres usar ese cable o queres conectar dos maquinas que corren Ubuntu independientemente del cable que sea ?

---

### Post by Brath-ga on 2009-05-24
Se trata de conectar un netbook a un sobremesa.
Ya sé que puedo conectarme por wifi, pero si la cantidad de datos que deseo pasar es de varios Gigas, me resulta muy lento.
El tema de conexión en usb iba aceptablemente bien en Windows.
Probaré con Wine si no hay solución en Ubuntu.

---

### Post by guillermolisi on 2009-05-24
> **Brath-ga said:**
> Se trata de conectar un netbook a un sobremesa.
Ya sé que puedo conectarme por wifi, pero si la cantidad de datos que deseo pasar es de varios Gigas, me resulta muy lento.
El tema de conexión en usb iba aceptablemente bien en Windows.
Probaré con Wine si no hay solución en Ubuntu.
Wine ?

Aun con una red cableada a 100Mbps sera lento ?
Por que no probas con un cable de red cruzado ? (o no entendi nada) :D

---

### Post by Brath-ga on 2009-05-25
Realmente equivale a un cable de red cruzado.
Alcanza los 480 Megas por segundo.

---

