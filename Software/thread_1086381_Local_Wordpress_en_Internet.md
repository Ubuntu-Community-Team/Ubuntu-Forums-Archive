---
title: "Local Wordpress en Internet"
date: 2009-03-04
forum: Software
---

### Post by zerosignal on 2009-03-04
Buenas noches amigos, como veran soy nuevo en esto del software libre. Instale Ubuntu Server Edition 8.10, instale LAMP. Tengo funcionando Wordpress en forma local de perlas bajo Apache2.
El problema surge cuando quiero visualizar el blog desde internet, no tengo problemas a la hora de configurar mi router para que redireccione los puertos necesarios (creo solo el 80) al equipo con el Ubuntu Server. Tengo DSL con IP dinamica, utilizo dyndns para actualizar mi ip via mi router. Cuando quiero ingresar al blog todos los links y referencias las hace a 'localhost' o sea no funciona. Intente cambiar la configuracion en wp-config.php pero nada. Espero me den una mano o una guia de que debo leer para esto.

Saludos

Zer0

---

### Post by c4d0rn4 on 2009-03-04
es un problema que surge por instalar wordpress como localhost, en la instalación toma "localhost" como la dirección y lo pasa a la base de datos.

La solución más paja es olvidate de ese wordpress borrale la base de datos y volvé a instalarlo SOLO cuando ya tengas un dominio tipo no-ip configurado. Luego usando tu dominio no-ip ejecutas el wp-config y sale con fritas.

La solución menos paja es, conseguir tu dominio no-ip y luego editar la base de datos del wordpress para que como dominio raiz pepito.no-ip.com y no localhost

Yo hostie mi propio wordpress durante mucho tiempo, pero mi pc hogareña no estaba para esos trotes jaja xD. Hoy en día soy un feliz usuario de blogger (pese a saber lo orgasmico que es wordpress)

El motivo por el que dejé wordpress fueron los servidores gratis que siempre estaban caidos o apestaban, me puse el mio, andaba bien pero mucho downtime jaja xD... wordpress.com no te deja editar css y blogger sí.

---

