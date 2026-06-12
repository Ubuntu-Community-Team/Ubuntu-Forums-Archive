---
title: "Busco Cliente para Blogging tipo BloGTK"
date: 2010-05-08
forum: Software
---

### Post by Bizware on 2010-05-08
Hola amigos,

Estoy utilizando Ubuntu 10.04 64 bits, y no logro hacer funcionar el BloGTK, así que me puse en campaña para encontrar un programa cliente para blogging,

¿conocen alguno que me puedan sugerir?

Y aprovechando... ¿saben porqué no anda BloGTK en 64 bits?

Un abrazo, y gracias.

---

### Post by alfplayer on 2010-05-09
No te funciona BloGTK en 10.04 64-bit? Por qué?

---

### Post by Bizware on 2010-05-09
> **alfplayer said:**
> No te funciona BloGTK en 10.04 64-bit? Por qué?

Hola alfplayer,

Gracias por interesarte en mi inquietud.

Te comento que en realidad no sé cual es el problema por el que no anda. En la versión 9.10 de 32 bits andaba perfecto. Por eso supongo que la razón debe ser que no corre bien en 64 bits, un poco simplista mi deducción :) 

Lo que hice ahora para seguir trabajando es instalarme el Xampp y Wordpress 2.9.2 localmente y escribo desde ahí.

No quiero quedarme con esta solución, por eso me gustaría encontrar un software que sirva para blogging, ya probé unos cuantos pero o no andan en 64 bits o están muy recortados (como Drivel)

Si tienes alguna sugerencia, o los amigos de la comunidad, se los agradeceré mucho (de igual manera si encuentro una solución la comentaré aquí).

Saludos.

---

### Post by alfplayer on 2010-05-09
Cuál es el problema que encontrás? Error en la instalación? Error al abrir la aplicación?

---

### Post by Bizware on 2010-05-09
> **alfplayer said:**
> Cuál es el problema que encontrás? Error en la instalación? Error al abrir la aplicación?

No hace nada  :(

Es decir que en la instalación se registró bien, incluso aparece en <Aplicaciones> <Internet> <BloGTK 2.0> pero al darle clic, pone un indicativo en el Panel "Iniciando BloGTK" y a los 20 segundos desaparece sin más.

Eso es todo.  No aparece ningún error, no aparece ninguna ventana, nada.

---

### Post by guillermolisi on 2010-05-09
> **Bizware said:**
> No hace nada  :(

Es decir que en la instalación se registró bien, incluso aparece en <Aplicaciones> <Internet> <BloGTK 2.0> pero al darle clic, pone un indicativo en el Panel "Iniciando BloGTK" y a los 20 segundos desaparece sin más.

Eso es todo.  No aparece ningún error, no aparece ninguna ventana, nada.
Para saber bien que esta pasando, nada mejor que correr el comando de ese programa en consola/terminal.

Para saber como se llama, una forma es editar el menu y ver ahi el nombre del archivo que invoca el lanzador. 

Luego correrlo en linea de comando (consola/terminal) y tomar nota de los mensajes que aparezcan, daran buena informacion al respecto, tanto al inicio como al cierre.

---

### Post by Bizware on 2010-05-09
> **guillermolisi said:**
> Para saber bien que esta pasando, nada mejor que correr el comando de ese programa en consola/terminal.

Para saber como se llama, una forma es editar el menu y ver ahi el nombre del archivo que invoca el lanzador. 

Luego correrlo en linea de comando (consola/terminal) y tomar nota de los mensajes que aparezcan, daran buena informacion al respecto, tanto al inicio como al cierre.

Hice lo que me has sugerido, y esto es lo que aparece por terminal:

Traceback (most recent call last):
  File "/usr/bin/blogtk2", line 6, in <module>
    from blogtk2 import main
  File "/usr/bin/../share/blogtk2/lib/blogtk2/__init__.py", line 35, in <module>
    from blogtk2.main import main
  File "/usr/bin/../share/blogtk2/lib/blogtk2/main.py", line 22, in <module>
    from gdata import service

Puede venir el problema por el lado de Python? (lo digo por los errores en las lineas 35 y 22 que hacen alusión a dos archivos  .py)

---

### Post by alfplayer on 2010-05-09
Cómo lo instalaste? Instalando el paquete de Ubuntu (recomendado)? Con Synaptic? Con un comando? Instalando un archivo descargado del sitio de BloGTK?

---

### Post by Thalskarth on 2010-05-09
> **Bizware said:**
> ... así que me puse en campaña para encontrar un programa cliente para blogging,

¿conocen alguno que me puedan sugerir?

Te recomiendo Blogilo. Es realmente muy buen cliente.

---

