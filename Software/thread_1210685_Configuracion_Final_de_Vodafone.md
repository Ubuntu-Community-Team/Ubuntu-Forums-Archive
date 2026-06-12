---
title: "Configuracion Final de Vodafone"
date: 2009-07-11
forum: Software
---

### Post by Pottian on 2009-07-11
Ya esta instalado el USB y el software Vodafone , cuando lanzo el software me sale esto y hay quede pegado... 
En TIPO DE DISPOSITIVO me sale SERIAL
No esta en /media como dispositivo .... 
de antemano gracias ... 

[IMG]http://img401.imageshack.us/img401/7321/pantallazofje.png[/IMG]

---

### Post by moreback on 2009-07-16
Los dispositivos seriales que se usan son generalmente /dev/ttyUSB0 o /dev/ttyACM0, Network-Manager los reconoce bien. En /media sólo deberías tener alguna microSD si es que tu modem trae una.

Lo otro que puede ser es que el usb_modeswitch te esté cambiando el dispositivo. ¿cómo configuraste esta aplicación?

Saludos.

---

