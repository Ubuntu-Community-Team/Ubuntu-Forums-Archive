---
title: "Consulta con script al inicio."
date: 2011-01-18
forum: Software
---

### Post by ramiro_md on 2011-01-18
Buenas, estoy usando Ubuntu Server en su versión 10.10.
Y mi idea era que conecte a la red wireless de casa al inicio del sistema. 
Al inicio del sistema, me refiero antes de que me pida login en tty. Aclaro que no estoy usando ningún entorno de escritorio.
Mi script contiene lo siguiente:
> #!/bin/bash
ifconfig wlan0 up;
wpa_supplicant -B -D wext -i wlan0 -c /home/rama/wpa.conf;
dhclient wlan0;
Con permisos con chmod +x para la ejecución. Cuando lo ejecuto una vez realizado el login en Ubuntu Server, el script funciona y me conecta a la res wireless de casa.
Una vez realizada esta prueba lo copié en /etc/init.d y ejecuté:
```
sudo update-rc.d wifiup.sh defaults
```
Cuando reinicio para corroborar su funcionamiento, el sistema arranca lo más normal y no conecta.
También intenté poner los 3 renglones de mi script en /etc/rc.local y tampoco anduvo.
El sistema arranca y no conecta, a menos que me logue y ejecute el script.
Agradecería cualquier consejo.
Un saludo y gracias.

---

### Post by guillermolisi on 2011-01-18
Para lograr lo que queres, tenes que leer sobre runlevels y que servicios se inician en cada uno, de forma tal que puedas habilitar, si es tecnicamente factible, la antena inalambrica en el momento que queres levantar los servicios de red.

[Esto]("http://www.google.com.ar/url?sa=t&source=web&cd=5&ved=0CDsQFjAE&url=http%3A%2F%2Fwww.goitexpert.com%2Flinux%2Frunlevels-daemons-services-in-debain-and-ubuntu-linux%2F&ei=fT02TYnQDoKr8AaG9c2ZCQ&usg=AFQjCNGgZnoW6KIbi6TULAuhgufIajgdBg") pareceria una buena introduccion al tema (en Ingles).

---

### Post by ramiro_md on 2011-01-19
> **guillermolisi said:**
> Para lograr lo que queres, tenes que leer sobre runlevels y que servicios se inician en cada uno, de forma tal que puedas habilitar, si es tecnicamente factible, la antena inalambrica en el momento que queres levantar los servicios de red.

[Esto]("http://www.google.com.ar/url?sa=t&source=web&cd=5&ved=0CDsQFjAE&url=http%3A%2F%2Fwww.goitexpert.com%2Flinux%2Frunlevels-daemons-services-in-debain-and-ubuntu-linux%2F&ei=fT02TYnQDoKr8AaG9c2ZCQ&usg=AFQjCNGgZnoW6KIbi6TULAuhgufIajgdBg") pareceria una buena introduccion al tema (en Ingles).

Guille gracias por la respuesta. En cuanto al enlace que me dejaste, lo que menciona es lo que estoy poniendo en "práctica".
> First, you must copy the startup script for your service into /etc/init.d directory. For example, the following command will install a service called serviceName with default settings.
#update-rc.d serviceName default
Gracias nuevamente, pero sigo en la misma. Probablemente el script no este bien escrito para ejecutar como servicio, ni idea la verdad :(

---

### Post by guillermolisi on 2011-01-19
Ramiro

Un script que se corre al inicio no es un servicio. En todo caso lo que inicie el script puede ser un programa que corre como servicio (o demonio, depende como este configurado).

El parrafo que comentas de ese enlace habla en forma generica sobre cual es la ubicacion de scripts que se ejecuten al inicio pero como vos queres que corra en un momento determinado es necesario saber en cual de los niveles de ejecucion del inicio hay que colocarlo.

Por lo que entiendo, vos queres que los servicios de red inalambrica esten disponibles sin abrir una sesion de usuario, sin que haga falta un login, para lo cual (y a priori) el nivel donde se habilitan las interfaces de red cableadas podria ser el indicado, siempre que en ese nivel el hardware de la antena este listo para ser usado por el sistema.

Buscando info mas especifica di con [esta nota]("http://nixliving.blogspot.com/2010/02/start-your-wireless-connection-on-boot.html"), bastante reciente, que habla de no usar NetworkManager para los servicios de red y dejar configurado todo el entorno de red en /etc/network/interfaces (lo cual me resulta logico y es asi como normalmente se hace en servidores, sin necesidad de scripting adicional para el inicio de los servicios de red).

Aclaracion: La nota habla sobre uso de WEP, asi que deberias modificar el bloque de metodo y protocolo de encripcion junto con la clave que se requiera.
Luego, a mi entender no hace falta remover NetworkManager ya que cuando este inicia deja de administrar las interfaces que ya estan siendolo manualmente (al definirlas en /etc/network/interfaces).

---

### Post by ramiro_md on 2011-01-19
> **guillermolisi said:**
> Ramiro

Un script que se corre al inicio no es un servicio. En todo caso lo que inicie el script puede ser un programa que corre como servicio (o demonio, depende como este configurado).

El parrafo que comentas de ese enlace habla en forma generica sobre cual es la ubicacion de scripts que se ejecuten al inicio pero como vos queres que corra en un momento determinado es necesario saber en cual de los niveles de ejecucion del inicio hay que colocarlo.

Por lo que entiendo, vos queres que los servicios de red inalambrica esten disponibles sin abrir una sesion de usuario, sin que haga falta un login, para lo cual (y a priori) el nivel donde se habilitan las interfaces de red cableadas podria ser el indicado, siempre que en ese nivel el hardware de la antena este listo para ser usado por el sistema.

Buscando info mas especifica di con [esta nota]("http://nixliving.blogspot.com/2010/02/start-your-wireless-connection-on-boot.html"), bastante reciente, que habla de no usar NetworkManager para los servicios de red y dejar configurado todo el entorno de red en /etc/network/interfaces (lo cual me resulta logico y es asi como normalmente se hace en servidores, sin necesidad de scripting adicional para el inicio de los servicios de red).

Guillermo, muchas gracias por la información. Ahora mismo me pongo a leerla atentamente.

---

### Post by ramiro_md on 2011-01-19
> **guillermolisi said:**
> 
Buscando info mas especifica di con [esta nota]("http://nixliving.blogspot.com/2010/02/start-your-wireless-connection-on-boot.html"), bastante reciente, que habla de no usar NetworkManager para los servicios de red y dejar configurado todo el entorno de red en /etc/network/interfaces (lo cual me resulta logico y es asi como normalmente se hace en servidores, sin necesidad de scripting adicional para el inicio de los servicios de red).


Esto me refrescó la memoria, hace tiempo encontré este [artículo]("http://www.vicente-navarro.com/blog/2009/03/01/configurar-wep-y-wpa-en-linea-de-comandos-y-en-el-arranque-en-debian-y-ubuntu/") sobre wireless por consola, y ahí encontré la solución final (configurar como corresponde el /etc/network/interface), que es lo que mencionabas vos guillermo.
Un saludo y muchas gracias.

---

