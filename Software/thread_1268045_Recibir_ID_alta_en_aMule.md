---
title: "Recibir ID alta en aMule"
date: 2009-09-16
forum: Software
---

### Post by Gonz@lo on 2009-09-16
Hola, qué tal? Quisiera que me ayudaran con el aMule. Resulta que me dice que recibí ID baja porque estoy tras un cortafuegos o router. Pero no tengo cortafuegos y el del router está desactivado. Qué puedo hacer?

Gracias de antemano.

---

### Post by sergiom99 on 2009-09-16
Gonzalo, te va resultar mas facil y directo consultar la documentacion del amule [http://wiki.amule.org/index.php/Main_Page-es](http://wiki.amule.org/index.php/Main_Page-es)

Saludos/

---

### Post by ramiro_md on 2009-09-16
Buenas, podrías activar el cortafuegos del router y abrir el puerto de aMule. O también fijarte de abrir el puerto en Iptables.
Acá te dejo algo de info sobre de Iptables:
[http://es.wikipedia.org/wiki/Iptables#Firewall_con_iptables]("http://es.wikipedia.org/wiki/Iptables#Firewall_con_iptables")
Un saludo !.

---

### Post by guillermolisi on 2009-09-16
> **Gonz@lo said:**
> Hola, qué tal? Quisiera que me ayudaran con el aMule. Resulta que me dice que recibí ID baja porque estoy tras un cortafuegos o router. Pero no tengo cortafuegos y el del router está desactivado. Qué puedo hacer?

Gracias de antemano.
En Linux el firewall existe siempre porque es parte del kernel.

Normalmente abre solo los puertos que algun servicio de tu maquina necesita usar.
Si alguna programa, como es este caso, necesita de un port TCP/IP abierto exprofeso tenes que abrirlo configurando el firewall (iptables) ya sea con las directivas propias de iptables (consola) o a traves de alguna interface grafica como Firestarter o similares.

---

### Post by Gonz@lo on 2009-09-18
Y me podrían decir cómo desbloqueo los puertos del iptables? Gracias.

---

### Post by dirty fingers on 2009-09-20
gufw

---

