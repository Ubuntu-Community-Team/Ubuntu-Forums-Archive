---
title: "bluetooth llavero no anda ayuda por favor"
date: 2008-09-13
forum: Software
---

### Post by churrolakra on 2008-09-13
tengo un llavero bluetooth esos usb (broadcom usb dongle).. en windows me anda con el driver widcomm y anda joya.. quiero hacerlo andar en ubuntu y no puedo..
seugi todas las guias que encontre.. baje el bluez y todas las cosas que hay que bajar pero no lo levanta..
en el hciconfig me tira esto

lakra@lakra-desktop:~$ hciconfig
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:30 acl:0 sco:0 events:5 errors:0
	TX bytes:21 acl:0 sco:0 commands:8 errors:0

lsusb me tira esto..

lakra@lakra-desktop:~$ lsusb
Bus 002 Device 002: ID 0ac8:0323 Z-Star Microelectronics Corp. Luxya WC-1200 USB 2.0 Webcam
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 005: ID 0a5c:2100 Broadcom Corp. 
Bus 001 Device 004: ID 0079:0011  
Bus 001 Device 003: ID 0079:0006  
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

ya no se que hacer para que lo reconozca.. le agradeceria de corazon al que me pueda dar una mano..

---

### Post by llove on 2008-09-13
calculo que ya habras probado, pero por las dudas...
hciconfig hci0 up

---

### Post by churrolakra on 2008-09-14
al poner  sudo hciconfig hci0 up
me dice lo siguiente
"Can't init device hci0: Device or resource busy (16)"
estoy kada dia mas desesperado :/

---

### Post by fmsismo on 2008-09-16
Yo tengo el mismo problema que vos en hardy.  Pero en intrepid estaba solucionado.

Quemate la ultima versión de intrepid y proba con eso.

Yo usando el kernel del hardy pero sobre intrepid (necesitaba el vmware andando y no soporta el kernel de intrepid.  no podía compilar los módulos de vmware), logre hacer funcionar el mío.

Si tu caso es el mismo, tenes que esperar un poco más y actualizar tu equió en 1 mes y chirola.

Abrazo.

---

