---
title: "Modificar Particionado Post-Instalación"
date: 2011-04-27
forum: Software
---

### Post by matlnx on 2011-04-27
Buenos días, hace un tiempo vengo utilizando Ubuntu Server para poder hacer monitoreo de mi red. Hace un par de días me surgió la necesidad de poder levantar un Syslog Server en mi ubuntu (v10.10 ue tiene corriendo Nagios y MRTG), pero veo que los archivos de Syslog se almacenan en el directorio /var/log.

Mi duda viene porque como la red es extensa, puede ser que muchos eventos me llenen ese directorio y me claven el sistema, por lo que (y de ahi viene mi duda), necesitaría separar en una nueva partición el directorio /var/log.

Esto me da mas seguridad / confianza, ya que en caso de que se produzcan una gran cantidad de logs que llenen mi disco, no se verá afectado por falta de espacio todo mi sistema.

Por si no quedo claro, el sistema se encuentra productivo y en funcionamiento.

Muchas gracias!!
Saludos cordiales
Matlnx

---

### Post by sanguinoso on 2011-04-27
Ok, mi español es mal pero voy a intentar. Como grande es su disco?

---

### Post by matlnx on 2011-04-27
> **sanguinoso said:**
> Ok, mi español es mal pero voy a intentar. Como grande es su disco?

Primero gracias por responder. Es una maquina virtual asi que tranquilamente puedo asignarle 10Gigas a esa particion. El tema es el modo de hacerlo ya que es productivo.

My english is very poor but, thanks for asking. It´s a virtual machine, so i can use a 10G partition, but the problem is the way to separate the /var directory, in the server, because it´s operative.

---

### Post by sanguinoso on 2011-04-27
Que programa se utiliza por la maquina virtual? Yo uso vmware y es posible para agregar un disco. Pero debería reiniciar. Si cambia /etc/fstab de manera que el punto de montaje es /var/ del nuevo disco, debería funcionar bien.

Lo siento, uso un dicionario por las palabras tecnicas.

---

### Post by sanguinoso on 2011-04-27
También ubuntu no guarda los registros de más de una semana o dos. Yo pienso...

---

### Post by alfplayer on 2011-04-28
Si sabes agrandar la partición, cuál es la dificultad?

---

