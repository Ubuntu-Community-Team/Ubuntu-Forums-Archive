---
title: "Dudas con syslog"
date: 2009-06-22
forum: Software
---

### Post by EnriqueK on 2009-06-22
Uso Ubuntu 9.04 64 bits , se me dió por ver los mensajes que muestra el archivo **gedit /var/log/syslog**, me encuentro que se repiten constantemente estas lineas 
 nullmailer[3946]: Starting delivery: protocol: smtp host: mail. file: 1240605297.29366
 nullmailer[5529]: smtp: Failed: Connect failed
 nullmailer[3946]: Sending failed:  Host not found
 nullmailer[3946]: Delivery complete, 4 message(s) remain.

Estas lineas se repiten constantemente y prácticamente todo el log y todos los logs que quedan de respaldo, al parecer el problema es con **nullmailer **que al parecer es un automatizador de mails que no recuerdo haber habilitado cosa semejante y no se si se puede anular o eliminar.

---

### Post by guillermolisi on 2009-06-22
Nullmailer es un relay de e-mail.

Si pones "nullmailer" en Google tenes una pila de explicaciones, preguntas y respuestas acerca de el.

Vos no lo instalaste pero algun otro programa lo hizo como dependencia necesaria, posiblemente.

No te recomiendo tener funcionando un e-mail relay en tu maquina. Por suerte parece que no tenes habilitado el smtp para que salgan los mensajes (que deben ser spam en su mayoria ya que hay robots que detectan puertos abiertos buscando este tipo de servicios).

---

### Post by EnriqueK on 2009-06-22
OK, entonce lo desinstalo tranquilo, gracias.

---

### Post by guillermolisi on 2009-06-22
> **EnriqueK said:**
> OK, entonce lo desinstalo tranquilo, gracias.
Antes de confirmar su desinstalacion, revisa bien que dependencias posee. No vaya a ser cosa que por quitar esto te quedes con varios paquetes rotos.

---

### Post by EnriqueK on 2009-06-22
Si, lo desinstalé mediante Synaptic y resultó ser un paquete sin dependencias y lo mas importante, se normalizó el syslog.

---

### Post by guillermolisi on 2009-06-23
> **EnriqueK said:**
> Si, lo desinstalé mediante Synaptic y resultó ser un paquete sin dependencias y lo mas importante, se normalizó el syslog.
Salio bien baratito el asunto :)

Si hubieras tenido el motor SMTP funcionando te voltean la maquina con la carga que le darian. Y corrias el riesgo que incluyan el bloque IP dentro del cual esta tu maquina en una spam blacklist.

---

