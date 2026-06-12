---
title: "Navegación en internet muy lenta :|"
date: 2009-08-21
forum: Software
---

### Post by ramiro_md on 2009-08-21
Buenas, resulta que hace unos días formatee y reinstalé Debian Lenny (sé que no es un foro de Debian, para ya estoy a gusto con la comunidad xD).
EL tema es que internet me va bastante lento a pesar de tener un servicio de 3 mb, lo más triste es que en XP me va a las chapas :S.
Estuve buscando en google algunos tips para optimizar el rendimiento de internet pero no encontré más que esos tutos para optimizar los navegadores (que por cierto uso iceweasel 3.0). Realicé algunos de esos tips pero no ha cambiado mucho (por no decir nada).
No sé si será el navegador o qué, por eso busco la opinión o los consejos de los usuarios del foro.
Desde ya muchas gracias !.
Un saludo.

---

### Post by guillermolisi on 2009-08-22
> **ramiro_md said:**
> Buenas, resulta que hace unos días formatee y reinstalé Debian Lenny (sé que no es un foro de Debian, para ya estoy a gusto con la comunidad xD).
.....................
Desde ya muchas gracias !.
Un saludo.
Es es una de las grandes diferencias entre una comunidad y otra.

A veces las cosas mas importantes no pasan por la tecnologia. De hecho, todos los desarrollos y avances que se logran tienen como objetivo principal a la gente (a pesar de que muchas personas olivdan este fundamental aspecto).

Yendo al semi inespecifico tema y siendo que bajo Windows funciona rapido, todo pareceria indicar que el problema lo tenes con el driver de la placa de red o algun otro componente (alguna regla de iptables, bind/dns, dhcp, etc.) relacionado con red, TCP, etc.

---

### Post by Hei Ku on 2009-08-22
hasta ahora todos los temas que vi de este tipo resultaron ser problemas de ISP o de *cof* *cof* usuario *cof* *cof*

Estas seguro que tu placa esta configurada igual? No estuviste tocando nada?

---

### Post by ramiro_md on 2009-08-22
Gracias por las respuestas, sinceramente no toque nada porque no he tenido tiempo jeje. 
A lo mejor debe haber algo mal configurado, porque mi hermana usa ubuntu 9.04 en su laptop y le anda bien internet :/.
Bueno si alguno me podría dar algunas ideas para que vaya viendo, aunque ahora ya tengo en mente ver el tema de la placa como comentaba guille. Y con Iptables ni idea porque no he tocado xD

Un saludo y gracias, seguiré esperando data !! :)

---

### Post by ramiro_md on 2009-08-22
Sigo buascando y buscando solución ala lentitud de internet y encontré muchos blogs que hablan de desactivar el ipv6...pero no quiero tocar nada sin consultar antes con la gente que sabe jeje..es seguro eso ?..será por ahí que vendrá el problema ?

---

### Post by gmunioz on 2009-08-22
Hola ram...:

Prueba lo siguiente:

a) Pulsa el botón derecho del mouse en el icono de red en la barra
   superior a la derecha.

b) Elige editar las conexiones.

c) En la ventana emergente que se abre, titulada conexiones de red,
   ilumina tu conexión.

d) En la nueva ventana emergente, titulada Editando Auto etho, 
   pulsa en la pestaña Ajustes de IPv4 Settings.

e) Dentro de Ajustes de IPv4, cambia en Metodo de Automatico (DHCP)
   a solo direcciones.

f) Pon en Servidores DNS Servers: 
   
   208.67.222.222, 208.67.220.220
   
g) Pulsa aplicar, y cierra todas las ventanas.

h)Pulsa Aplicaciones - Accesorios - Terminal, en la consola 
que se abre ejecuta las ordenes, escribiendolas y dando enter.

     [HTML]sudo cp /etc/resolv.conf /etc/resolv.conf.auto

sudo gedit /etc/dhcp3/dhclient.conf[/HTML]

i) En el archivo que se abre coloca al final la siguiente 
   línea:

   [HTML] prepend domain-name-servers 208.67.222.222,208.67.220.220;[/HTML]

j) Guarda el archivo, cierra gedit y ejecuta en la consola:
    
 [HTML] sudo ifdown eth0 && sudo ifup eth0 [/HTML]

**Si tu tarjeta de red no es eth0, cambia eth0 por la que corresponde a tu tarjeta. **  

Ya tendría que funcionar tu conexión a velocidad normal.

---

