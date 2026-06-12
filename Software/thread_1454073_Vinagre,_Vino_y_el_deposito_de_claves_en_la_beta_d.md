---
title: "Vinagre, Vino y el deposito de claves en la beta de Lucid Linx"
date: 2010-04-14
forum: Software
---

### Post by leillo1975 on 2010-04-14
Hola

En primer lugar me gustaría presentarme, me llamo Leo y soy Español, y el post que voy a escribiros ya lo posteé en el [foro de Ubuntu-es.org]("http://www.ubuntu-es.org/?q=node/131828") donde no encontré respuesta.

Os comento un problema que tengo que no se si es un bug o es que es así. En primer lugar comentar que con la 9.10 no me pasaba.

El caso es que tengo instalada la ultima beta de Lucid actualizada al dia de hoy en varios equipos. El equipo en que estoy yo normalmente lo usuo para conectarme via VNC con Vinagre al resto de equipos.

Los equipos servidores de Vino (que mal suena) los tengo como equipos de consulta y se trata de 3 equipos modestos iguales que se usan para ofimatica e internet.

Cuando me conecto desde mi equipo con Vinagre no consigo ver el escritorio remoto, y al ir a este me encuentro con una ventana que me indica que debo poner la contraseña de sesion para poder continuar. Una vez hecho esto puedo ver este equipo desde mi ordenador sin problema.

Los 3 equipos modestos tienen autologin, por lo que arrancan y llegan directamente al escritorio sin tener que meter la contraseña en el logon.

¿Existe alguna forma de evitar que salga este mensaje?

Un saludo a todos


EDITO: Me han contestado en el foro de Ubuntu-es.org y lo he solucionado. El problema se soluciona haciendo lo siguiente (copiado de "[me olvido de todo]("http://meolvidotodo.com.ar/2009/07/evitar-que-te-pregunta-cada-vez-la.html")"):

Para que te pregunte cada vez que ingreses la clave del keyring en Ubuntu 9.04
Le quita seguridad, pero prefiero que sea mas practico; sino cada vez que inicio ubuntu el network manager me pregunta la clave para iniciar el wireless... muy molesto.

1. Ir a Aplicaciones/Accesorios/Contraseñas y claves de cifrado
2. Una vez abierto “Contraseñas y claves de cifrado” da clic en la pestaña Contraseñas
3. Selecciona “default” y da clic con el botón derecho del ratón, en el menú contextual selecciona Cambiar la contraseña
4. Te saldrá la ventana “Cambiar la contraseña del depósito”, en la cual debes introducir tu Contraseña antigua, y deja en blanco los campos de Contraseña y Confirmar contraseña, clic en Cambiar
5. Te saldrá la advertencia “¿Almacenar sus contraseñas sin cifrarlas?”, da clic en Usar depósito inseguro
6. Ahora puedes cerrar “Contraseñas y claves de cifrado” y una vez reinicies el equipo no te pedirá de nuevo la contraseña

---

