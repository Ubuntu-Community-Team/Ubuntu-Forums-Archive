---
title: "Correo Evolution  - expiró el tiempo de conexion"
date: 2010-12-10
forum: Software
---

### Post by bygot on 2010-12-10
Hola, recientemente  he actualizado (formateando) a Ubuntu 10.10 y luego de restaurar el correo me dice desde un archivo nombre.tar.gz al hacer click en Enviar/Recibir (antes al hacer esto me pedia mi password para desbloquear el "anillo de llaves" y  ahora no hace nada, al agregar una nueva cuenta de correo no pide la password) me da un error "expiró el tiempo de conexion"   antes no me pasaba con la 9.10,  supongo que no escorrecta algun tipo de configuracion de la red o dns uotra cosa  la conexion a internet  funciona  traves de un adsl-modem dlink 504t 
He buscado y buscado  sin encontrar algun post similar

desde la consola , pero no entiendo la respuesta

$ dig smtp.gmail.com

;dig smtp.gmail.com

; <<>> DiG 9.7.1-P2 <<>> smtp.gmail.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42922
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 4, ADDITIONAL: 4
;; QUESTION SECTION:
;smtp.gmail.com.            IN    A
;; ANSWER SECTION:
smtp.gmail.com.        110    IN    CNAME    gmail-smtp-msa.l.google.com.
gmail-smtp-msa.l.google.com. 110 IN    A    74.125.65.109
;; AUTHORITY SECTION:
google.com.        299250    IN    NS    ns3.google.com.
google.com.        299250    IN    NS    ns2.google.com.
google.com.        299250    IN    NS    ns4.google.com.
google.com.        299250    IN    NS    ns1.google.com.
;; ADDITIONAL SECTION:
ns1.google.com.        144971    IN    A    216.239.32.10
ns2.google.com.        140306    IN    A    216.239.34.10
ns3.google.com.        146646    IN    A    216.239.36.10
ns4.google.com.        140306    IN    A    216.239.38.10
;; Query time: 24 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri Dec 10 21:57:24 2010
 MSG SIZE  rcvd: 222


Desde ya gracias
Este es mi primer post si no esta en el lugar correcto cambiarlo, gracias de nuevo

Bygot

---

### Post by guillermolisi on 2010-12-11
La salida que te dio la corrida de dig dice que llegas perfectamente bien al server SMTP de Google, es decir no tenes problemas de acceso y/o conectividad.

No termino de entender esta parte de tu relato > Hola, recientemente he actualizado (formateando) a Ubuntu 10.10 y luego de restaurar el correo me dice desde un archivo nombre.tar.gz al hacer click en Enviar/Recibir

Como fue el proceso de respaldo y restauracion de los mensajes de e-mail ?

Que cliente de correo electronico estas usando ?

Que se supone contiene ese tarball (.tar.gz) ?

---

### Post by bygot on 2010-12-11
Guillermo :
Siempre dispuesto gracias por respuesta

Como fue el proceso de respaldo y restauracion de los mensajes de e-mail ?
Desde el menu del "Correo Evolution" Archivo - Respaldar configuracion , Archivo  restaurar ajustes

Que cliente de correo electronico estas usando ?
Evolution Mail (correo por defecto)
 
Que se supone contiene ese tarball (.tar.gz) ? 
contiene los mensajes, carpetas , libreta de direcciones, cuentas de correo, 

cabe mencionar tambien que intente sin exito con el cliente de de correo  del navegador Opera

Por otro lado  la version que teia antes era la 9.04 no la 9.10 

Axel

---

### Post by guillermolisi on 2010-12-12
Suponiendo que ese respaldo y su posterior restauracion sean perfectamente compatibles entre las versiones de Evolution que estabas usando y que usas actualmente, revisaria la configuracion completa de las cuentas de e-mail y los parametros de conexion con el o los servidores de e-mail de cada una.

Expiro el tiempo de conexion denota que esta intentando acceder a un server que no le responde, no existe o no encuentra.

---

### Post by bygot on 2010-12-12
Gullermo :
Gracias por la respuesta , ahora no estoy en mi casa para revisar tus comentarios, en cuanto llegue me fijo.
Axel

---

### Post by bygot on 2010-12-12
La cuenta que estoy utilizando esta configurada asi

Recepcion de correo 
tipo se srvidor POP
servidor: pop.gmail.com:995
usuario: miusuario
cifrado: ssl

envio de correo 
tipo se srvidor SMTP
Servidor: smtp.gmail.com:465
marcado en  El sevidor requiere autentificacion 
usar coneccion segura SSL
atentificacion PLANO 
usuario : miusuario

aun sigue con el mismo error

Axel

---

