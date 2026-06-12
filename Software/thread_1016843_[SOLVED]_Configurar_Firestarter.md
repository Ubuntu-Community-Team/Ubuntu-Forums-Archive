---
title: "[SOLVED] Configurar Firestarter"
date: 2008-12-20
forum: Software
---

### Post by Josecanalla on 2008-12-20
Hola, estoy desde la notebook. Me conecto a internet de forma inalámbrica. Configuré el firestarter con Wlan pero cuando lo abro dice que no ha podido arrancar el cortafuegos porque el dispositivo wlan0 no está preparado.

¿Qué puedo hacer?

---

### Post by Hei Ku on 2008-12-20
Buscar en threads anteriores sobre firestarter donde dimos la solucion a ese problema.

---

### Post by guillermolisi on 2008-12-21
> **Josecanalla said:**
> Hola, estoy desde la notebook. Me conecto a internet de forma inalámbrica. Configuré el firestarter con Wlan pero cuando lo abro dice que no ha podido arrancar el cortafuegos porque el dispositivo wlan0 no está preparado.

¿Qué puedo hacer?
Ademas del consejo de Hei Ku fijate si tenes instalados los paquetes necesarios y suficientes como para Firestarter funcione correctamente. Estos son bind9 y dhcp (client).

---

### Post by Josecanalla on 2008-12-21
Gracias a ambos.

El dhcp client lo tenía ya, pero el bind9 no. Lo instalé, pero todo sigue igual...

---

### Post by guillermolisi on 2008-12-21
> **Josecanalla said:**
> Gracias a ambos.

El dhcp client lo tenía ya, pero el bind9 no. Lo instalé, pero todo sigue igual...
Cuando iniciaste por primera vez Firestarter ya tenias la red inalambrica funcionando ?
Si no fue asi, es decir configuraste por primera vez Firestarter antes de poner en marcha la red inalambrica, solo deberias volver a correr el wizard de configuracion (menu Firewall - Run Wizard) y ver si te reconoce la placa inalambrica como una de las alternativas para conectarte a Internet. Si tenes mas de una placa, deberia ofrecerte que elijas por cual de las dos te conectas a Internet.

Esto con la conexion WiFi funcionando.

Conta como te resulto.

---

### Post by Hei Ku on 2008-12-22
Hay varios threads donde se explica cómo modificar el firestarter.sh para que funcione bien con el Ubuntu en español. A eso me refería en mi post anterior.

Por ejemplo:
[http://ubuntuforums.org/showthread.php?t=1006277&p=6338478](http://ubuntuforums.org/showthread.php?t=1006277&p=6338478)

---

### Post by Josecanalla on 2008-12-22
Si, al final ayer busqué como decía Hei Ku y encontré para modificar el archivo y agregarle un tilde a un "mas". Y todo funcionó correctamente.

Gracias.

---

### Post by Hei Ku on 2008-12-22
Una vez resuelta tu consulta, vas al menu Thread Tools, y apretas en "Mark this thread as Solved". 
Yo en esta lo hice por vos, para la próxima, ya sabes. ;)
Gracias!

---

