---
title: "Geetpeername ( problema samba ) Solucion?"
date: 2010-04-19
forum: Software
---

### Post by padasystem on 2010-04-19
Hola a todos, estoy teniendo problemas con samba en ubuntu server 9.04. Haber si alguien me da una mano.
Mirando los logs de samba /var/log/samba/log.smbd encuento unas lineas que dicen:

[COLOR=#000000][FONT=Times New Roman][FONT=verdana]**lib**/**util_sock**.**c**:**get_peer_addr_internal**(**1676**) 
getpeername failed. Error was Transport endpoint is not **connected** 
write_data: write failure in writing to **client** 0.0.0.0. Error **Connection **reset by peer [/FONT][/FONT][/COLOR]

Se conectan varios WINXP a ese server, y en cada log de cada conexion ( PC ) da ese mensaje en forma aleatoria provocando perdida de conexion con algunos softwares.
EL servidor no es PDC, solamente comparte una carpeta PUBLICA para todas las PCS con XP.

He buscado por internet y hablan sobre los puertos de conexion que maneja samba y windows, sobre el 139 y el 445, asi que agregue una linea en samba asi:
smb ports = 139 

Sigo con problemas...! 

Alguna sugerencia ? espero sus respuestas!!.

Gracias.

---

