---
title: "Difference between aptitude and apt-get?"
date: 2009-10-14
forum: Software
---

### Post by vksingh on 2009-10-14
Hi,

What is the difference between the following commands:

$ apt-get update

$ aptitude update

Thanks,

Vivek

---

### Post by tacantara on 2009-10-14
The apt-get and aptitude commands work basically the same way (as far as the command structure, i.e "sudo apt-get install" and "sudo aptitude install").  The main difference between the two is that aptitude keeps its own log of software installed while also updating the system log, while apt-get only updates the system log for installed software.  Aptitude is better at recommending dependencies for software that you are installing.  Because it tracks those dependencies, it also makes it more effective for removing those dependencies when you uninstall a package.

Basically, you can use either to accomplish package download.  It comes down to personal preference.

---

### Post by SLA_leandrin on 2009-10-14
> **vksingh said:**
> Hi,

What is the difference between the following commands:

$ apt-get update

$ aptitude update

Thanks,

Vivek

Please Vivek, this is a Spanish speaking subforum... you are very welcome here, but try to post in our language.

Thanks.

---

### Post by guillermolisi on 2009-10-14
> **SLA_leandrin said:**
> Please Vivek, this is a Spanish speaking subforum... you are very welcome here, but try to post in our language.

Thanks.
There are too many people here that cannot read and understand English. That's why this subforum is a Spanish speaking one.

---

### Post by tacantara on 2009-10-14
I apologize for not noticing that as well when I replied to the OP.  I am not fluent in Spanish, hence my reply in English.

tac

---

### Post by guillermolisi on 2009-10-17
> **tacantara said:**
> The apt-get and aptitude commands work basically the same way (as far as the command structure, i.e "sudo apt-get install" and "sudo aptitude install").  The main difference between the two is that aptitude keeps its own log of software installed while also updating the system log, while apt-get only updates the system log for installed software.  Aptitude is better at recommending dependencies for software that you are installing.  Because it tracks those dependencies, it also makes it more effective for removing those dependencies when you uninstall a package.

Basically, you can use either to accomplish package download.  It comes down to personal preference.
Traduccion:

Los comandos apt-get y aptitude basicamente trabajan de la misma manera (por lo menos en lo que a estructura se refiere, por ejemplo "sudo apt-get install" y "sudo aptitude install"). La mayor diferencia entre los dos es que aptitude mantiene su propio log de paquetes instalados mientras tambien actualiza el log del sistema. apt-get solo actualiza el log del sistema para paquetes instalados. Aptitude es mejor al momento de recomendar dependencias para paquetes que se instalen. Como lleva registro de esas dependencias, es mas efectivo al momento de desinstalarlas cuando se remueve un paquete.

Basicamente, cualquiera de los dos puede ser utilizado para descargar paquetes. La eleccion recae en preferencias personales.

---

