---
title: "Como leer la sim de mi celular?"
date: 2012-10-20
forum: Software
---

### Post by sergioc on 2012-10-20
Hola, quiero entrar a la sim de mi celular para borrar las fotos por que esta repleta y ademas ya se pasaron al dropbox, pero no se como acceder, enchufe el celular a la pc y luego no encuentro como acceder a ese disco..

Desde donde o como hago esto?

Saludos!

---

### Post by guillermolisi on 2012-10-21
Las fotos estan en la SIM o en una tarjeta de memoria adicional ?

---

### Post by sergioc on 2012-10-21
Hola, bueno de celulares no se mucho, yo dije sim solo desde mi ignorancia, es la memoria que me viene por defaut en el teléfono, es un galaxy s, con el so anterior solo iba a mi pc y lo encontraba ahí, acá no se como hacer, en google encontré de tipear **sudo fdisk -l** pero a las opciones que me tira no les encuentro relación con el celular como para elegir una, así que no se si es correcto.

---

### Post by guillermolisi on 2012-10-21
Fijate que se registra en el log /var/log/dmesg cuando conectas el telefono via cable USB (con ingresas dmesg en consola/terminal es suficiente para ver las ultimas lineas del log).

---

### Post by sergioc on 2012-10-21
Ultimas lineas:
[54192.012856] cdc_acm 1-3:4.0: ttyACM0: USB ACM device
[54192.014091] usbcore: registered new interface driver cdc_acm
[54192.014099] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[54193.880300] usb 1-3: USB disconnect, device number 3
[54194.188122] usb 1-3: new high-speed USB device number 4 using ehci_hcd
[54194.325653] cdc_acm 1-3:4.0: This device cannot do calls on its own. It is not a modem.
[54194.325817] cdc_acm 1-3:4.0: ttyACM0: USB ACM device
[54308.860172] usb 1-3: USB disconnect, device number 4
[54326.140114] usb 1-3: new high-speed USB device number 5 using ehci_hcd
[54326.275511] cdc_acm 1-3:4.0: This device cannot do calls on its own. It is not a modem.
[54326.275680] cdc_acm 1-3:4.0: ttyACM0: USB ACM device

asi?

---

### Post by guillermolisi on 2012-10-21
Si. Llamativo que no figure el reconocimiento de la tarjeta.
Con mi Samsung Ace (2.3.4 Gingerbread) obtengo > [164616.004072] usb 2-2: new high-speed USB device number 2 using ehci_hcd
[164616.288992] Initializing USB Mass Storage driver...
[164616.289193] scsi5 : usb-storage 2-2:1.3
[164616.289295] usbcore: registered new interface driver usb-storage
[164616.289297] USB Mass Storage support registered.
[164616.929732] cdc_acm 2-2:1.0: This device cannot do calls on its own. It is not a modem.
[164616.929868] cdc_acm 2-2:1.0: ttyACM0: USB ACM device
[164616.930873] usbcore: registered new interface driver cdc_acm
[164616.930876] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[164617.288948] scsi 5:0:0:0: Direct-Access     SAMSUNG  GT-S5830L Card   0100 PQ: 0 ANSI: 2
[164617.290510] sd 5:0:0:0: Attached scsi generic sg2 type 0
[164617.296055] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[guille@guillenb ~]$ sudo fdisk -l /dev/sdb
que es bien distinto a lo que mostraste.

Tu telefono posee alguna opcion de Mass Storage a traves de Settings - About Phone ? (el mio no)

---

### Post by sergioc on 2012-10-23
No logre hacerlo de esa manera, entre a configuración, y borre el contenido dela tarjeta, pensé que se me borrarían los contactos y juegos de mi hijo también, pero por suerte solo se borro lo de la galería.

Así que solucionado aunque no por el camino correcto, fue como desactivar una bomba, jaja muchas gracias y suerte!

---

