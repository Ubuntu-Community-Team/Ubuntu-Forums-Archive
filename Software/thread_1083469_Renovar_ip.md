---
title: "Renovar ip??"
date: 2009-03-01
forum: Software
---

### Post by erdosain9 on 2009-03-01
Hola.  Qué tal? Quería pedir si alguien puede explicarme cómo hacer para cambiar la ip... tengo ip dinámica... con Fibertel.
Bueno, simplemente eso.
En windows había un archivo bat con el que lo hacía... qué es lo que se hace en Ubuntu???
Saludos y muchas gracias

---

### Post by victor_nesta on 2009-03-01
Tal ves hay formas mas útiles o mas fáciles. (De seguro que las hay)
pero te tiro una para que pruebes

primero, en la terminal, lo siguiente

> sudo dhclient -r

Y cortas la conexión

después borras los registros de tu conexión


> sudo gedit /var/lib/dhcp3/dhclient.leases
y
> sudo gedit /var/lib/dhcp3/dhclient.eth0.leases

borras todo lo que tengan ambos archivos, o haces un buckup como gustes.

y luego reconectas

> sudo dhclient

Teniendo IP dinamica, es muy probable que te asignen otra.


Saludos

---

### Post by erdosain9 on 2009-03-01
mmmm, muchas gracias... pero sigue igual! antes era IP Pública  	190.19.101.197 y luego IP Pública  	190.19.101.197... o sea no cambió nada!!!
Qué más podría hacer???
Saludos, gracias nuevamente!

---

### Post by NickCis on 2009-03-01
Ya hay un post mio sobre esto, donde se da una solucion, te recomiendo usar el buscador antes de abrir un post: [http://ubuntuforums.org/showthread.php?t=1001899](http://ubuntuforums.org/showthread.php?t=1001899)

Bueno la solucion es esta:
1- Instalar el programa dhcpcd 
```
sudo apt-get install dhcpcd
```

2- Ejecutar este comando
```
sudo dhcpcd -k ethX 
```
Donde X es el numero de tu placa de red que tiene conectado el modem. Si tenes una sola placa de red si o si ese numero es 0.

3- Ejecutar este comando
```
sudo dhcpcd -s [Tu numero de ip mas 1] -l -1 ethX
```
Donde X es el numero de tu placa de red que tiene conectado el modem. Si tenes una sola placa de red si o si ese numero es 0.
Tenes que reemplazar los corchetes por tu numero de ip mas uno o cualquier numero de ip VALIDO que no tengas en este momento.

Esto lo ejecutas por consola y cambias de ip.

Esto se puede automatizar haciendo un script:
```
#! /bin/bash
dhcpcd -k ethX & sleep 2s && dhcpcd -s [Numero de Ip] -l -1 ethX
```
Donde X es el numero de tu placa de red que tiene conectado el modem. Si tenes una sola placa de red si o si ese numero es 0.
Tenes que reemplazar los corchetes por tu numero de ip mas uno o cualquier numero de ip VALIDO que no tengas en este momento.

Lo grabas en la carpeta "/usr/bin" con el nombre "cambiarip" (sin comillas), y ejecutas estos comandos:
```
sudo gedit /usr/bin
```
Pegas el contenido, y despues:
```
sudo chmod +x /usr/bin/cambiarip
```
El chmod +x le da permisos de ejecucion.

Ahora cada vez que nececites cambiar ip solo tenes que ejecutar el comando
```
sudo cambiarip
```

Notas: puede ser que despues de un tiempo deje de cambiar la ip, para solucionar esto tenemos que hacer lo siguiente:
```
sudo gedit /usr/bin/cambiarip
```
Y cambiamos la Ip por el numero de tu ip mas 1. Este problema se debe a que vos tenes la misma ip que esa que esta en el archivo, que es la que estas pidiendo.

Fuente: [http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html](http://taringa.net/posts/linux/1645302/Descargar-de-Rapidshare-y-Megaupload---Ubuntu.html)

Saludos.

---

### Post by erdosain9 on 2009-03-01
Hola.  disculpá que no buscara antes... y sí, ya había encontrado el "tema" y seguí los pasos del link de taringa y el cambio de ip ya funciona!!!!! Pero al intentar configurar el jdownloader algo no funca porque no sé hacer esto que dice acá 
"Ahora creamos un "lanzador" o "Enlace a aplicación" en el escritorio, en orden ponemos jdownloader, y en opciones avanzadas (esto es en KUbuntu, no recuerdo como era en Ubuntu) eligen ejecutar como otro usuario y le ponen root. Esto es para que el programa pueda ejecutar sin problemas el cambio de IP, ya que se necesitan permisos de superusuario para realizarlo."

mmm, cómo se hace esto en Ubuntu????

Saludos y gracias nuevamente!

---

### Post by erdosain9 on 2009-03-01
mmmm....... acabo de hacer el lanzador... y cambio en configuración a externa y ahí /usr/bin/cambiarip... Al hacer el test me dice "Reconnect failed!"
Por qué???
quién no tiene permisos???

porque el cambiarip funciona!

Saludos

---

### Post by NickCis on 2009-03-01
Mira, te explico, vos para ejecutar el dhcpcd necececitas ser root, entonces para ejecutar el script cambiarip tenes que ser root tambien, por eso se ejecuta con sudo. El jdownloader, ya que es un programa que lo esta ejecutando un usuario que no tiene derechos de root, no puede ejecutar el script cambiarip.

Una solucion es abrir el jdownloader con sudo o gksudo, asi tiene privilegios de root y puede ejecutar el script.
Si creaste un script que ejecute el jdownloader, lo que podes hacer es (en consola)
```
sudo jdownloader
```
Si te dice qe el programa no existe, o no esta instalado, significa que no creaste ese script. Entonces lo que podes hacer es
```
sudo java -jar [ruta]/JDownloader.jar
```
Donde [ruta] es la ruta donde esta el jdonwloader por ejemplo "/home/andres/JDownloader/", acordate que en linux las mayusculas y minusculas importan en el nombre de la ruta.

Saludos.

---

### Post by sajnox on 2009-03-01
Me parece que hay una opcion mas facil

1) instalar el macchanger

```
sudo apt-get install macchanger
```

2) Desenchufar el modem de fibertel (no standby *desenchufar*)

