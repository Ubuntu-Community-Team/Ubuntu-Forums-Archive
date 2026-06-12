---
title: "Ubuntu 11.10- Evolution"
date: 2011-10-21
forum: Software
---

### Post by Vero1 on 2011-10-21
Hola a todos,

Hace dos días he hecho upgrade de Ubuntu 11.04 a 11.10, directamente desde Internet.
Estoy teniendo ciertos problemas desde el vamos, pero el problema mas grave que se me presentó fue que De los mas de 2100 mensajes que tenía en la Bandeja de Entrada, solamente se reflejan 400. No sé dónde fueron a parar los que faltan.Cometí el error de no hacer un backup previamente. 
Del mes de Octubre 2011 no tengo ninguno, cosa que me llama la atención, más teniendo en cuenta que en la Bandeja de Salida si hay.

Hay problema con mbox que no pude instalar porque el applet está roto. Ya lo reporté a Launchpad pero aún no me respondieron.
Si no tengo mal entendido el mbox sirve para contener mucha cantidad de correos o no es asi?
Si así fuera me pregunto si los correos faltantes tendrán alguna relación.

Bueno, espero que alguien pueda darme una solución para volver a tener los correos faltantes y desde ya les agradezco.

saludos

---

### Post by hictio on 2011-10-22
Una lástima que no hayas hecho un backup de Evolution antes de hacer el update.
Con el proceso de backup del propio Evolution (File > Backup Settings) vengo pasando mis emails (agenda, contactos, etc) desde 7.04 sin mayores problemas.
Tu cuenta de email es pop3 o imap? Quizás tengas copia en el servidor?

---

### Post by Vero1 on 2011-10-22
Hola, gracias por responder.

Es POP3.

saludos

---

### Post by danielvelez on 2011-10-27
Hola
Me sucedió lo mismo por aquí. Sin embargo, el problema no parece ser sólo con la pérdida misteriosa de muchos correos, sino que además cuando envío un correo electrónico, me genera un error.

Básicamente se creó misteriosamente una subcarpeta dentro de las carpetas de correo en Evolution que se llama #evolution, y que tiene una subcarpeta llamada sbd. Ambas carpetas están vacías.
Por otro lado, se me perdieron los nombres de las carpetas que tenía (Revisados) y obviamente los correos que contenían.

Ahora, el error cuando envío un correo:

"Your message was sent, but an error ocurred during post-processing.
The reported error was "failed to appendo to mbox:///home/***/.local/share/evolution/mail/local#Sent: Invalid folder URI...
Appending to local 'Sent' folder instead"

Lo curioso es que explorando la carpeta /home/***/.local/share/evolution/mail/local, aparecen lo que parecen los correos desaparecidos, e incluso el archivo "revisados" que supongo contiene la "carpeta" de evolution que contiene los correos que puse allí antes de la actualización.

Parece un problema de redireccionamiento de las carpetas en la nueva versión de Evolution, pero no sé cómo corregirlo, o como re-activar las subcarpetas perdidas.

---

### Post by Vero1 on 2011-10-27
Hola DanielVelez,

No es exactamente lo mismo pero bueno.
A mi directamente no me sale ningun error cuando intento enviar.
Me informa que envió el 100% pero el correo sigue en la Bandeja de Salida

Hasta el momento no tengo resolución del problema.

saludos

---

### Post by Vero1 on 2011-10-28
Hola,

Realmente no puedo decir exactamente de qué manera se resolvió pero pienso que se debe a que entré en modo de recuperación y éso debe haber ayudado.

Ahora ya puedo enviar.

En cuanto a hacer backup todavía me sigue saliendo el cartelito de que la aplicación no está soportada, pero me dijeron que no hiciera caso y efectivamente empezó el backup pero quería respaldar mas de 2000 mails. Pienso que deben ser todos los mails que tenía a partir de la primera distribución. No sé cómo se puede hacer para que haga backup de los mails de las distintas bandejas por separado.

Si alguien lo sabe, agradecida desde ya.

saludos

---

