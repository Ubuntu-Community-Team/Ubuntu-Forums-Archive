---
title: "[SOLVED] Montar web en ubuntu"
date: 2009-08-28
forum: Software
---

### Post by krakc on 2009-08-28
Hola a todos

bueno les comento que cuando tenia windows, en mi pc tenia una web montada, para eso usaba los siguientes programas:

appserver : como servidor
SQL server : para manejo de base de datos
no-ip : para enmascarar mi ip.

lo que quiero ahora es hacer lo mismo pero en ubuntu.... que programas reemplazarian a los anteriores para poder montar una web en mi pc???

gracias.

---

### Post by ramiro_md on 2009-08-28
Buenas Krakc, yo monte páginas web con Debian usando [esta]("http://www.forat.info/2008/03/05/como-montar-un-servidor-web-con-linux-debian/") guía. En Ubuntu debe ser muy parecido, por no decir igual. Espero que te haya servido.
Un saludo.

---

### Post by guisheca on 2009-08-28
Mirá, yo mucho que digamos no se del tema, pero se (y lo hice en mi pc) que tener una web en la pc con ubuntu es mas que facil mediante la instalacion de LAMP.
Basta con ir a synaptic>Editar>Marcar paquetes por tareas. Elegimos "Lamp server". Despues para administrar bases de datos, con el mismo synaptic, buscamos e instalamos phpmyadmin.
Eso es todo, con poner localhost en un navegador ya vas a ver la raiz de tu web que creo se encuentra en /var/www.

Mas info:
[Cesarius]("http://www.cesarius.net/instalar-lamp-en-ubuntu/")
[Tecnologías libres]("http://tecnologiaslibres.net/2008/11/08/instalar-servidor-lamp-linuxapachemysqlphp-en-ubuntu-810/")

Espero te sirva, yo lo hice y es recontra fácil, pero no lo pude sacar a la web porque no se como configurar mi router para que redireccione las entradas.

Saludos.

---

### Post by guillermolisi on 2009-08-28
> **krakc said:**
> hola

gracias a los dos por las respuestas... bueno he decidido cambiar el Apache por el Lighttpd, este ultimo es mas ligero y es justo lo que necesito.

ahora.. alguien sabe si en mysql se pueden ejecutar "trabajos" o querrys cada cierto tiempo como se hace en sqlserver ???

si alguien lo sabe hacer que me lo diga... XD
Como la pregunta es especifica sobre MySQL, va en thread aparte.

---

### Post by krakc on 2009-08-28
vale, la pregunta inicial quedo solucionada, ya me anda una web de prueba que he hecho y he conectado tambien a la base de datos...

revisare el otro thread!

gracias.

---

