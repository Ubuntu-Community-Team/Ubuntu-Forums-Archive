---
title: "Problemas con servidor isa"
date: 2009-08-20
forum: Software
---

### Post by Bytesn+1 on 2009-08-20
Buenas gente, esta es mi primera publicación/consulta, por lo tanto quería saber si es posible configurar el proxy en ubuntu, ya que no puedo utilizar apt-get/aptitude para descargar repositorios y actualizaciones, este muy incomodo ya que soy la unica persona que tiene gnu/linux en el trabajo, y por desgracia todos los servidores son windows y no me puedo (o no se) meterme en el dominio. La pregunta es que si alguien le ha pasado esto o tiene alguna idea de como poder actualizar el sistema por medio de los repositorios. Gente desde ya muchas gracias por leer esta duda y si pueden ayudar mucho mejor, saludos

---

### Post by Fistandantilus on 2009-08-20
Proba con esto

[http://ubuntuforums.org/archive/index.php/t-474978.html](http://ubuntuforums.org/archive/index.php/t-474978.html)

---

### Post by Bytesn+1 on 2009-09-01
Fistandatilus, gracias por responder...te cuento que no funciono, ya que el servidor de dominio es un 2003 y no me puedo acoplar a el. Lo que plantea este usuario ya lo habia probado en reiteradas veces y nunca pude hacerlo andar. Si alguien tiene una idea de como hacerlo, es para el laburo y me esta sacando la cabeza desde hace unos dias. desde ya muchas gracias. Saludos

---

### Post by gmunioz on 2009-09-01
Hola byt...:

Necesitas, previo a configurar el proxy para el 
Isa Server, configurar tu ordenador Ubuntu para 
que actúe como cliente del servidor Windows 2003.

Debes tener instalados: 

samba  smbclient winbind samba-common 

como no puedes utilizar los repositorios

deberas bajar los paquetes desde otro ordenador

e instalarlos con dpkg

a) Loguearse como root

En una terminal ejecutar

sudo su

b) Editar el archivo /etc/nsswitch.conf

gedit /etc/nsswitch.conf

Ver que quede con este contenido:

      passwd:         compat winbind
      group:          compat winbind
      shadow:         compat


c)  Editar el archivo /etc/pam.d/common-account

gedit /etc/pam.d/common-account

Ver que quede con este contenido

      account sufficient      pam_winbind.so
      account required        pam_unix.so try_first_pass

d) Editar el archivo /etc/pam.d/common-auth

gedit  /etc/pam.d/common-auth

Ver que quede con este contenido:

      auth    sufficient      pam_winbind.so
      auth    required        pam_unix.so nullok_secure try_first_pass

e) Editar el archivo /etc/pam.d/common-password

gedit /etc/pam.d/common-password,

Ver que quede con este contenido

      password    sufficient      pam_winbind.so
      password   required   pam_unix.so nullok obscure min=4 max=8 md5 try_first_pass

f) Editar el archivo /etc/pam.d/common-session

gedit  /etc/pam.d/common-session

Ver que quede con este contenido


      session sufficient      pam_winbind.so
      session required        pam_unix.so try_first_pass

g) Editar el archivo /etc/samba/smb.conf

gedit /etc/samba/smb.conf

Ver de cambiar estos parámetros:

        workgroup = NOMBRE_DEL_DOMINIO
        winbind use default domain = yes
        netbios name = NOMBRE_DEL_CLIENTE_LINUX
        # separate domain and username with '\', like DOMAIN\username
        winbind separator = '\'
        # allow enumeration of winbind users and groups
        winbind enum users = yes
        winbind enum groups = yes
        # give winbind users a real shell (only needed if they have telnet access)
        template homedir = /home/winnt/%D/%U
        template shell = /bin/bash

e) Unirse al dominio

       net rpc join -S <NOMBRE_NETBIOS_PDC> -U Administrador

si esto funciona, recien entonces, configurar

el proxy para el Isa Server

---

### Post by Bytesn+1 on 2009-09-23
Gabriel, gracias por responder...perdon por la demora de la respuesta, estuve haciendo unas tareas que me llevaron a dejar esto por un tiempo. Te comento que pude unirme al dominio, lo unico que faltaba era "security = domain". lo demas anduvo perfecto. Desde ya muchas gracias un abrazo

---

### Post by Bytesn+1 on 2009-09-24
Gente, consulta...tengo un problema con el isa server, no puedo actualizar mi sistema con apt-get update. Configure varias veces de varias maneras, pero ninguna me da un resultado posible...todo esto quedo mas o menos asi configurado y ahi me quede atascado

configuracion de opciones en /etc/ntlmaps/server.cfg  

PARENT_PROXY: svrisa (tambien probe con la ip)
PARENT_PROXY_PORT: 8080
NT_HOSTNAME: domino_adm1 (tambien probe con la ip)
NT_DOMAIN: estacion
USER: usuario (usuario de win2003)
PASSWORD: password (pass de win2003)

despues hice un export: export http_proxy=http://localhost:8080/

y cuando hago apt-get update, no funciona me tira este  cartel "no puede conectarse a localhost:8080 (127.0.0.1). - connect (111).

Alguien tiene idea? por que ya probe varias cosas y no pude dar con la tecla..igualmente gracias Fistandantilus pero no me sirvio. Saludos

---

### Post by gmunioz on 2009-09-25
Hola byt...:


Para que funcione es necesario configurar la variable http_proxy,

y todo lo aquello que necesite autenticacion de proxy a:

http//127.0.0.1:5865

5865 es el port por defecto del ntlmaps

---

### Post by Bytesn+1 on 2009-09-25
Gabriel, ya esta solucionado...tenia configurado el proxy en /etc/environment y creo que esto me estaba dando conflico, asi que lo quite y funciono. De todas formas gracias por responder, abrazo y gracias nuevamente

---

