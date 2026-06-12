---
title: "conectar notebook ubuntu 10.04 y pc win7 con cable cruzado"
date: 2010-07-12
forum: Software
---

### Post by 3nG3ndR0 on 2010-07-12
hola soy un usuario de ubuntu casi 2 años pero no experto, solo novato, pero hay algo que nunca e podido hacer es conectar mi notebook mediante un cable cruzado a mi pc con win.

este procedimiento lo se hacer solo de win a win con el cable cruzado y si me funciona al 100%, y lo que yo quiero es usar en mi notebook solo con ubuntu.

alguien podría ayudarme a configurar este procediemto para poder compartir archivos de ubuntu a win, como win a ubuntu.

mi notebook tiene ubuntu 10.04 y mi pc win7

---

### Post by themasterdark on 2010-07-12
quizas esto te sirva =)

[http://www.forosdelweb.com/f41/conectar-ubuntu-por-cable-cruzado-windows-773069/](http://www.forosdelweb.com/f41/conectar-ubuntu-por-cable-cruzado-windows-773069/)

y esto:

[http://humbertofp.wordpress.com/2007/10/29/conectar-dos-equipos-en-red-en-windows-xp-y-ubuntu/](http://humbertofp.wordpress.com/2007/10/29/conectar-dos-equipos-en-red-en-windows-xp-y-ubuntu/)

Saludos =)

---

### Post by Lutho on 2010-07-17
Este texto fue extraido de un post.
del sitio web taringa.net
---------------------------------

PLACA WIFI CONCTADA A INTERNET---->MI PC CON UBUNTU----->PLACA DE RED RJ45 CON CABLE CRUZADO DE---->MI PC CON UBUNTU-------> A PC CON WINDOWS XP 

1) Instalar el Firestarter en el Ubuntu, (no voy a dar muchos detalles de como instalarlo ya q es una boludes... solo usar el Gestor de Paquetes Synaptic o el apt-get....) 
2) Instalar el dhcp3-server 
3) Ejecutar como root el Firestarter, configurar q placa usa internet, y cual es la q va a compartirla...(en mi caso WAN0 q es la inalambrica primero, y la eth0 para compartir)... 
4) abrimos una terminal poniendo: ifconfig para ver q numero de ip esta asignada para la placa eth0.. (en mi caso 10.42.43.1) 
5) Vamos a la PC q tiene windows XP y configuramos las propiedades de TCP/IP: Tildamos Asignacion de ip automatica por DHCP.... aplicamos..., y configuramos manualmente los DNS, solo el primero.. con la direccion q recibe la placa de red inalambrica de ubuntu... (la q ya nombre antes q tenia la dir 192.168.1.101 en mi caso) 

salu2!... espero les sirva, no pongo imagenes, xq no valen la pena. 

--------------------------------------

Espero que te sirva o que ayude en algo  

Saludos!

---

### Post by 3nG3ndR0 on 2010-09-23
Solucionado, al fin contento ahora borrare la partición de winbugs en mi notebook, lo solucione de la siguiente manera.

Ubuntu:

1.- Click derecho sobre el **icono de red** e elegir **editar las conexiones...**
2.- En la pestaña de **Cableada** marcar **Auto eth0** y pulsamos el botón **Editar**
3.- Vamos a la pestaña **Ajustes de IPv4** y en el **Método** seleccionamos **Manual**
4.- En Direcciones agregamos:

    Dirección    Mascara de Red
    192.168.1.1  255.255.255.0

la puerta de enlace la deje en blanco y **Aplicar**
5.- Abrir una consola y ejecuta el comando: sudo /etc/init.d/networking restart, para reiniciar la interface.

Windows:

debemos tener la ip 192.168.1.2

---

