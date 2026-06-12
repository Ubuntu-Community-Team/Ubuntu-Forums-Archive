---
title: "Mensaje de evolution, ¿debo aceptar o no?"
date: 2010-08-10
forum: Software
---

### Post by claracc on 2010-08-10
Hola,

He publicado la siguiente pregunta en el general help de ubuntu forums, pero como el mensaje de error que recibo está en español, me da la impresión de que no me van a entender ni contestar.

Por eso lo pregunto aquí, a ver si alguien lo sabe:

Desde ayer recibo el siguiente mensaje en evolution (lo tengo configurado para recibir los mensajes de mi cuenta hotmail y otras cuentas):

Comprobación de Certificado SSL para pop3.live.com:

Emisor: CN=Entrust.net Secure Server Certification Authority,OU=(c) 1999 Entrust.net Limited,OU=www.entrust.net/CPS incorp. by ref. (limits liab.),O=Entrust.net,C=US
Asunto: CN=pophm.sympatico.ca,OU=Bell Sympatico,O=Bell Canada,L=Toronto,ST=Ontario,C=CA
Huella: 78:22:65:8d:bb:7b:cd:35:e0:5e:d6:fb:b6:c5:78:05
Firma: ERRÓNEO

¿Quiere aceptar?

Yo le doy a cancelar y obtengo otro mensaje de error:
Error al obtener mensajes: Ocurrió un error cuando se leía un saludo válido desde el servidor POP pop3.live.com

Mi pregunta es, ¿qué es esto?, ¿es spam?, ¿un intento de instalar un certificado falso?, ¿debo aceptar o cancelar como he hecho hasta ahora?

Muchas gracias y saludos

---

### Post by alfplayer on 2010-08-10
Habría que averiguar si el servicio POP de Windows Live o Evolution tienen problemas actualmente con certificados inválidos o vencidos. Es natural que se establezca la comunicación si no se acepta el certificado. Se podría probar con otro cliente de correo como Thunderbird, asegurando de ingresar los datos de configuración correctos.

---

### Post by Cajuma on 2010-08-10
Hola Claracc, si te sirve yo en Ubuntu uso Thunderbird, en el que tengo configuradas, tres cuentas, Arnet mail, gmail y live.com y en ninguna de las tres, me tiró ningún error.
En Live.com, servidor entrante: POP3.live.com en puerto 995 SSL/TLS 
saliente smtp.live.com puerto 25 SSL/TLS.
No te puedo responder lo de Evolutión, pues hace tiempo que no lo uso.
Saludos.....;)

---

### Post by claracc on 2010-08-12
No me ha vuelto a aparecer el mensaje en evolution.

Si accedo directamente desde la web a mi cuenta de hotmail, tampoco aparece nada sobre un saludo válido desde Ontario Canadá (no conozco a nadie allí, supongo que es spam), ni tampoco nada de un certificado erróneo.

Gracias por responder, saludos

---

