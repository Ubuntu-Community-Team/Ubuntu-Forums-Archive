---
title: "Imposible actualizar/instalar Lucid"
date: 2010-04-07
forum: Software
---

### Post by benjamin_linux on 2010-04-07
Hola,

primero que nada los saludo que hace mil años no entro acá.

El asunto es que me decidí a probar Lucid, bajé el Daily Build, lo quemé y se queda en la barra de progreso, por más que quiera ir al instalador o al Live CD. Probé de quemarlo a velocidad mínima y pasa lo mismo. En ambos casos, si compruebo fallos en el disco, se queda en SquashFS.

El tema es que decidí actualizar, actualicé Karmik, me fijé que no hubiese ningún paquete dando vueltas perdido y puse update-manager -d. Toda la noche estuvo actualizándose, termina, reinicio y... se queda en la barra de progreso.

Tengo un Sempron con Nvidia, nunca tuve un problema como este en ninguna versión. Ahora estoy desde el LiveCD de Karmik.

Please help!

PD: Cuando se cuelga tengo que reiniciar manualmente y al hacerlo se ve el error Kernel Panic syncing y algo como... trying to kill init. Al buscar este error y el de SquashFS muchos dicen que es o el CD o el lector o el disco o la memoria. Pero el cd no es porque lo copié varias veces y distintas isos, el disco tampoco porque acabo de instalar Karmik y por la memoria acabo de hacer un memtest y no tengo un solo problema.

---

### Post by alfplayer on 2010-04-09
No entiendo cuál es la relación entre la comprobación de fallos en el disco y SquashFS. No se termina la comprobación de fallos? Está fallando la comprobación de fallos?

---

### Post by benjamin_linux on 2010-04-12
Yo tampoco entiendo. 
Al chequear el CD se quedaba en SquashFS, en 3 CDs distintos copiados a mínima velocidad con isos distintas.
Por otro lado, al actualizar desde Karmik se quedaba en upstart también... volví atrás la actualización, quedó karmik limpio, en el foro internacional sugirieron que probáramos (había otros chicos con este mismo problema) con "nomodeset". A ellos les funcionó, yo ahora ni siquiera puedo actualizar, me dice que tengo paquetes rotos (hice autoremove, autoclean, probé por las dudas un install -f por si había algo dando vuelas y nada, nada). Ya ni sé.

Edit: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/561705?comments=all](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/561705?comments=all), bug 561705, parece que estoy con mala suerte.

---

