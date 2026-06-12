---
title: "ClamAV"
date: 2008-05-20
forum: Software
---

### Post by Vero1 on 2008-05-20
Hola a todos,
Ayer utilicé ClamAV que encontró 2 virus en Evolution. Los mandé a cuarentena. 
Hoy me encuentro con la desagradable sorpresa de que se han borrado todos los mensajes de la Bandeja de Entrada y el antivirus me saca este aviso:
evolution-shell-Message: Killing old version of evolution-data-server...

Hay alguna forma de recuperar estos mensajes?

Tampoco están los enviados.

Aclaro que un virus estaba en la Bandeja de Entrada y el otro en Enviados.

Yo no configuré nada con respecto a eliminar nada.

Espero vuestros comentarios y gracias.

---

### Post by euzkoarima on 2008-05-20
Te digo solamente de memoria, porque el ClamAV lo usé en OSX pero hace rato que no lo uso. Fijate en la documentación, pero me acuerdo que te dicen que no pongas en cuarentena los mails (en realidad depende del programa que uses, pero con la mayoría) porque, por ejemplo, tu bandeja de entrada puede tener 20 mails, 1 tiene un virus, pero "el archivo" (físico) es uno solo para toda la bandeja, con los 20 mails incluídos. Así que si lo mandás a cuarentena lo moviste de directorio y tu programa de mail "pierde los mails" tal como vos comentás.

CREO, que hay una opción de sacar de cuarentena, y si mal no recuerdo tenías que volver el archivo a su lugar a mano (creo que no lo volvía a poner donde estaba en forma automática)

lo del mensaje > evolution-shell-Message: Killing old version of evolution-data-server...
ni idea.

Suerte.

---

### Post by Vero1 on 2008-05-20
Gracias por responder tan rápido.

Es la primera vez que uso este antivirus y no sabía que movería toda la carpeta...
Dices que lo tengo que poner de vuelta a mano.
Eso se hace desde Terminal? porque no hay opción en la solapa de Cuarentena para restaurar.

En caso de que así sea, cómo sería el comando? No tengo mucho conocimiento todavía de los comandos. Serías tan amable de indicarme?

Muchas gracias

---

### Post by MeduZa on 2008-05-20
> **Vero1 said:**
> Gracias por responder tan rápido.

Es la primera vez que uso este antivirus y no sabía que movería toda la carpeta...
Dices que lo tengo que poner de vuelta a mano.
Eso se hace desde Terminal? porque no hay opción en la solapa de Cuarentena para restaurar.

En caso de que así sea, cómo sería el comando? No tengo mucho conocimiento todavía de los comandos. Serías tan amable de indicarme?

Muchas gracias

lo que pasa es que el evolution debe guardar todos los email en un solo archivo (como hace thunderbird) y por eso te "pone en archivo infectado en cuarentena" pero lo que hace es mover el archivo de emails
lo que tenes que hacer es ver que email es y borrarlo y listo.

---

### Post by Vero1 on 2008-05-20
> **MeduZa said:**
> lo que pasa es que el evolution debe guardar todos los email en un solo archivo (como hace thunderbird) y por eso te "pone en archivo infectado en cuarentena" pero lo que hace es mover el archivo de emails
lo que tenes que hacer es ver que email es y borrarlo y listo.

Imposible porque no tiene la opción de ver de qué e-mail se trata, solo informa que hay dos virus en Inbox y Sent.l


Gracias igual.

---

### Post by euzkoarima on 2008-05-20
En "algún lado" (no recuerdo donde) de las preferencias del ClamAV tiene que estar a que carpeta mueve lo que va a cuarentena.
Entiendo que ahí tendría que estar tu mailbox (bandeja de entrada) y hay que moverlo a donde si debería estar.
El tema es que no uso evolution (uso Thunderbird) por eso no se decirte "donde debería estar".

Una vez que tengas ubicados esos dos directorios moves de uno a otro arrastrando con el ratón.

Y si, uno de los problemas del clamav es que te dice que un mail tiene virus y no sabes cual (me pasaba).


Saludos

---

### Post by Hei Ku on 2008-05-20
Fijate si no hay un plugin de Evolution para ClamAv. En el caso de Kontact, tiene un plugin para KlamAV y entonces te permite escanear los mails entrantes. Como los mails tienen un formato particular es mejor escanearlos con un plugin particular para el cliente de correo que uses. Los programas generales no entienden el formato de los correos y te pueden hacer desastres asi.

---

### Post by Vero1 on 2008-05-21
> **euzkoarima said:**
> En "algún lado" (no recuerdo donde) de las preferencias del ClamAV tiene que estar a que carpeta mueve lo que va a cuarentena.
Entiendo que ahí tendría que estar tu mailbox (bandeja de entrada) y hay que moverlo a donde si debería estar.
El tema es que no uso evolution (uso Thunderbird) por eso no se decirte "donde debería estar".

Una vez que tengas ubicados esos dos directorios moves de uno a otro arrastrando con el ratón.

Y si, uno de los problemas del clamav es que te dice que un mail tiene virus y no sabes cual (me pasaba).


Saludos

Bueno, pude solucionar el problema.
Me fije en uno de los archivos de ClamTk(es el programa que hace el scan) y allí hablaba de que si uno le pone Falso Positivo esos mails son enviados a Mi Carpeta Personal. Efectivamente allí estaban. Me fuí a Evolution y con la opción de Importar pude importar a sus lugares de origen los mails. Estoy muy contenta :-)
Gracias por tu tiempo y porque trataste de ayudarme.

saludos

---

### Post by Vero1 on 2008-05-21
> **Hei Ku said:**
> Fijate si no hay un plugin de Evolution para ClamAv. En el caso de Kontact, tiene un plugin para KlamAV y entonces te permite escanear los mails entrantes. Como los mails tienen un formato particular es mejor escanearlos con un plugin particular para el cliente de correo que uses. Los programas generales no entienden el formato de los correos y te pueden hacer desastres asi.

Hola Hei Ku :-)

Gracias por tu comentario. Me fijaré si hay algun plugin para Evolution, pero por si acaso, no enviaré nada mas a cuarentena :-)

saludos

---

