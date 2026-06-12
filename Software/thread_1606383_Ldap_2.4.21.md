---
title: "Ldap 2.4.21"
date: 2010-10-26
forum: Software
---

### Post by ketepa on 2010-10-26
Buen día gente, necesito ayuda para configurar open ldap, instale la ultima versión y no encuentro documentación de como configurar LDAP de esta versión, ya que desapareció el viejo slapd.conf y solo quedo ldaf.conf y una carpeta slapd.d

---

### Post by guillermolisi on 2010-10-26
Desaparecio o esta en otra ubicacion ?

Si bien [este how to]("http://englanders.us/~jason/howtos.php?howto=openldap") esta en Ingles y realizado bajo Slackware, creo que podria orientarte, por lo menos para verificar un par de cosas.

---

### Post by sys.adm.og on 2010-10-26
> **ketepa said:**
> Buen día gente, necesito ayuda para configurar open ldap, instale la ultima versión y no encuentro documentación de como configurar LDAP de esta versión, ya que desapareció el viejo slapd.conf y solo quedo ldaf.conf y una carpeta slapd.d


Como estas!
En su web estan las Guias de Administración.
[http://www.openldap.org/doc/admin24/](http://www.openldap.org/doc/admin24/)

Exitos.

---

### Post by ketepa on 2010-10-28
> **sys.adm.og said:**
> Como estas!
En su web estan las Guias de Administración.
[http://www.openldap.org/doc/admin24/](http://www.openldap.org/doc/admin24/)

Exitos.

Hola!!! si tenés razón!!! Bueno a ver si ya que estamos hacemos una mini-guía de como funciona esta configuración dinámica.

Muchas gracias, eso me pasa por no saber leer, je

Ketepa

---

### Post by sys.adm.og on 2010-10-28
Ldap te va hacer sacar canas. En la empresa estamos con eso tambien!:guitar:

---

### Post by ketepa on 2010-11-05
Bueno desculando un poco el tema, basicamente la carpeta slapd.d dentro de /etc/ldap es casi lo mismo que el viejo slapd.conf, solamente que esta trabajado de forma que tome las configuraciones dinamicamente desde archivos .ldif

Aqui encontre una buena info para implementarlo.

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)


Saludos,

David

---

