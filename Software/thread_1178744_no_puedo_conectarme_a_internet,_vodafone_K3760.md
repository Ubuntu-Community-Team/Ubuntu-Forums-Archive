---
title: "no puedo conectarme a internet, vodafone K3760"
date: 2009-06-04
forum: Software
---

### Post by Brodo_bolson on 2009-06-04
Hola, utilizo Ubuntu 9.04 y no puedo hacer funcionar un modem movil que tengo, es un vodafone K3760, no he logrado conectarme a internet desde ubuntu, nosé si alguien me puede ayudar.

de antemano, muchas gracias.

PD: un link con el modelo del modem:   [http://www.entelpcs.cl/modequipos/ficha.iws?id_equipo=49539](http://www.entelpcs.cl/modequipos/ficha.iws?id_equipo=49539)

---

### Post by nopersona on 2009-06-04
Como es un dispositivo usb especifico, no sé si tenga el soporte necesario para funcionar. 

Encontré esto, ojalá te sirva.

[http://pelotil.blogspot.com](http://pelotil.blogspot.com)

---

### Post by augias on 2009-06-04
yo encontre este turorial. si tienes preguntas sobre alguna instruccion, no dudes en preguntar aqui.

[http://www.peck.org.uk/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.peck.org.uk/networkmanager-0.7.0-and-3g-wwan-modems.html)

---

### Post by jdgarrido on 2009-06-14
ese dispositivo no funciona y entel no da soporte para el.
lo intenté con la aplicacion de vodafone, si bien lo reconoce y todo, a la hora de conectarse no pasa nada.
mejor cambia el aparato. los huawei son mejor soportados

---

### Post by tuxsarge on 2009-06-18
hola.. ¿a que te refieres con "lo reconoce y todo"?

osea, logras instalarlo por lo menos?

---

### Post by CdK1 on 2009-06-18
El que busca encuentra, mira este hilo...

[http://ubuntuforums.org/showthread.php?t=1173350](http://ubuntuforums.org/showthread.php?t=1173350)

  	 	 	 	 	 	  VODAFONE MOBILE CONNECT INSTALLATION INSTRUCTIONS.  -------------------------------------------------   * You need a previously working internet connection (e.g: your ethernet one)  * Download from this page these two DEB packages:       - usb-modeswitch      - vodafone-mobile-connect  * Install them, e.g: in a terminal command line (substitute the version and architecture here for the ones you have downloaded)       sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb      sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.deb  * After this step, you will possibly have unresolved dependencies problems. To solve them execute:       sudo apt-get -f install    * If everything has gone fine you can plug in the modem, and execute the driver with:       vodafone-mobile-connect-card-driver-for-linux

---

