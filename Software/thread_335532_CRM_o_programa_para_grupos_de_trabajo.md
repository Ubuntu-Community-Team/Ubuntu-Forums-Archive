---
title: "CRM o programa para grupos de trabajo"
date: 2007-01-10
forum: Software
---

### Post by waj on 2007-01-10
Buenas,    alguien tiene experiencia sobre CRM, que pueda instalarse en ubuntu, que contenga, correo (imap seria ideal)tareas, contactos, seguimiento, agenda, y demas,
ahora estan usnado ACT(es pago y corre sobre windows), pero la idea es reemplazarlo.
intente con egruopuware, pero no logre que funcione bien.-
Saludos y gracias.-

---

### Post by marianom on 2007-01-10
Casualmente hablabamos de Zope ayer. Fijate esto: [http://wiki.erp5.org/](http://wiki.erp5.org/)
Se ve que tienen una demo y todo.

---

### Post by Oktubre on 2007-01-10
Este es muy bueno, y funciona sobre Linux: [http://www.sugarcrm.com/crm/](http://www.sugarcrm.com/crm/)

---

### Post by euzkoarima on 2007-01-12
> **Oktubre said:**
> Este es muy bueno, y funciona sobre Linux: [http://www.sugarcrm.com/crm/](http://www.sugarcrm.com/crm/)

Ese es el que instale en la oficina (la primer cosa que instale en linux en toda mi vida) y nunca dio problemas. Los que lo usan estan contentos con las prestaciones que da.

---

### Post by marianom on 2007-01-13
Para el que no lo sepa yo soy fanatico absoluto de Oracle así que teniendo en cuenta el tema del thread no puedo dejar de señalarles que Oracle ha liberado varias aplicaciones que pueden instalarse y usarse sin costo: [http://www.oracle.com/technology/products/database/application_express/packaged_apps/packaged_apps.html](http://www.oracle.com/technology/products/database/application_express/packaged_apps/packaged_apps.html)
No estoy seguro si alguna de ellas cubre plenamente las necesidades acá planteadas pero traen varias cosas interesantes.
Además de ellos, hay una versión gratis de oracle (oracle express edition) que pueden instalar y usar (solo hasta 4 gigas de datos, no es mucho pero...) sin costo.

---

### Post by afulloa on 2008-12-15
No soy nuevo en temas de instlación de cosas raras pero el ERP5 sólo he conseguido que funciones desde el LiveCD, y voy que ardo. Intentando instalarlo en la versión de Ubunto 8.10, me salió rana, con eror en la instalación del modulo zope-erp5-sandbox, y haí se quedo. Re-instale un par de veces y peor. 
Podrías darme el "secreto" de com instalarlo.

---

### Post by mhoyos on 2008-12-15
buenas..

si lo que necesitas es "correo (imap seria ideal)tareas, contactos, seguimiento, agenda, y demas" (demas que ??).. tenes zimbra:

[http://www.zimbra.com/](http://www.zimbra.com/)

lo he usado e implementado en una empresa, y anda de maravillas.. :)

te lo recomiendo como otra opcion, para que tengas en cuenta..

salu2

---

### Post by Hei Ku on 2008-12-15
> **afulloa said:**
> No soy nuevo en temas de instlación de cosas raras pero el ERP5 sólo he conseguido que funciones desde el LiveCD, y voy que ardo. Intentando instalarlo en la versión de Ubunto 8.10, me salió rana, con eror en la instalación del modulo zope-erp5-sandbox, y haí se quedo. Re-instale un par de veces y peor. 
Podrías darme el "secreto" de com instalarlo.


Podrías poner en detalle qué errores te dió y qué pasos hiciste para instalarlo?

---

### Post by z37a on 2008-12-15
> **mhoyos said:**
> buenas..

si lo que necesitas es "correo (imap seria ideal)tareas, contactos, seguimiento, agenda, y demas" (demas que ??).. tenes zimbra:

[http://www.zimbra.com/](http://www.zimbra.com/)

lo he usado e implementado en una empresa, y anda de maravillas.. :)

te lo recomiendo como otra opcion, para que tengas en cuenta..

salu2

Otro mas que te recomienda Zimbra, aparte si queres aumentar la infraestructura con zimbra podes, pro que tenes todo gratis, menos el conector de outlook, y el conectos con blackberry, peor nadie te lo da gratis y con zimbra solo pagas pro eso!!!!

---

### Post by afulloa on 2008-12-17
antes de nada gracias por ayudarme.
Comence la instalación desde el vinculo que tiene ERP5.org en download, seleccione la pagina "DownloadApt is the way for Ubuntu, Debian users and developers to setup a erp5 sandbox. (external resource)". y de ahí a la página [http://www.raskon.org/trac/erp5/wiki/Erp5Ubuntu](http://www.raskon.org/trac/erp5/wiki/Erp5Ubuntu). Aqui rode los scripts que vienen en la misma para la version 8.10, por último rode el script:
sudo apt-get update
y al terminar, viendo que no hacia nada pulse el vínculo del punto 5:
5. You can now install ERP5 by clicking this link .

Se instalo el Zope, mySQL y me dío erro en el zope-erp5-sandbox y el zope-erpr5-night.
La página zope funciono en el puerto 8028? creo y una en el 8032? si no me falla la memoria.
Como ví que no funcionaba el ERP5 decidí desintalar todo y realizarlo de nuevo, y ahora tengo una empanada de instalación con el Zope 2.8 del erp5 Zope 3 y ninguna se activa o funciona.
En fín un lio de cuidado, que antes de seguir liando que es lo que puedeo hacer mejor para poder instalar y ver si el ERP5 puede solucionarme algo de gestión de producción.


Saludos
Inataló l

---

