---
title: "Acceso a Tomcat"
date: 2010-05-18
forum: Software
---

### Post by fma81 on 2010-05-18
Hola, soy nuevo en Linux y en Ubuntu. 

Pude instalar java y configurar el Home, instalé Tomcat 6 (java-tomcat desde Synaptic) en Ubuntu 10.04. 

Ejecuté el startup.sh.
Apunté al [http://localhost:8080/manager/hmtl](http://localhost:8080/manager/hmtl) levantó el login del Tomcat.

Pero no logro ingresar al manager, utilicé los usuarios que están en el /etc/tomcat6/tomcat-users.xml y en todos los casos no los acepta, tampoco aparece mensaje de error de login, al aceptar queda en blanco el usario/contraseña.

Les agradecería si podrían ayudarme y poder acceder al Tomcat.

Muchas gracias.

Saludos

---

### Post by tom.gobel on 2010-07-21
Senor,
Puedo leer, pero no escribir bien. (I can read but not write well.)

Acabo de hacer esto (I just did this):

$ sudo vi /etc/tomcat6/tomcat-users.xml 

[I]<tomcat-users>

<role rolename="manager" />
<user username="test" password="test" roles="manager" />

</tomcat-users>[/I]

$ sudo service tomcat6 restart

Ahora, voy a [http://localhost:8080/manager/html](http://localhost:8080/manager/html), y todo es bien. (I got to that url, and it works fine)

Buena suerte

---

