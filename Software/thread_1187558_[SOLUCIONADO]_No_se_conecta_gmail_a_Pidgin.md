---
title: "[SOLUCIONADO] No se conecta gmail a Pidgin"
date: 2009-06-14
forum: Software
---

### Post by Dame Cruz on 2009-06-14
Hola,
Me he adaptado bien a pidgin pero el problema que me plantea es que no me puedo conectar desde mi cuenta de gmail, he buscado algunos tutoriales sin exito.
La señal de la que me conecto es una que no permite la conección a servidores, no se si eso es lo que da problemas, pero me puedo conectar a la cuenta de hotmail.
Gracias.

---

### Post by moreback on 2009-06-15
Qué extraño, yo no tengo ningún problema para conectarme, ¿segura que estás creando tu cuenta como tipo Google Talk? La única diferencia que tengo con lo que sale ahí es que en la pestaña **Avanzadas** -> **Opciones de XMMP** tengo marcado **Requiere SSL/TLS**.

Saludos.

---

### Post by Dame Cruz on 2009-06-15
Uso mi cuenta de gmail, y he tiqueado todo por si acaso funciona, pero dice que es un problema SSL.

---

### Post by moreback on 2009-06-15
Intenta marcando sólo la opción que tengo yo. Además verifica que estés conectándote al puerto 5222 y el servidor es talk.google.com.

---

### Post by Iced_R on 2009-06-18
Podías conectarte con tu cuenta de Gmail en Messenger? Si es así, habilita el método HTTP en ls configuraciones de tu cuenta y verifica que sea el servidor por defecto para Hotmail (no recuerdo cuál es, pero no deberías tener que modificar nada xD) y que el puerto sea el 1863. Yo por lo menos no tengo ningún problema en conectarme en Pidgin con mi cuenta de Gmail.

---

### Post by Dame Cruz on 2009-06-18
Dice que no se puede conectar al servidor, cual ocupan?

---

### Post by moreback on 2009-06-19
> **Iced_R said:**
> Podías conectarte con tu cuenta de Gmail en Messenger? Si es así, habilita el método HTTP en ls configuraciones de tu cuenta y verifica que sea el servidor por defecto para Hotmail (no recuerdo cuál es, pero no deberías tener que modificar nada xD) y que el puerto sea el 1863. Yo por lo menos no tengo ningún problema en conectarme en Pidgin con mi cuenta de Gmail.

Pero eso es conectarse al Messenger, otro protocolo, lo que acá quieren es conectarse al Google Talk.

Dominio: gmail.com
Tiquear Requiere SSL/TLS
Puerto de Conexión: 5222
Conectar con el servidor: talk.google.com
Proxy para transferencia de archivos: proxy.jabber.org:7777

Eso tengo yo.

---

### Post by Dame Cruz on 2009-06-20
Lo hice funcionar con la configuración de esta página: [http://www.congdegnu.es/2009/01/29/como-configurar-google-talk-en-pidgin/](http://www.congdegnu.es/2009/01/29/como-configurar-google-talk-en-pidgin/)

Gracias de todos modos :D

---

