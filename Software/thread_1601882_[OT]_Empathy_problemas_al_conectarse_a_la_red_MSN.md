---
title: "[OT] Empathy problemas al conectarse a la red MSN"
date: 2010-10-20
forum: Software
---

### Post by hectorivand on 2010-10-20
Hola gente, en el día de la fecha estoy teniendo problemas para conectarme con Empathy a la red MSN, no pasa lo mismo con la aplicación emesene y otras, a alguien más le esta pasando o solo a mi?

Saludos
Nacho

---

### Post by harryscode on 2010-10-20
Somos 2

---

### Post by rsepulvedacl on 2010-10-20
Somos tres. :P

---

### Post by anarko on 2010-10-20
Esto pasa : [https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/663670](https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/663670)
Aparentemente la gente de MS cambio el protocolo o algo.
PD: No prueben la solucion de ahi de modificar el archivo RequestMultipleSecurityTokens.py porque tampoco marcha, baja los contactos pero termina dando un assertion en el python y no conecta. A esperar que saquen el patch.

---

### Post by anarko on 2010-10-21
Me retracto la solucion funciona, solo que falta algo en la explicacion que es ke hay que kiliar el butterfly o reiniciar la pc, con solo cerrar y abrir el emphaty no anda.

Solucion : 
En el archivo  /usr/lib/pymodules/python2.6/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py

Hay que reemplazar la linea que dice : 
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
por: 
CONTACTS = ("contacts.msn.com", "MBI")

El fix es de un tal kakaroto de ahi de la lista del bug.

---

### Post by hectorivand on 2010-10-21
> **anarko said:**
> Me retracto la solucion funciona, solo que falta algo en la explicacion que es ke hay que kiliar el butterfly o reiniciar la pc, con solo cerrar y abrir el emphaty no anda.

Solucion : 
En el archivo  /usr/lib/pymodules/python2.6/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py

Hay que reemplazar la linea que dice : 
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
por: 
CONTACTS = ("contacts.msn.com", "MBI")

El fix es de un tal kakaroto de ahi de la lista del bug.

Justo lo iba a postear :D por unos minutos, confirmo también que lo que puso Anarko funca.

Saludos
Nacho

---

### Post by el_burgues on 2010-10-24
Gracias kakaroto, sos un capo.

---

