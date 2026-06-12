---
title: "Una mano con LDAP"
date: 2009-09-28
forum: Software
---

### Post by agosto on 2009-09-28
Antes que nada Hola a todos, soy nuevo en el foro y tamb en el mundo Linux.

Realmente me enganche mucho con el tema y ahora no puedo despegarme de la pc :)
Pero como todo novato tengo mis problemas y dudas.

Queria saber si alguien sabia de alguna Guia de LDAP, ya que quiero armar un servidor de datos y quiero dar los permisos de luctura y escritura en cada carpeta y asi armar toda la estructura de accesos.

Me pasaron este link [http://tecnoloxiaxa.blogspot.com/2008/11/servidor-ldap-en-ubuntu-o-debian-con.html](http://tecnoloxiaxa.blogspot.com/2008/11/servidor-ldap-en-ubuntu-o-debian-con.html)

Me fue bastante bien pero me mori con el JXplorer, no entiendo bien la diferencia entre el phpldapadmin y el JXplorer.

Espero alguien me pueda dar una mano, si puede ser la guia en español se lo agradecere muchisimo.

Disculpen si ya es tema viejo para algunos pero realmente intente buscar en el foro y todo lo que encontre estaba en Ingles y no me doy mucha maña.

Salu2

---

### Post by agosto on 2009-09-28
root@server-ldap:/home/ldap/Escritorio# sh ./JXv3.2.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jre1.6.0_16/bin//java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

Perdon por el doble post pero queria mostarles el error q me tira. 

Gracias

---

### Post by guillermolisi on 2009-09-28
> **agosto said:**
> Antes que nada Hola a todos, soy nuevo en el foro y tamb en el mundo Linux.

Realmente me enganche mucho con el tema y ahora no puedo despegarme de la pc :)
Pero como todo novato tengo mis problemas y dudas.

Queria saber si alguien sabia de alguna Guia de LDAP, ya que quiero armar un servidor de datos y quiero dar los permisos de luctura y escritura en cada carpeta y asi armar toda la estructura de accesos.