3) Para la actividad de red
```

sudo /etc/init.d/networking stop
```

4) Cambiar la mac de la placa de red

```
sudo macchanger -r eth0
```

5) Reiniciar la actividad de red

```
sudo /etc/init.d/networking start
```

6) Enchufar el modem y fijarte que tengas un ip distinta

---

### Post by erdosain9 on 2009-03-02
Muchas gracias... lo raro ahora es que al iniciar el jdownloader, 
"sudo jdownloader"... todo funca bien, bajo, etc.  Si cierro el programa y lo vuelvo a iniciar también todo bien... el tema es que al cerrar y reiniciar la máquina al abrir el programa me pide nuevamente idioma, lugar donde se guardará lo que baje, etc... como si se volviera a instalar... y claro todas las cosas que puse a bajar se borran de la lista!!!
 Qué hago???

---

### Post by erdosain9 on 2009-03-03
Incluso me pide las mismas actualizaciones que ya había bajado...¿?¿?¿?¿?

---

### Post by NickCis on 2009-03-03
sajnox el problema de tu respuesta es que nececitas desenchufar el modem, cosa que te impide la automatizacion del trabajo de bajar archivos.

Erdosain9, proba iniciando el Jdownloader con el compiz desactivado (Sistemas/Preferencias/Apariencia/Efectos visuales --- Desactivado)

Saludos.

---

### Post by erdosain9 on 2009-03-04
che no ha cambiado en nada... me sigue pidiendo el idioma, el lugar para bajar los archivos y me avisa de actualizaciones... cada vez que inicio el programa... qué pasa???

---

### Post by NickCis on 2009-03-04
MMM,,, que link usaste para bajar el Jdownloader, proba usando otro link, o sino buscalo en Taringa ([www.taringa.net](www.taringa.net)). Acordate que la version para windows tambien te sirve por que viene con el archivo .jar que es el que estarias ejecutando atraves del Java.

Saludos.

---

### Post by afp_sch on 2010-03-22
> **sajnox said:**
> Me parece que hay una opcion mas facil

1) instalar el macchanger

```
sudo apt-get install macchanger
```2) Desenchufar el modem de fibertel (no standby *desenchufar*)

3) Para la actividad de red
```

sudo /etc/init.d/networking stop
```4) Cambiar la mac de la placa de red

```
sudo macchanger -r eth0
```5) Reiniciar la actividad de red

```
sudo /etc/init.d/networking start
```6) Enchufar el modem y fijarte que tengas un ip distinta

Hola,

no he logrado renovar ip.

Aqui esta lo que hice:

$ **sudo /etc/init.d/networking stop**
 * Deconfiguring network interfaces...                                                                                                    [ OK ] **$ sudo macchanger -r eth0**
Current MAC: 8e:d0:9e:5c:b8:4a (unknown)
Faked MAC:   f6:07:bf:3e:fd:45 (unknown)
**$ sudo /etc/init.d/networking start**
 * Configuring network interfaces...                                                                                                                         WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.


y nada tengo la misma ip.

Alguna idea??

Gracias!!!


**NOTA:** Pruebo con el moden directo al pc y dspues pruebo con un routewr conectado al modem.

---

### Post by afp_sch on 2010-03-22
Hola,

reinicié el pc y el modem sin router.

seguí tus pasos y listo...
...mil gracias.

Lo unico que hice diferente s que despues de:

sudo /etc/init.d/networking start

coloco 
sudo /etc/init.d/networking restart

Nuevamente mil gracias!!!

---

