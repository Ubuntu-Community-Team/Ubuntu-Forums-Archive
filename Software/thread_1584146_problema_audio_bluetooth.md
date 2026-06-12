---
title: "problema audio bluetooth"
date: 2010-09-28
forum: Software
---

### Post by asterix77 on 2010-09-28
Hola a todos 

Les comento que tengo un pc de escritorio dual boot con ubuntu 10.04 amd64 y windows 7 (solo lo uso en realidad para consola de juegos je je je).

Bueno mi problema es que no puedo recibir el audio de mi tv a mi pc y usar mi sistema de audio del pc como amplificador, cosa que si puedo hacer con win.

Otra cosa es por ejemplo que no puedo usar los parlantes de mi tv como receptor de audio de mi pc. Mi hija tiene un notebook con win y se conecta por bluetooth al tv para escuchar el sonido de su notebook o a mi pc de escritorio cuando corre windows.

He instalado las utilidaes blueman, bluez, pero no hay caso.

Creo que el error se genera en algún tipo de conexión a dbus, porque cuando ejecuto:

#bluetoothd -nd                       aparece lo siguiente:
bluetoothd[8903]: Bluetooth daemon 4.60
bluetoothd[8903]: Enabling debug information
bluetoothd[8903]: parsing main.conf
bluetoothd[8903]: discovto=0
bluetoothd[8903]: pairto=0
bluetoothd[8903]: pageto=8192
bluetoothd[8903]: name=%h-%d
bluetoothd[8903]: class=0x000100
bluetoothd[8903]: discov_interval=0
bluetoothd[8903]: Key file does not have key 'DeviceID'
bluetoothd[8903]: Unable to get on D-Bus

La lista debería ser más larga, pero se detiene en la última linea.

Si alguien me pudiera orientar con ese problema, se los agradecería.

Me interesaría de sobremanera poder usar mi pc con ubuntu para amplificar el audio de mi tv.


Saludos

---

### Post by josecuervo86 on 2010-09-29
Hola Asterix, mira yo me conecto desde la PC con un Headset Nokia y lo hago desde **blueman** mediante la opción **AudioSynk**. Lo importante es que el televisor sea reconocido como un elemento capaz de recibir audio, por lo que tenes que configurarlo vos cuando haces el apareo.
Una vez que estes en ese modo anda **Sistemas**>**Preferencias**>**Sonido** y en la solapa **Salida** deberia aparecerte la opción de elegirlo como salida en vez de tu placa de sonido.

---