Me pasaron este link [http://tecnoloxiaxa.blogspot.com/2008/11/servidor-ldap-en-ubuntu-o-debian-con.html](http://tecnoloxiaxa.blogspot.com/2008/11/servidor-ldap-en-ubuntu-o-debian-con.html)

Me fue bastante bien pero me mori con el JXplorer, no entiendo bien la diferencia entre el phpldapadmin y el JXplorer.

Espero alguien me pueda dar una mano, si puede ser la guia en español se lo agradecere muchisimo.

Disculpen si ya es tema viejo para algunos pero realmente intente buscar en el foro y todo lo que encontre estaba en Ingles y no me doy mucha maña.

Salu2
Releyendo nuevamente tu primer post me parece que o falta algun dato adicional o te estas complicando la vida.

LDAP sirve para validar usuarios en una sesion de red, en un dominio local. Tal como hacen otros sistemas opertivos (historicamente conocidos como Domain Controller para este caso) con algo llamado Active Directory que no es mas que una implementacion de LDAP en otro contexto.

Si lo que estas procurando es un esquema de permisos de lectura, escritura, ejecucion a nivel archivos (esto incluye directorios ya que tambien son archivos) dentro de una misma maquina, oficiando de file server por ejemplo, donde concurren varios usuarios que utilizan sistemas operativos que no son Linux, es una cosa.

Ahora si los clientes de ese file server estan usando Linux, creo que podrias administrar la cosa de otra forma mas sencilla, sin meterte con LDAP que no es algo que podria llamarse facil y menos para alguien que recien se inicia en Linux.

Tal vez suene a redundante y este subestimando tus conocimientos, pero antes de meterme con LDAP empezaria conociendo como es el sistema de permisos de Linux a nivel de archivos, luego lo equivalente para cuentas de usuario y despues encararia algo mas complejo en funcion de lo que queres realizar y las distintas soluciones que podes implementar.

Tal vez si das algo mas de detalle sobre tu proyecto podamos afinar mejor la punteria.

---

### Post by faktorqm on 2009-09-29
[http://www.alcancelibre.org/staticpa...BALDAP-CENTOS5](http://www.alcancelibre.org/staticpa...BALDAP-CENTOS5)
[http://www.alcancelibre.org/staticpa...UI-LAM-Centos5](http://www.alcancelibre.org/staticpa...UI-LAM-Centos5)

si queres ver mas fijate en alcancelibre.org, tenes la seccion manuales y la de descargas.


fijate el primer link de aca que es el libro que tiene tooooooooooooooooodo 

[http://www.alcancelibre.org/filemgmt/](http://www.alcancelibre.org/filemgmt/)


[http://ostau2008.blogspot.com/2008/0...ptsources.html](http://ostau2008.blogspot.com/2008/0...ptsources.html)
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)
[http://wiki.samba.org/index.php/Impl...ies_with_Samba](http://wiki.samba.org/index.php/Impl...ies_with_Samba)
[http://blogs.clavedigital.com/ncasti...ler-sambaldap/](http://blogs.clavedigital.com/ncasti...ler-sambaldap/)
[http://www.improvisa.com/index.php?n...rticle&sid=387](http://www.improvisa.com/index.php?n...rticle&sid=387)

este ultimo esta muy bueno.

yo ya lo implemente y estuve haciendo un par de manuales pero es extremadamente aburrido y largo. prometo finalizar mi trabajo para que todos levanten sus dominios felices. Cualquier cosa pregunta. salu2!

---

### Post by agosto on 2009-09-29
Muchas gracias por toda la data que me han tirado, mañana estare un poco mas tramquilo en el trabajo y leere todo.

Les cuento que me recomendaron LDAP por que las maquinas que tienen que loguear son Windows.

Hoy en día la empresa donde trabajo esta en Windows y mi tarea es ir pasando a Linux, obiamente entienden que es un mundo nuevo para mi y tengo mi libertad para experimentar y ver lo que mas conviene.

Lo mas importante es cambiar los servidores, que obiamente son los mas caros al nivel licencia de Windows.

Con el tiempo tengo q lograr, Server de Datos - Dominio - Contro de navegacion (creo que se llama Squid pero no estoy seguro) - y servidor de Terminal Server.

Eso es lo que tengo que lograr.

Y creo que si logro hacer andar el Ldap y Samba luego el resto de las cosas se me aran mas faciles ya que uso la misma base de usuarios para todos los servicios que quiera agregar.


Bueno sigo intentando instalarlo, Gracias nuevamente por la data y si alguien sabe algo mas sobre LDAP que me pueda servir bienvenido.

---

### Post by guillermolisi on 2009-09-29
> **agosto said:**
> Muchas gracias por toda la data que me han tirado, mañana estare un poco mas tramquilo en el trabajo y leere todo.

Les cuento que me recomendaron LDAP por que las maquinas que tienen que loguear son Windows.

Hoy en día la empresa donde trabajo esta en Windows y mi tarea es ir pasando a Linux, obiamente entienden que es un mundo nuevo para mi y tengo mi libertad para experimentar y ver lo que mas conviene.

Lo mas importante es cambiar los servidores, que obiamente son los mas caros al nivel licencia de Windows.

Con el tiempo tengo q lograr, Server de Datos - Dominio - Contro de navegacion (creo que se llama Squid pero no estoy seguro) - y servidor de Terminal Server.

Eso es lo que tengo que lograr.

Y creo que si logro hacer andar el Ldap y Samba luego el resto de las cosas se me aran mas faciles ya que uso la misma base de usuarios para todos los servicios que quiera agregar.


Bueno sigo intentando instalarlo, Gracias nuevamente por la data y si alguien sabe algo mas sobre LDAP que me pueda servir bienvenido.
Para que usuarios con Win se "validen" en un dominio podes implementar algo mas simple con Samba como controlador. Para saber si esta alternativa es adecuada habria que considerar las especificaciones funcionales del caso.

Es decir, trabajas LDAP pero desde Samba que, por lo menos al principio, te puede facilitar algunas cosas.

---

### Post by faktorqm on 2009-09-30
Lo que te pase, el lo que dice Lisi. Es como levantar un dominio son samba para compartir carpetas e impresoras y hacer roaming profiles. Ahora bien, el control de navegacion se puede hacer con squid, pero el terminal server no. Digamos podes tener su equivalente en linux, pero va a ser una sesion de linux. entendes?

El camino para levantar un dominio es muy largo y tedioso, asi que cuando lo vayas a hacer, no te pongas mal si tardas una semana, la primera vez cuesta un monton. Salu2!

---

