---
title: "Consulta sobre dominios windows en ubuntu"
date: 2011-07-12
forum: Software
---

### Post by asterix77 on 2011-07-12
Hola a todos.

Deseo hacer una consulta. En mi empresa existe un dominio al cual los usuarios ingresan a través de equipos windows, incluido yo, para lo cual tengo asignado un notebook. Mi idea es instalar ubuntu en un disco duro externo con el grub en el. Tengo entendido que si el grub está en el disco duro externo, aparecerá solo si conecta el disco usb.

Al tener mi usuario y clave creada en el dominio, pienso que podría configurar mi notebook con ubuntu (se trataría del mismo con el que me conecto pero con windows)

¿se podría hacer eso?

Los tutoriales que he visto en google, apuntan a ingresar un equipo con ubuntu por primera vez, por lo que es necesario la autorización del administrador del dominio; si hago eso acá, no me van a dejar.

La verdad es ahora estoy usando el mismo notebook con un live cd, y corre de maravillas,mucho mejor que con windows. Llevo usando 5 años ubuntu y me resisto a dejarlo.


Por favor si alguien me puede ayudar en eso. Saludos

---

### Post by gmunioz on 2011-07-12
1- Ten mucho cuidado al instalar el Grub, ya que siempre busca instalarse en /dev/sda.
2- En mi lugar de trabajo tenemos una aplicación de gestión corriendo en un servidor Windows, accedo sin problemas y ejecuto el exe con Wine desde Ubuntu.
3- Solo requiere que:
Esten instalados samba samba-common y smbclient
El equipo lleve el nombre de uno autorizado por el servidor
En la configuración de samba el workgroup sea el de la red.

---

### Post by asterix77 on 2011-07-14
Gracias por la respuesta, tendré mucho cuidado. Espero no estropear algo.
 
¿Nadie ha tenido una situación similar que pudiera comentar?
 
 
Saludos

---

