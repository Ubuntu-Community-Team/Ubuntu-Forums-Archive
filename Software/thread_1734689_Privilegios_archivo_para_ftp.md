---
title: "Privilegios archivo para ftp"
date: 2011-04-20
forum: Software
---

### Post by capcabgue on 2011-04-20
Hola:
Estoy trabajando en una red con redhat, pero los privilegios al archivo se los puedo dar como en Ubuntu (por línea de comandos).
Tengo un archivo que yo realizo, copio, modifico, pero necesito que alguien más lo ponga en un servidor mediante ftp, he intentado con chmod los privilegios para esto, pero no me resulta, ya que si hago me paso lo siguiente:
chmod 700 archivo = no lo puede leer, modificar (que es lo que quiero) pero no puede hacer un "put" para moverlo mediante ftp (es lo que necesito)
chmod 701 archivo= lo puede mover mediante ftp (esto esta bien), pero tambien lo puede leer (no quiero que pueda) alguien me puede decir como le puedo dar solo permiso para hacer un put para ftp y nada más.
Gracias y espero su respuesta

---

### Post by CarlosRuiz on 2011-04-24
Holap:

Tengo un servidor FTP (uso el famoso VSFTPD, es muy bueno en todos los sentidos), y para que funcione bien debo hacer que la carpeta "ftp" tenga los permisos:

**755**

El comando para hacerlo es:
**sudo chmod 755 /home/ftp**

Con cualquier otra combinación, siempre ocurre algún problema, incluso con la 777.
Espero haberte ayudado.

Saludooos :P

P.D:
Aquí te dejo un link que podría servir:
[http://carlosruizortega.wordpress.com/2008/11/16/servidor-ftp-en-ubuntu-%C2%BFy-para-que/](http://carlosruizortega.wordpress.com/2008/11/16/servidor-ftp-en-ubuntu-%C2%BFy-para-que/)

---

### Post by RafaelG on 2011-04-25
> **CarlosRuiz said:**
> **sudo chmod 755 /home/ftp**

[SIZE=2]777 = [/SIZE][FONT=verdana,arial,helvetica,sans-serif][SIZE=2]Owner, group y others tienen permiso de lectura, escritura y ejecución[/SIZE][/FONT][SIZE=2]
766 =[/SIZE][FONT=verdana,arial,helvetica,sans-serif][SIZE=2] Owner tiene permiso de lectura, escritura y ejecución. Group y others permiso de lectura y escritura.[/SIZE][/FONT][SIZE=2]
755 = [/SIZE][FONT=verdana,arial,helvetica,sans-serif][SIZE=2]Owner tiene permiso de lectura, escritura y ejecución. Group y others permiso de lectura y ejecución.[/SIZE][/FONT] [SIZE=2](Recomendado)[/SIZE]
 [FONT=verdana,arial,helvetica,sans-serif][SIZE=2]744 = Owner tiene permiso de lectura, escritura y ejecución. Group y others unicamente permisos de lectura. [/SIZE][/FONT][SIZE=2]

Documentacion oficial de Ubuntu para FTP:
[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html) 

Saludos,[/SIZE]

---

### Post by capcabgue on 2011-04-27
[QUOTE=[FONT=verdana,arial,helvetica,sans-serif][/FONT][SIZE=2]
Documentacion oficial de Ubuntu para FTP:
[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html) 
[/SIZE][/QUOTE]
Muchas gracias, pero efectivamente ya conocía lo de los privilegios en un archivo.
Sin embargo, mi problema es otro, ya que yo debo creae el archivo, por lo cual yo soy el owner, pero otra persona del grupo debe tomarlo y ponerlo en el server mediante ftp.
En definitiva, yo creo un archivo en mi carpeta y otra persona debe ponerlo en el servidor.
Yo no quiero que pueda leer, modificar el archivo que cree, solo quiero que lo pueda mover mediante ftp.
 Espero explicarme
Gracias

---

### Post by Killer Jacker on 2011-04-29
> **capcabgue said:**
> Muchas gracias, pero efectivamente ya conocía lo de los privilegios en un archivo.
Sin embargo, mi problema es otro, ya que yo debo creae el archivo, por lo cual yo soy el owner, pero otra persona del grupo debe tomarlo y ponerlo en el server mediante ftp.
En definitiva, yo creo un archivo en mi carpeta y otra persona debe ponerlo en el servidor.
Yo no quiero que pueda leer, modificar el archivo que cree, solo quiero que lo pueda mover mediante ftp.
 Espero explicarme
Gracias

Hola Capcabgue. Creo que el problema que planteas es un poco complicado. Si no quieres que otro usuario pueda leer el archivo, no debiera tener el permiso de lectura (r) que es el permiso básico para trabajar con archivos. Creo no equivocarme al decir que un usuario debe tener como mínimo permiso de lectura para poder, aunque sea, mover el archivo. Quizás debieras buscar alguna otra forma de impedir el acceso al contenido del archivo, ya que si quieres que otro usuario "lo mueva", debe tener permiso de lectura sobre él. :-\"

Algo más complicado podría ser que hicieras un script que automatizara la subida de dicho archivo con un usuario autorizado. Y al "otro usuario" le das permiso de ejecución al script... 
no... muy complicado... :P

---

