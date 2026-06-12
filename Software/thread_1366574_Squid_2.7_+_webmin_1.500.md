---
title: "Squid 2.7 + webmin 1.500"
date: 2009-12-28
forum: Software
---

### Post by quedefantasma on 2009-12-28
Estimados, estoy hace días intentando configurar un "proxy-server" (nombre común) para en principio compartir la conexion a internet a las maquinas de la red (intranet). y mas adelante intentar usar restricciones y caches...para optimizar el uso de la misma.

Despues de bastante trabajo, pruebas y errores (SOY NOVATO) Tengo instalados el ubuntu server 9.10, webmin 1.500, y el modulo squid 2.7. Tambien dos placas de red configuradas eth0 con la IP asignada por el servidor DHCP de la red, y eth1 con la direccion IP asignada por el servidor DHCP del router. Aparentemente ambas funcionando...

Seguí y leí varios tutoriales y how to's pero no encontré ninguno que cubra estas dos aplicaciones en conjunto...muchos hablan solo de SQUID y su configuración por medio de la consola y la edicion del archivo SQUID.CONF. Otros solo de WEBMIN y están desactualizados o solo pasan por arriba la configuración básica del modulo SQUID.

---

### Post by guillermolisi on 2009-12-28
Webmin es una herramienta para administrar, graficamente via web browser, servidores.

La configuracion de Squid te conviene llevarla a cabo desde consola. En [http://www.squid-cache.org/](http://www.squid-cache.org/) bajo el titulo Documentation tenes practicamente todo lo que necesitas, en Ingles, para dejarlo casi como vos queres.

---

### Post by jpmorelli on 2009-12-28
Quedefantasma, yo ya armé una vez lo que vos querés armar. Con paciencia va quedando perfecto y te puedo asegurar que anda impresionantemente bien. Es un fierro.
No hace falta el webmin, es solo un servicio web para que administres las millones de opciones de servicios que despues podés levantar en la PC que vas a usar de proxy, firewall, etc
Te comento, yo levante un Firewall, Proxy, DNS, Antispam, Routing, Content Filter, y anda genial. Todo en un Celeron 2.4 con 1Gb de memoria. El CPU oscilaba entre el 2 y el 10 % !!! se mata de risa.
Eso si, te recomiendo que uses todo esto junto con el shorewall (firewall basado en IPTables pero de más fácil configuración que éste ultimo)
Yo saqué todos los datos de configuración desde esta página. Ahí tenés miles de ejemplos de como se setean las cosas.
Teniendo en cuenta algunos conceptos intermedios de routing y gateway y DNS todo te va a funcionar !

El link: [http://www.shorewall.net]("http://www.shorewall.net")
Te vas a la parte de Documentation y ahí tenés de todo, incluso multiples proveedores con fail over, etc.
Suerte !

---

### Post by quedefantasma on 2009-12-29
> **guillermolisi said:**
> Webmin es una herramienta para administrar, graficamente via web browser, servidores.

La configuracion de Squid te conviene llevarla a cabo desde consola. En [http://www.squid-cache.org/](http://www.squid-cache.org/) bajo el titulo Documentation tenes practicamente todo lo que necesitas, en Ingles, para dejarlo casi como vos queres.

Guillermo, si esto lo lei por varios lados y estuve leyendo la documentacion de squid...

Pero al instalar el WEBMIN me encontre con muchisimas lineas de comando en el SQUID.CONF y en el panel de control del webmin unas cuantas ACL'S y restricciones que ya vienen por defecto...

Podre borrar todas estas configuraciones sin problemas y comenzar a configurar el squid desde cero? Como lo ves?

---

### Post by quedefantasma on 2009-12-29
> **jpmorelli said:**
> Quedefantasma, yo ya armé una vez lo que vos querés armar. Con paciencia va quedando perfecto y te puedo asegurar que anda impresionantemente bien. Es un fierro.
No hace falta el webmin, es solo un servicio web para que administres las millones de opciones de servicios que despues podés levantar en la PC que vas a usar de proxy, firewall, etc
Te comento, yo levante un Firewall, Proxy, DNS, Antispam, Routing, Content Filter, y anda genial. Todo en un Celeron 2.4 con 1Gb de memoria. El CPU oscilaba entre el 2 y el 10 % !!! se mata de risa.
Eso si, te recomiendo que uses todo esto junto con el shorewall (firewall basado en IPTables pero de más fácil configuración que éste ultimo)
Yo saqué todos los datos de configuración desde esta página. Ahí tenés miles de ejemplos de como se setean las cosas.
Teniendo en cuenta algunos conceptos intermedios de routing y gateway y DNS todo te va a funcionar !

El link: [http://www.shorewall.net](http://www.shorewall.net)
Te vas a la parte de Documentation y ahí tenés de todo, incluso multiples proveedores con fail over, etc.
Suerte !

Gracias JP! En eso estoy....ya me pongo a ver esto que me recomendas. Slds.

---

### Post by guillermolisi on 2009-12-29
> **quedefantasma said:**
> Guillermo, si esto lo lei por varios lados y estuve leyendo la documentacion de squid...

Pero al instalar el WEBMIN me encontre con muchisimas lineas de comando en el SQUID.CONF y en el panel de control del webmin unas cuantas ACL'S y restricciones que ya vienen por defecto...

Podre borrar todas estas configuraciones sin problemas y comenzar a configurar el squid desde cero? Como lo ves?
Como poder se puede, lo que no se es si te conviene.

Tambien uso Webmin pero en aquellos casos en los que te facilita la administracion y no la entorpece ni disimula. Tambien es lo ultimo que instalo luego de haber puesto en servicio todo lo anterior, por eso hablaba de configurar Squid sin ningun tipo de asistencia "extra". Ademas la documentacion existente debe considera Squid solamente, sin ningun otro tipo de herramienta (tal como te has dado cuenta al principio de este thread).

---

### Post by quedefantasma on 2010-01-27
Aquí nuevamente con mis consultas y dudas...

Estoy actualmente y finalmente conectado mediante mi servidor UBUNTU 9.10 con SQUID 2.7 y WEBMIN 1.500 como ayuda para las configuraciones.

Como muy bien me recomendaron, finalmente fue mas facil configurar el SQUID en forma manual desde el archivo squid.conf y despues retocarlo con el webmin.

Aparentemente esta casi todo funcionando! aunque me faltan ajustar los permisos para los diferentes grupos de usuarios...y algun "fine tunning" para que esté como lo necesito.

También me fue de mucha ayuda el post [http://ubuntuforums.org/showthread.php?t=1355298&page=2](http://ubuntuforums.org/showthread.php?t=1355298&page=2) de este foro.

Ahora la nueva consulta...la cual quizás amerite un nuevo post?!

Segun tengo entendido SQUID no puede intermediar las conexiones SMTP, POP3, TELNET, SSH, IRC...por lo que necesitaría un SOCKS server DANTE para intermediar las conexiones de los clientes de la red al correo electrónico...

No estoy encontrando casi ninguna información sobre DANTE, ni su configuración, ni su modulo de WEBMIN...nada como para arrancar!

Alguien que me pueda dar algunas pistas? Alguna recomendación para manejar esto? Es realmente DANTE lo que necesito?

Muchas gracias y Slds.

---

