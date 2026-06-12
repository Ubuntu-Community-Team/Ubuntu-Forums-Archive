---
title: "A ver lo que puee hacer el dichoso compiz"
date: 2008-06-01
forum: Software
---

### Post by andy_91 on 2008-06-01
alguien sabe como habilitar el dichoso compiz en linux mint Xfce

por lo que se es una vercion de ubuntu 7.10 con mas cosas instaladas

les dejo la captura del icono de la bandeja de sistema(esa si la instale yo)

bueno desde ya gracias

---

### Post by _kAz_ on 2008-06-01
Primero, ya instalaste compiz desde el synaptic o el respectivo para mint???

Tenés que tener instalado además compizconfig setting manager (está en el synaptic). Desde ahí vas a poder habilitar todos los efectos. A mi me pasó que sí tenía compiz pero como no tenía de donde "manejarlo" ni enterado.

Una vez que instales eso, te vas a preferencias y en Configuración Avanzada de CompizConfig vas a poder manejarlo a tu antojo.

Salu3.

---

### Post by andy_91 on 2008-06-01
si vino todo instalado de fabrica lo unico que instale yo fue el GL Desktop

---

### Post by _kAz_ on 2008-06-01
Comprobaste si tenes en alguna parte del menú la "Configuración Avanzada de CompizConfig"???

Si no lo tenes cerciorate de que lo tengas instalado en el synaptic (recordá que el paquete se llama compizconfig settings manager). Si está ahí pero no lo ves, apreta Alt+F2 o andá a consola y pone ```
ccsm
```

---

### Post by andy_91 on 2008-06-01
si esta lo qe yo quiero es activarlo???

uso xfce no gnome asi que nose como se activa

---

### Post by santiagoward2000 on 2008-06-01
Hola Andy!
Para prenderlo, abrí una terminal y escribí:
```
compiz
```
Si hay algún problema te va a saltar ahí.
Si anda bien, podés instalar **fusion-icon**.
```
sudo apt-get install fusion-icon
```
Cuando lo abras, te va a aparecer un icono en el panel, que te deja prender y apagar compiz, emerald (si esta instalado) y abrir ccsm.
Suerte!

---

### Post by andy_91 on 2008-06-02
> andy@andy-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/xfwm4 

** (xfwm4:13357): WARNING **: Another Window Manager is already running


me salio eso en la consola alguna idea

---

### Post by jpmorelli on 2008-06-02
Dos opciones:

1) No tenés una placa que sea compatible con XGL ( a partir de una TNT2 MX4000 ya deberías poder sin problemas, incluso con las Intel 810 o superiores )

2) Si tenés pero no cargaste el driver restrictivo. Fijate si no tenés una aplicación llamada "Hardware drivers", o "Controladores de hardware" y no tenés que poner en uso a tu placa de video. Con las Intel no es necesario.

Cualquier cosa chiflá, Suerte !

---

### Post by faktorqm on 2008-06-03
che el comando no era "compiz --replace" o algo por el estilo? salu2!

---

### Post by andy_91 on 2008-06-03
> **jmorelli said:**
> Dos opciones:

1) No tenés una placa que sea compatible con XGL ( a partir de una TNT2 MX4000 ya deberías poder sin problemas, incluso con las Intel 810 o superiores )

2) Si tenés pero no cargaste el driver restrictivo. Fijate si no tenés una aplicación llamada "Hardware drivers", o "Controladores de hardware" y no tenés que poner en uso a tu placa de video. Con las Intel no es necesario.

Cualquier cosa chiflá, Suerte !
 ni idea por eso deje el pantallazo en el post 1, sin embargo me dice que: mi hardware no nesesita drivers privativos

---

### Post by anarko on 2008-06-03
> **faktorqm said:**
> che el comando no era "compiz --replace" o algo por el estilo? salu2!

Si, el comando es compiz --replace

---

