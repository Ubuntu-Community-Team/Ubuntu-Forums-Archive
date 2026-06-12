---
title: "Administración FTP"
date: 2009-04-18
forum: Software
---

### Post by KaKuS on 2009-04-18
Hola gente, les cuento, ya tengo mi primer servidor en Linux. Como recien empiezo todavía me faltan algunas cosas.

Tengo el vsftpd andando en modo privado y hace todo lo que necesito que haga.

El tema es el siguiente, para darle acceso ftp a un cliente le tengo que crear una cuenta en el servidor. Pero yo no quiero que en el listado de usuarios que aparece en el menú de "Apagar, cerrar sesion, etc" me aparezcan los 30 usuarios para el ftp que tengo creados y tampoco quiero que se puedan loguear localmente.

¿Hay alguna manera de que existan usuarios pero que no solo no se puedan loguear localmente sino que además no me aparezcan en ese listado?

Saludos

---

### Post by faktorqm on 2009-04-18
Por supuesto que existe! 

```
useradd -s /bin/nologin nombre_usuario
```

Eso te hace que no se pueda loguear y que no se le cree la carpeta home. 

Lo del listado de usuarios que hablas es una configuracion tuya de alguna parte de la interfaz grafica que muestra eso, no tiene nada que ver con usuarios y grupos......

Y ahora la pregunta del millon: ¿instalaste interfaz grafica en un servidor?? Salu2!

---

### Post by KaKuS on 2009-04-18
> **faktorqm said:**
> Por supuesto que existe! 

```
useradd -s /bin/nologin nombre_usuario
```

Eso te hace que no se pueda loguear y que no se le cree la carpeta home. 

Lo del listado de usuarios que hablas es una configuracion tuya de alguna parte de la interfaz grafica que muestra eso, no tiene nada que ver con usuarios y grupos......

Y ahora la pregunta del millon: ¿instalaste interfaz grafica en un servidor?? Salu2!

El tema es que el servidor esta para bajar cosas de P2P, probar páginas web y hacer pruebas desde una red externa a la de trabajo. Como todavía no me cierra el tema de navegar o usar torrents y ese tipo de cosas desde la consola le instale un ubuntu desktop.

El ftp lo administro totalmente de la consola, vía ssh. Salvo cuando tengo que usar algunas de las cosas que te puse arriba y ahí me logueo por VNC.

Gracias por la info, igual sigo buscando como evitar que aparezcan en mi interfaz gráfica. No es nada amigable ver una lista de 30 usuarios ahí.

No entiendo esa necesidad de que sean usuarios locales, me gustaría poder agregar usuarios como en otras aplicaciones (todas bajo microsoft) en las que simplemente agregas los usuarios y las contraseñas a un listado que no tiene nada que ver con los usuarios del sistema operativo.

En un tutorial del vsftpd vi que había un vsftpd.user_list donde agregar los usuarios sin ser estos locales. Pero en la versión que descargue para ubuntu no esta la línea donde la activas. Supongo que me estoy pasando algo por alto.

---

### Post by Hei Ku on 2009-04-18
No probaste hacerlo con OpenLDAP? De esa manera manejas los usuarios independientemente del servidor.

---

### Post by guillermolisi on 2009-04-18
> **Hei Ku said:**
> No probaste hacerlo con OpenLDAP? De esa manera manejas los usuarios independientemente del servidor.
Si, OpenLDAP podria ser una alternativa pero me parece mucho mas compleja (y con mayor funcionalidad tambien) que administrar un archivo de texto con una lista de 30 users.

Encontre algo que posiblemente sirva en [http://www.ubuntu-es.org/index.php?q=node/78510](http://www.ubuntu-es.org/index.php?q=node/78510)

---

### Post by ramiro_md on 2009-04-18
ESte thread me viene al pelo :D. Justo estaba teniendo un problema con proftpd...es un problema digno d un salame, pero bueno, es un problema en fin :P. 
Resulta que no puedo crear un usuario para el ftp, por lo que leí en este tuto [http://www.frikis.org/staticpages/index.php?page=proftpd](http://www.frikis.org/staticpages/index.php?page=proftpd) la ucestión es crear un usuario normal de linux y luego modificar el /etc/passwd la línea del usuario nuevo para que quede con shell /bin/false y en el direcotrio home /home/usuario/www (en la guia dice ftp pero yo tengo la carpeta www je).
Entonces cuando me quiero loguear haciendo "ftp ip" ingreso el usuario que cree anteriormente y me dice loguin incorrecto :S
Si me podrían daruna mano se los agardecería je.
Un saludo !
Y garcias.

---

### Post by guillermolisi on 2009-04-18
> **ramiro_md said:**
> ESte thread me viene al pelo :D. Justo estaba teniendo un problema con proftpd...es un problema digno d un salame, pero bueno, es un problema en fin :P. 
Resulta que no puedo crear un usuario para el ftp, por lo que leí en este tuto [http://www.frikis.org/staticpages/index.php?page=proftpd](http://www.frikis.org/staticpages/index.php?page=proftpd) la ucestión es crear un usuario normal de linux y luego modificar el /etc/passwd la línea del usuario nuevo para que quede con shell /bin/false y en el direcotrio home /home/usuario/www (en la guia dice ftp pero yo tengo la carpeta www je).
Entonces cuando me quiero loguear haciendo "ftp ip" ingreso el usuario que cree anteriormente y me dice loguin incorrecto :S
Si me podrían daruna mano se los agardecería je.
Un saludo !
Y garcias.
Antes de modificar el /etc/passwd ingresa bien al ftp o tampoco funciona ?

Revisaste permisos de /home/usuario/www ?

---

### Post by ramiro_md on 2009-04-19
> **guillermolisi said:**
> Antes de modificar el /etc/passwd ingresa bien al ftp o tampoco funciona ?

Revisaste permisos de /home/usuario/www ?

En si el ftp funciona, porque probé conectarme al servidor de un amigo y lo hizo de toque. Sipongo mi usuario de sistema (ramiro) conecta y me entra a mi /home (obviamente)..pero por ejemplo, cuando quiero ingresra con el usuario que cree especialmente para el ftp no hay caso :S.
Por otro lado, los permisos de la carpeta /home/usuario/www son de lectura, excritura y ejecución.
Gracias, un saludo (y tal vez nos veamos en la RP).

---

