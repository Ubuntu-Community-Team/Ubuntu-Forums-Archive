---
title: "Ayuda con Ubuntu 10.04 y Virtualbox"
date: 2011-01-12
forum: Software
---

### Post by Lobo_Gris on 2011-01-12
Buenas,

Primero gracias por leer esto.
Ahora vamos al tema, tengo instalado 10.04 (Desktop), y Virtualbox con diversos sistemas dentro (ArchHurd, Debian 5, TurnkeyLinux) para diversos desarrollos.
Lo que necesito saber es que y como configurar, o instalar para que cuando trabajo en mis desarrollos web dentro de los servidores virtualizados que tengo, al teclear una dirección ([www.loquesemeocurra.algo](www.loquesemeocurra.algo)) el Ubuntu le diga al navegador que busque esa dirección en la dirección dinamica asignada por el virtualbox (Esto es por que suelo trabajar con y sin conexion a internet)

Desde ya, nuevamente, muchas gracias.
Espero que se haya entendido mi duda.
Saludos.

---

### Post by hectorivand on 2011-01-12
Te diria que le pongas una dirección IP fija, que este en el rango obvio, a cada una de las maquinas. 

De última instálate un servidor DNS y anda agregando cada host manualmente.

para que te quede [http://desarrollo1](http://desarrollo1) ---> 192.168.1.35 por ejemplo y no tengas que andas recordando direcciones IP.

Por ahí alguien que tenga más clara el tema de infraestructura en Ubuntu o Ubuntu Server te puede dar que paquete instalar y como configurarlo.

Saludos
Nacho

---

### Post by biale on 2011-01-13
El primer punto es que la direccion de los servidores deberia ser estatica y encontrarse dentro del rango de la red local

Y luego es facil correlacionar a nivel del cliente "esa" direccion con el nombre [www.loquesemeocurra.algo](www.loquesemeocurra.algo)  Basta con definirla en el archivo del cliente /etc/hosts

No hay inconveniente en instalar un servidor dns (etc), pero vas a terminar haciendo un desarrollo que no hace a tus objetivos.

---

### Post by Lobo_Gris on 2011-01-14
Biale,
Entonces me decís que si pongo en /etc/hosts unas lineas que digan por ejemplo:

192.168.56.101 [www.loquesemeocurra.algo](www.loquesemeocurra.algo) serverVM

ya me traduce el Ubuntu 10.04 [Host] la www a la Ip de la VM ¿Es así?
¿Debo reiniciar algo después de insertar la linea en el archivo?
Ej.: /etc/init.d/networking.

Les dejo otra pregunta.
¿Hay forma desde el host de averiguar por linea de comandos el ip de la VM?
Pienso, por que si es así, puedo escribir algún script para iniciar la VM y que antes me setee la configuracion de /etc/hosts.

Saludos,
Y gracias,
Gonzalo.

---

### Post by biale on 2011-01-14
El servidor virtual tiene definada en VBox la interfase de red en modo bridge (no NAT). Y por dentro la VM tiene la direccion estatica 192.168.56.101, una direccion en tu red local fuera del rango dhcp.

El host puede pinguear la VM:  ping 192.168.56.101
El host invocar al servidor web haciendo   [http://192.168.56.101:80](http://192.168.56.101:80)
nmap muestra la VM y el port  -->  (Una forma de averiguar la IP)

La definicion en /etc/hosts permite hacer la traduccion:

ping loquesea
[http://loquesea](http://loquesea)

En mi caso (Samba/ Nautilus)

smb://RED;Administrador@p28wxp/c$/             en lugar de:
smb://RED;Administrador@192.168.20.44/c$/

Moraleja: lo que vale es la direccion de ip publicada para la red local. El resto es solo una traduccion.

---

### Post by Lobo_Gris on 2011-01-18
Perfecto,
Funciono de 10!
Muchas Gracias,
Ahora solo tengo que investigar un poco para hacer un script que me cambie la ip según trabaje online u offline.

Saludos,
Gonzalo.

---

