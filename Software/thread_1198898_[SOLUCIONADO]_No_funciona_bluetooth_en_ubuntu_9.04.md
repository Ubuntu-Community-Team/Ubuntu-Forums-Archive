---
title: "[SOLUCIONADO] No funciona bluetooth en ubuntu 9.04, Dellxpsm1730"
date: 2009-06-28
forum: Software
---

### Post by flakojaime on 2009-06-28
Hola.

Bueno, tengo instalado Ubuntu 9.04 en mi dell 1730 y no he logrado que me detecte dispositivos bluetooth.

Tengo instalado bluez 1.8 y el paquete para compartir archivos por bluetooth.

El led indicador del notebook está encendido y cuando trato de conectar dispositivos, no me sala nada en la lista del gestor.

Lo he intentado con un celular nokia, un samsung y un audifono bluetooth dell.

Busque por el google y no encontre solucion.

Saludos.:popcorn:

---

### Post by CdK1 on 2009-06-28
Te recomiendo que uses **bluez-gnome y **[B]gnome-bluetooth;

[/B]Que te tira el comando:

sudo hciconfig ?

---

### Post by flakojaime on 2009-06-28
Hola, 

tengo instalado los dos paquetes y el comando hciconfig no me sale nada en la consola.

Tengo encendido el led de funcionamiento de bluetooth en el notebook, pero no puedo ver ningun dispositivo, ni puedo detectar el notebook.



saludos

---

### Post by CdK1 on 2009-06-28
Ese comando es parte del package "Bluez", te recomiendo que lo reinstales...

---

### Post by moreback on 2009-06-28
El comando hciconfig entrega información sólo cuando el dispositivo está habilitado. A mi me aparece sólo cuando tengo habilitado el botón del wireless, por lo que tengo dudas respecto de si tu notebook trae bluetooth.

Con el switch habilitado me sale este dispositivo con **lsusb**:

Bus 003 Device 019: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth

¿Tienes alguno similar?

---

### Post by flakojaime on 2009-06-28
> **moreback said:**
> El comando hciconfig entrega información sólo cuando el dispositivo está habilitado. A mi me aparece sólo cuando tengo habilitado el botón del wireless, por lo que tengo dudas respecto de si tu notebook trae bluetooth.

Con el switch habilitado me sale este dispositivo con **lsusb**:

Bus 003 Device 019: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth

¿Tienes alguno similar?

Hola.

Es el mismo que tengo yo ademas,tengo el dispositivo conectado, (esta debajo de la bateria) y me funcionaba muy bien con windows, de hecho actualice mi nokia n95 asi.

Tengo el sw encendido del bluetooth en el notebook , es el mismo que activa el wireless
.
El comando lsusb
Bus 006 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c251 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8105 Dell Computer Corp. U2 in HID - Driver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

El comando **dmesg | grep Bluetooth**
[    0.660006] Bluetooth: Core ver 2.13
[    0.660017] Bluetooth: HCI device and connection manager initialized
[    0.660017] Bluetooth: HCI socket layer initialized
[    3.511703] Bluetooth: L2CAP ver 2.11
[    3.511705] Bluetooth: L2CAP socket layer initialized
[    3.511707] Bluetooth: SCO (Voice Link) ver 0.6
[    3.511709] Bluetooth: SCO socket layer initialized
[    3.511738] Bluetooth: RFCOMM socket layer initialized
[    3.511744] Bluetooth: RFCOMM TTY layer initialized
[    3.511745] Bluetooth: RFCOMM ver 1.10
[   19.228733] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.228736] Bluetooth: BNEP filters: protocol multicast

Como les digo, el bluetooth funcionaba muy bien en windows.

Intentare desconectar y conectar fisicamente el dispositivo.

Gracias!

---

### Post by flakojaime on 2009-06-28
Hola.

Reinstale BLuez y Gnome-bluetooth, Desconecte y volvi a conectar el modulo bluetooth.

Reinicie y no funciona.

Me falta algo?

Saludos

**_Edit 1:_**

Puaj!!!

Por lo que he estado leyendo, debo activar el bluetooth en windows para que funcione en linux.

No quiero windows.... sigo buscando otra solucion.

Saludos..

---

### Post by moreback on 2009-06-29
La verdad es que no sé que tienes, yo acabo de probar mi Bluetooth y funciona perfectamente, puede detectar mi celular y éste al computador sin ningún problema.

