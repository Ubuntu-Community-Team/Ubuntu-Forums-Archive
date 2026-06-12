---
title: "Ayuda con eBox o lo que se le parezca"
date: 2008-08-29
forum: Software
---

### Post by jpmorelli on 2008-08-29
Muy buenas a todos !
Hace varios dias que me estoy rompiendo el coco con esta distribucion que vendría a ser algo como una caja que hace de firewall, mailfilter, mailboxes, validación de usuarios con OpenLdap, Filesharing, PrinterSharing, etc y que esta basado en Ubuntu server, para los que no lo conocen está muy bueno y les paso la web desde donde se descarga, hasta tiene un LiveCD para probarlo:
[http://ebox-platform.com/]("http://ebox-platform.com/")

Hasta acá todo bárbaro pero para lo que principalmente lo quiero usar es para tenerlo como pasarela de los mails desde internet, filtrarlo con su antispam y antivirus y dejar esos mails en el servidor exchange de la empresa que los distribuye en sus buzones correspondientes.
La pregunta es: alguien que estuvo con este soft lo logró ?, o en su defecto, conocen alguno herramienta para hacer esto ? No quiero gastar una fortuna en un Brightmail de Symantec, etc.
Estuve leyendo mucho y me parece que lo que más se puede llegar a hacer si es que no trabajas los buzones en el Ebox es habilitar a un servidor externo para que empuje los mails al eBox , este los filtra y se los devuelve, pero... ni idea como hacer eso en el exchange.
Se entiende ? a ver si soy más prolijo... lo que quiero hacer es:

Internet --> Ebox (Filtrado de spam y virus) ---> Exchange

En el lugar donde trabajaba anets esto era tan simple como usar un appliance de Symantec que era la puerta de todo el mail ( servidor MX publico ), logueaba, filtraba y limpiaba de virus todos los mails y de ahi los mandaba al servidor exchange. 
Puse la pregunta en el foro de eBox pero nadie contesto :(
Gracias desde ya !!!

---

### Post by sergiom99 on 2008-08-29
proba con qmailtoaster [1]. Le pones el spamdyke[2] y santo remedio. te deja afuera el 95% del spam (segun mis propias estadisticas de los dominios hosteados en nuestros servidores). Dejas todo en una cuenta multiPOP que lo baja el Exchange desde el lado de atras y listo.

[1] [http://www.qmtiso.com/](http://www.qmtiso.com/)
[2] [http://www.spamdyke.org/](http://www.spamdyke.org/)

---

### Post by jpmorelli on 2008-08-29
Espectacular solución !!! Tal vez no sea tan completa como la anterior pero hace lo que necesito !, incluso puedo llegar a utilizar ambos...
Muchas gracias ! Ahora, este spamdyke es como un addon ? es fácil de agregarse, porque lo usas ? es más confiable que el spamassassin ?

Muchas gracias y un tenkiu para vos :lolflag:

---

### Post by sergiom99 on 2008-08-30
spamdyke corre antes aun que el spamassassin.
cuando se inicia una conexion SMTP al servidor, valida lo que quieras (si la ip esta en RBLs, si tiene rDNS, si el rDNS coincide con el nombre del server, etc. etc) si falla ni siquiera entrega el correo.
por ahi te lleva un par de semanas tunear todo para que no rebote ningun correo legitimo, pero hecho eso y haciendo que todos tus usuarios antes de mandar se autentiquen (con eso lo saltean) bajas una cantidad tremenda el spam, ya te digo en nuestros servers rebota el 95% del spam. el resto llega taggeado por spamassassin.
lo malo es que solo corre en una instalacion de qmail (cualquier qm), pero el QM es uno de los mejores (sino el mejor) MTA, asi que bien vale la pena.
si lo implementas anotate en la lista de spamdyke y te ayudamos desde ahi.
suerte!

---

### Post by faktorqm on 2008-09-01
GROSSO! como dice la propaganda "funciona para los veterinarios que trabajan de otra cosa!" jajajaj salu2!

---

### Post by sergiom99 on 2008-09-01
"elegido por 8 de cada 10 veterinarios gerentes de IT"

---

