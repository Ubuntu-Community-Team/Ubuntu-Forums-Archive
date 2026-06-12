---
title: "Modem Huawei e1756 Movistar solicita clave"
date: 2010-12-21
forum: Software
---

### Post by asterix77 on 2010-12-21
He contratado un plan de banda ancha móvil de movistar de 500 megas mensuales. El problema ya sea en network-manager o en una aplicación de betavine que descargué (betavine connection manager), cada vez que intento conectarme me aparece la ventanita del famoso anillo de claves; ingreso la contraseña, y luego me aparece la siguiente ventana en donde vuelve a pedir otra clave.

[http://img690.imageshack.us/img690/3706/pantallazo8f.png](http://img690.imageshack.us/img690/3706/pantallazo8f.png)


He puesto el PIN, he puesto el PUK, he puesto la clave de usuario de Movistar que es simplemente "web", he puesto la clave del anillo, he puesto la clave de superusuario, y ya no hallo que más poner, y no hay caso con este modem.

Otra cosa, mi lsusb es el siguiente:

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 004: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

¿Porqué ubuntu me lo reconoce como E620 y no como E1756?. Acaso será ese el problema?


Otra cosa, wvdial tampoco me funciona, a pesar de que está bien configurado.

Un compañero me prestó su módem entel, lo conecté y ubuntu me lo reconoce en forma correcta, con cualquier método me conecta (wvdial, NM, BCM).


Espero que puedan ayudarme.

---

### Post by bichopro on 2010-12-21
Ve a editar las conexiones y luego a banda ancha mobil con el modem desconectado, borra la configuracion y vuelve a colocarlo. A mi se me soluciono una vez asi

---

### Post by -DRAGON- on 2010-12-21
en la ventana dice "Entel PCS"....... 

seguro q configuraste bien el modem...?? 

ese cuadro q sale es para poner el codigo PIN. 

Desde el programa de que trae el modem (win.. u.u) se puede quitar la opcion para q no pida el codigo PIN cada vez q te conectes... (no c si esto tambien  se puede acer en ubuntu)

pero como dice bichopro ... borralo y parte de nuevo..

---

### Post by asterix77 on 2010-12-21
Bichopro, lo que me comentas lo he hecho varias veces, y sigue apareciendo el mismo aviso.

Dragon, tienes razón, dice entelpcs (no me había dado cuenta de detalle); lo que pasó es que al modem de mi amigo (entelpcs huawei e176) le saqué el chip y lo inserté en el e1756 de movistar y traté de conectarlo. 

Investigando por google encontré que estos modem vienen bloqueados para ser usados en otras compañias, así es que por eso creo que apareció "Entelpcs" en vez de "Movistar" al tratar de conectarme con el chip de entelpcs en el módem de movistar.

Pero el problema es el mismo, aunque trate de conectarme con el módem E1756 de Movistar, me aparece el dichoso aviso.

Por lo menos a habido un avance, ya que al menos en 1 intento de 8 ó 10, he logrado conectarme con el Betavine Connecting Manager. Lo que si cada vez que reinicio el pc, tengo que borrar el perfil anterior, crear un nuevo perfil, y tratar de conectarme varias veces hasta que en una de esas se conecta.


Saludos

---

### Post by -DRAGON- on 2010-12-21
haaaaa... oks

sep.. yo tambien e intentado acer funcionar un chip vomista en un modem entel ... (no funciona)...

lo otro es ver si tienes suficiente señal.. ya q estas cosas son muy sensibles a eso.. 

por ejemplo... si pongo en modem de mi hermana (vomistar) en su notebook si toma la señal... si lo llevo donde esta mi pc la señal se pierde,,, =_=

---

### Post by asterix77 on 2010-12-22
Finalmente he solucionado el problema al parecer. Mi amigo me pasó su modem e176 de entel ya que tenía otro que lo podía usar sin problemas para conectarse con su windows.

Lo que hice fue descargar un programa v4mpire que es para windows, el cual hice correr bajo wine. Lo único que hay que hacer es ejecutarlo, luego el programa te pide el IMEI del modem, tras lo cual te calcula un código de desbloqueo. Después tuve que instalar la BAM (de entelpcs ya que el módem era de esa compañía), a un pc con windows. Todo esto para que windows reconozca el dispositivo como modem; una vez hecho esto cambias el chip de entel por el de movistar en mi caso, ejecutas el programa para conectarte que viene por defecto en estos tipos de módem. Al detectar que tiene un chip de otra compañía, te pide un código de desbloqueo, y es aquí donde ingresas el código obtenido por el v4mpire. De esta forma desbloqueas el módem para ser usado por cualquier proveedor de banda ancha móvil.

Luego obviamente lo conecté a ubuntu para probar, y voila, funcionó de inmediato sin pedir ninguna contraseña de ningún tipo.

He reiniciado mi notebook unas 10 veces, y no me ha fallado la conexión.

Ahora se me ha creado otro problema, creo que fue el fruto de tanto eliminar, instalar,reinstalar y tocar algunos archivos de configuración; y es que en mi hogar no me puedo conectar vía wifi a mi AP, al momento de hacerlo me aparece lo siguiente al hacer un iwconfig.

[http://img841.imageshack.us/img841/2740/pantallazo10d.png](http://img841.imageshack.us/img841/2740/pantallazo10d.png)

Cambia el essid de mi ap por otro ilegible

Creo que no es algo complicado de solucionar en caso de no poder hacerlo, crearé un nuevo post sobre el tema.

Dejo un pantallazo del modem (de entelpcs modelo huawei e176), trabajando con un chip movistar en mi notebook con lucid.

[http://img814.imageshack.us/img814/2618/conexin.png](http://img814.imageshack.us/img814/2618/conexin.png)

Saludos y gracias

---

### Post by gcevallos on 2011-01-12
Como están , soy de Ecuador , me podrían ayudar a instalar un modem huawei E 176 en Ubuntu 10.04 . Me podrían ayudar con los pasos o los paquetes que debo descargar para que funcione. Aquí el otro proveedor ya viene configurado pero Movistar no . Hay algún ecuatoriano que haya hecho funcionar este modem en ubuntu. NO quiero usar XP para navegar.
Me pide APN usuario contraseña red pin 
Bueno necesito lo que se dice un protocolo para conectar este modem aqui en Ecuador

---

### Post by asterix77 on 2011-01-12
Por supuesto que te podemos ayudar.

Revisa el siguiente post y sigue los pasos

[http://ubuntuforums.org/showthread.php?p=10346069#post10346069](http://ubuntuforums.org/showthread.php?p=10346069#post10346069)

Por experiencia te puedo decir que las aplicaciones de betavine en este caso, soportan dicho módem.

No me queda muy claro quien es tu proveedor de banda ancha móvil ¿es movistar?

Si es así los datos son los siguientes:

o APN: internet.movistar.com.ec 
o Username: movistar 
o Password: movistar 

Con respecto al pin, este viene impreso en la tarjeta donde viene el chip.


Saludos y cualquier duda posteala

---

### Post by gralet on 2011-01-30
Hola, soy de México y tengo el Huawei e1756c de Movistar ya instaldo y configurado (ubuntu 10.4 ya traía los valores de Movistar para mi país), sin embargo cuando intento conectarme, simplemente se desconecta, el daemon log registra lo siguiente:
 
Jan 29 19:53:38 sara-juana pppd[2368]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 29 19:53:38 sara-juana pppd[2368]: peer doesn't want to authenticate us with eap
Jan 29 19:53:38 sara-juana pppd[2368]: Connection terminated.
Jan 29 19:53:38 sara-juana NetworkManager: <info> (ttyUSB0): device state change: 7 -> 9 (reason 13)
 
Desactivé eap, pero en ese caso me dice que es requerida por mi peer. Espero me puedan ayudar.

---