Por lo que veo en tu lsusb no aparece níngun dispositivo Bluetooth y en el listado de dmesg tampoco aparece la indicación de que carga el driver, esto me sale a mí:

```
 [14391.583057] Bluetooth: Generic Bluetooth USB driver ver 0.3
```Da la impresión que tu dispositivo no estuviera habilitado en la BIOS, ¿revisaste ahí?

Saludos.

---

### Post by flakojaime on 2009-06-29
HOla.

Tambien revise el dispositivo bluetooth en la bios, y está habilitado.

Sospecho que el adaptador bluetooth murio.

saludos.

---

### Post by moreback on 2009-06-30
Entonces no queda otra que lo pruebes en Windows.

---

### Post by flakojaime on 2009-06-30
Puaj!!:mad:

Prefiero comprar un bluetooth externo y despues cambiar el interno.

Les aviso cualquier cosa.

Muchas Gracias!

---

### Post by moreback on 2009-06-30
> **flakojaime said:**
> **Puaj!!**:mad:

Prefiero comprar un bluetooth externo y despues cambiar el interno.
Meh! no le veo lo asqueroso en probar si el bluetooth funciona con Windows, es mucho más práctico que andar gastando plata en comprar hardware.

(Obviamente lo anterior sólo si tienes Windows instalado).

---

### Post by flakojaime on 2009-06-30
Bueno, 

Sería una buena opción, pero tendría que volver a instalar windows, volver a instalar todos los controladores.

¿mataria al grub si instalo windows otra vez?

Gracias!

---

### Post by Carlos C on 2009-06-30
Sí, pierdes el grub. Además de que debes tener windows en la primera partición del disco. Recuperar el grub no es tan difícil, hay más de una forma:

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

---

### Post by flakojaime on 2009-07-03
Hola.

Un dato: Instale un adaptador bluetooth externo Dell (que venia con un teclado y un raton bluetooth junto con el notebook) en un puerto usb, y me reconoció el dispositivo.

Me inclino porque el bluetooth interno este malo??

Gracias

jaime

PD: No he instalado el windows todavia, no he tenido tiempo.

---

### Post by Carlos C on 2009-07-04
Difícil saberlo, son dispositivos diferentes.

Si no quieres perder tus configuraciones, archivos personales y tu grub, es decir, si lo único que deseas es probar windows para verificar tu bluetooth y luego restaurar tu sistema tal y como estaba antes, te sugiero que hagas una imagen de tu partición. El programa que uso para esos casos es clonezilla, te lo recomiendo. Puedes hacer un respaldo del disco completo o de las particiones que quieras, hacer todos los cambios que desees y luego restaurar todo en no más de 15 minutos. Por supuesto, necesitas tener una partición aparte o un disco externo en donde dejar el respaldo:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by flakojaime on 2009-07-05
Ok.

Ahora estoy bajando el ISO del programa para hacer la copia de respaldo y luego volver a instalar windows.

Otra consulta:
El notebook tiene 2 discos duros, si instalo windows en el segundo disco (en el primero tengo instalado Ubuntu), igual me dara problemas?

Gracias

---

### Post by Carlos C on 2009-07-05
Supongo que no, ya que el problema se da cuando windows borra la información del sector de arranque. En caso de instalarlo en el segundo disco eso no debiera ocurrir. De todas maneras ojalá alguien que lo haya hecho te pueda confirmar lo que te digo.

---

### Post by flakojaime on 2009-07-07
HOla.
 
Bueno, al final volvi a instalar windows para salir de la duda.
 
No  me reconocio el dispositivo bluetooth, asi que asumo que se murio.
 
Lamantablemente no pude recuperar con el clonezilla la imagen del disco, me hace todo el proceso de recuperacion, pero cuando inicio me sale un error.
 
Solucion: Comprar adaptador bluetooth interno y volver a instalar Ubuntu 9.04.
 
 
Gracias por todo!

---

### Post by flakojaime on 2009-07-21
Hola otra vez

BUeno, los retroalimento para que se cierre el post.

1.- Reinstale ubuntu y configure todo denuevo.
2.- No funciono el modulo bluetooth interno, pero si uno externo USB que le instalé.
3.- Cambie el modulo bluetooth interno (estaba malo al final) y ahora esta todo de maravilla, incluso funciona perfectamente el bloqueo por bluetooth (BLueproximity).

Fin de todo

Gracias por la ayuda!

---

