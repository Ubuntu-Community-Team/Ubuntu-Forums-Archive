---
title: "Problemas con Evolution"
date: 2010-11-15
forum: Software
---

### Post by Vero1 on 2010-11-15
Hola todos,
No hace muchos días que he instalado Ubuntu Lucid Lynx.
En un principio no tenía los problemas que tengo ahora.
Pasa que no puedo enviar correos. El Servidor rechaza mi contraseña. Sin embargo no he tocado nada.
Presuntamente la contraseña es la misma que para el correo entrante pero...
He googleado, me comuniqué con mi ISP a ver si me podían dar la contraseña, cosa que rechazaron. Entré en contraseñas y claves pero la única contraseña que figura es la de pop(correo entrante).
Hice consultas en el Foro de Ubuntu-es y en una página Web llamada ubuntu-guía. He mirado la Ayuda. Cambié la contraseña por todas las que "podrían" ser, sin resultado alguno. Ya no sé qué más probar.
Agradecería si me pudieran ayudar con este problema, muy molesto.

saludos

---

### Post by hectorivand on 2010-11-16
> **Vero1 said:**
> Hola todos,
No hace muchos días que he instalado Ubuntu Lucid Lynx.
En un principio no tenía los problemas que tengo ahora.
Pasa que no puedo enviar correos. El Servidor rechaza mi contraseña. Sin embargo no he tocado nada.
Presuntamente la contraseña es la misma que para el correo entrante pero...
He googleado, me comuniqué con mi ISP a ver si me podían dar la contraseña, cosa que rechazaron. Entré en contraseñas y claves pero la única contraseña que figura es la de pop(correo entrante).
Hice consultas en el Foro de Ubuntu-es y en una página Web llamada ubuntu-guía. He mirado la Ayuda. Cambié la contraseña por todas las que "podrían" ser, sin resultado alguno. Ya no sé qué más probar.
Agradecería si me pudieran ayudar con este problema, muy molesto.

saludos

Pregunta ¿recibís bien los mensajes? ¿el problema solo se genera al enviar?

Saludos
Nacho

---

### Post by Vero1 on 2010-11-16
Hola,

Sí, recibir recibo sin problemas y no entiendo el motivo ya que la contraseña presuntamente es la misma que para el correo entrante.

Gracias.

---

### Post by pablo.s on 2010-11-16
Verificá que en el correo saliente (SMTP) 
esté activada la autenticación SSL y/o TLS.

---

### Post by hectorivand on 2010-11-16
> **Vero1 said:**
> Hola,

Sí, recibir recibo sin problemas y no entiendo el motivo ya que la contraseña presuntamente es la misma que para el correo entrante.

Gracias.

Vero, no es un problema de contraseña, tu proveedor seguramente cambio parametros de seguridad en el servidor de correo saliente y a partir de ahora, tenes que autenticarte antes de poder enviar un correo electrónico, por fortuna, esto es algo que se configura una sola vez y no se toca más.

Para configurar esto que te digo, tenes abrir Evolution. vas a Editar > Preferencias > Cuentas de correo. Seleccionas la cuenta que te está trayendo problemas. Haces un clic sobre editar.

En la solapa Envío de correo, tildas la opción "el servidor requiere autenticación"

En usuario.: Pones tu dirección de correo electrónico y seleccionas "recordar contraseña"

Fíjate en este screenshot que te subo para que entiendas mejor lo que te digo.

Después, enviate a vos misma un correo, te va a pedir la contraseña, la pones y seleccionas que la recuerde y listo, no te la va a pedir más.

Lo que comenta Pablo, no es seguro, ya que no sabemos si tu proveedor usa SSL o TLS para sumarle seguridad la conexión con el servidor. Con lo cual, ponele "Texto Plano"

Contanos que tal te fue.

Saludos
Nacho

---

### Post by Vero1 on 2010-11-16
Hola Pablo,
Le puse lo que me dijiste y me contesta que no está soportado.
Gracias igual por tu respuesta.

Hola Nacho,

Tengo configurado tal cual me decís, pero cundo quiero enviar sale un cartel que dice que me tengo que autenticar. Le pongo la contraseña y me dice que el Servidor no la acepta.

Me estoy volviendo loca con ésto.

Antes tenía Karmic y el problema no existía.

Gracias.

---

### Post by Vero1 on 2010-11-17
Hola todos,

El problema se solucionó.
Era una tontería de la que no me había dado cuenta.
Le faltaba poner el nombre del usuario en la parte de abajo(cosa que antes no se hacía y funcionaba igual).
Lo completé y ahora ya puedo enviar.
Agradezco su ayuda y les envío saludos.

Vero2

---

