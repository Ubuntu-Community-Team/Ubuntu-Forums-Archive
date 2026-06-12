---
title: "Problemas con Samba"
date: 2009-03-25
forum: Software
---

### Post by lithium25 on 2009-03-25
Hola a todos. Este es mi primer post en el foro y aclaro que soy un poco nuevo en esto de linux.
Instale Ubuntu 8.04 e instale samba. Cambie el nombre del WORKGROUP por el que uso en mi casa. Agregue el usuario de samba y todo bien hasta ahi.
En mi otra pc tengo XP y puedo acceder a mis sitios de red/grupo de trabajo/ y veo el equipo que contiene ubunto, pongo la clave y accedo lo más bien a mis carpetas compartidas.
El problema lo tengo para acceder desde Ubuntu a Windows. Me voy a Red - Servicios de Red y veo que dice Red de Microsoft Windows o algo así. Entro y veo el nombre del grupo de trabajo pero cuando hago doble click se queda pensando un rato y no veo mis equipos Windows. Muchas veces tampoco llego a ver ni el nombre de mi grupo de trabajo.
Lo que hice fue agregar dentro de la configuración de red las ip´s de mis otras máquinas 
192.168.1.2 user1
192.168.1.3 user 2
y así con todas.
Pero tampoco funciona.

Si puedo acceder desde Firefox escribiendo smb://192.168.1.2 pero no es lo que necesito
Aclaro que en XP tengo el firewall desactivado.

Agradecería si alguien me puede dar una mano porque ya no se que es lo que esta funcionando mal.
En otras oportunidades que instale ubuntu 7.04 y podía acceder a mis equipos.

Saludos!

---

### Post by lithium25 on 2009-03-27
nadie sabe?

---

### Post by guillermolisi on 2009-03-27
> **lithium25 said:**
> Hola a todos. Este es mi primer post en el foro y aclaro que soy un poco nuevo en esto de linux.
Instale Ubuntu 8.04 e instale samba. Cambie el nombre del WORKGROUP por el que uso en mi casa. Agregue el usuario de samba y todo bien hasta ahi.
En mi otra pc tengo XP y puedo acceder a mis sitios de red/grupo de trabajo/ y veo el equipo que contiene ubunto, pongo la clave y accedo lo más bien a mis carpetas compartidas.
El problema lo tengo para acceder desde Ubuntu a Windows. Me voy a Red - Servicios de Red y veo que dice Red de Microsoft Windows o algo así. Entro y veo el nombre del grupo de trabajo pero cuando hago doble click se queda pensando un rato y no veo mis equipos Windows. Muchas veces tampoco llego a ver ni el nombre de mi grupo de trabajo.
Lo que hice fue agregar dentro de la configuración de red las ip´s de mis otras máquinas 
192.168.1.2 user1
192.168.1.3 user 2
y así con todas.
Pero tampoco funciona.

Si puedo acceder desde Firefox escribiendo smb://192.168.1.2 pero no es lo que necesito
Aclaro que en XP tengo el firewall desactivado.

Agradecería si alguien me puede dar una mano porque ya no se que es lo que esta funcionando mal.
En otras oportunidades que instale ubuntu 7.04 y podía acceder a mis equipos.

Saludos!
Esas IPs y los user donde los pusiste ? En las maquinas windows pero en que lugar de cada una ?

Podrias mostrar el contenido de tu archivo de configuracion de Samba (/etc/samba/smb.conf) ?

En que red esta la maquina con Ubuntu ? En 192.168.0.x o en otra ?

---

