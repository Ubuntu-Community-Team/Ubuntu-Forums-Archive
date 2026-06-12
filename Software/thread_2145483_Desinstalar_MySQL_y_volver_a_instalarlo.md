---
title: "Desinstalar MySQL y volver a instalarlo"
date: 2013-05-15
forum: Software
---

### Post by javierlinux1 on 2013-05-15
Tengo un problema que me está enloqueciendo. 

En un servidor que tenía instalado LAMP se olvidaron la clave de root de MySQL y me pidieron que lo desinstalara para volver a instalarlo. Yo cometí el grosero error de no leer nada y directamente desintalar todo. 

Es un Ubuntu Server 12.04 y ejecuté 

apt-get remove --purge mysql 

y borro 94,8 mb de paquetes. 

A continuación hice la instalación, me pidio la clave de root tres veces y empezaron los problemas... Me da este error (es largo y sigo abajo): 

apt-get install mysql-server mysql-client 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias 
Leyendo la información de estado... Hecho 
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios. 
libsmbclient obex-data-server libavahi-glib1 libsoup-gnome2.4-1 libopenobex1 libgd2-xpm libexif12 libbluetooth3 
libsoup2.4-1 
Utilice «apt-get autoremove» para eliminarlos. 
Se instalarán los siguientes paquetes extras: 
libdbd-mysql-perl libmysqlclient18 mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server-5.5 
mysql-server-core-5.5 
Paquetes sugeridos: 
tinyca mailx 
Se instalarán los siguientes paquetes NUEVOS: 
libdbd-mysql-perl libmysqlclient18 mysql-client mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server 
mysql-server-5.5 mysql-server-core-5.5 
0 actualizados, 9 se instalarán, 0 para eliminar y 1 no actualizados. 
Se necesita descargar 0 B/26,3 MB de archivos. 
Se utilizarán 94,8 MB de espacio de disco adicional después de esta operación. 
¿Desea continuar [S/n]? s 
Preconfigurando paquetes ... 
Seleccionando paquete mysql-common previamente no seleccionado 
(Leyendo la base de datos ... 109385 ficheros o directorios instalados actualmente.) 
Desempaquetando mysql-common (de .../mysql-common_5.5.31-0ubuntu0.12.04.1_all.deb) ... 
Seleccionando paquete libmysqlclient18 previamente no seleccionado 
Desempaquetando libmysqlclient18 (de .../libmysqlclient18_5.5.31-0ubuntu0.12.04.1_amd64.deb) ... 
Seleccionando paquete libdbd-mysql-perl previamente no seleccionado 
Desempaquetando libdbd-mysql-perl (de .../libdbd-mysql-perl_4.020-1build2_amd64.deb) ... 
Seleccionando paquete mysql-client-core-5.5 previamente no seleccionado 
Desempaquetando mysql-client-core-5.5 (de .../mysql-client-core-5.5_5.5.31-0ubuntu0.12.04.1_amd64.deb) ... 
Seleccionando paquete mysql-client-5.5 previamente no seleccionado 
Desempaquetando mysql-client-5.5 (de .../mysql-client-5.5_5.5.31-0ubuntu0.12.04.1_amd64.deb) ... 
Seleccionando paquete mysql-server-core-5.5 previamente no seleccionado 
Desempaquetando mysql-server-core-5.5 (de .../mysql-server-core-5.5_5.5.31-0ubuntu0.12.04.1_amd64.deb) ... 
Procesando disparadores para man-db ... 
Configurando mysql-common (5.5.31-0ubuntu0.12.04.1) ... 
Seleccionando paquete mysql-server-5.5 previamente no seleccionado 
(Leyendo la base de datos ... 109566 ficheros o directorios instalados actualmente.) 
Desempaquetando mysql-server-5.5 (de .../mysql-server-5.5_5.5.31-0ubuntu0.12.04.1_amd64.deb) ... 
Seleccionando paquete mysql-client previamente no seleccionado 
Desempaquetando mysql-client (de .../mysql-client_5.5.31-0ubuntu0.12.04.1_all.deb) ... 
Seleccionando paquete mysql-server previamente no seleccionado 
Desempaquetando mysql-server (de .../mysql-server_5.5.31-0ubuntu0.12.04.1_all.deb) ... 
Procesando disparadores para ureadahead ... 
Procesando disparadores para man-db ... 
Configurando libmysqlclient18 (5.5.31-0ubuntu0.12.04.1) ... 
Configurando libdbd-mysql-perl (4.020-1build2) ... 
Configurando mysql-client-core-5.5 (5.5.31-0ubuntu0.12.04.1) ... 
Configurando mysql-client-5.5 (5.5.31-0ubuntu0.12.04.1) ... 
Configurando mysql-server-core-5.5 (5.5.31-0ubuntu0.12.04.1) ... 
Configurando mysql-server-5.5 (5.5.31-0ubuntu0.12.04.1) ... 
Error del analizador AppArmor para /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld en la l?nea 9: No se pudo abrir <<abstractions/mysql>> 
start: Job failed to start 
invoke-rc.d: initscript mysql, action "start" failed. 
dpkg: error al procesar mysql-server-5.5 (--configure): 
el subproceso instalado el script post-installation devolvió el código de salida de error 1 
Configurando mysql-client (5.5.31-0ubuntu0.12.04.1) ... 
dpkg: problemas de dependencias impiden la configuración de mysql-server: 
mysql-server depende de mysql-server-5.5; sin embargo: 
El paquete `mysql-server-5.5' no está configurado todavía. 
dpkg: error al procesar mysql-server (--configure): 
problemas de dependencias - se deja sin configurar 
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo. 
Procesando disparadores para libc-bin ... 
ldconfig deferred processing now taking place 
Se encontraron errores al procesar: 
mysql-server-5.5 
mysql-server 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Y estoy estancado en eso. No encuentro la manera de hacer que se "olvide" que le pusieron contraseña a mysql y NO PUEDO reinstalar el Servidor donde está corriendo. 

Si alguien me puede ayudar les agradezco muchisimo. 

PD: Aclaro que llevo tres dias siguiendo tutoriales y no logro dar con la solución.

---

### Post by biale on 2013-05-19
Parece que el el subsistema de seguridad que provee apparmor esta inhibiendo el proceso. Tendrias que estudiar como desconectarlo en forma provisoria.

Pero el punto no sería ese sino donde y como se almacena la clave de admistracion del MySQL. Cuando reinstales los ejecutables es muy posible que las configuraciones y las bases no se renueven y el problema seguiria existiendo.

Siempre existe la posibiilidad de hacer "percha" todo, pero en ese caso los datos almacenados tambien mueren. O sea que si en las bases hay datos utiles hay que tomar backup...

---

### Post by gmunioz on 2013-05-19
Prueba:
Eliminar el archivo /etc/apparmor.d/usr.sbin.mysqld

---

### Post by guillermolisi on 2013-05-21
Señores, tengo que felicitarlos porque los dos han dado en el clavo. Javier resolvio el tema y el inconveniente estaba justamente en la relacion de apparmor y MySQL.

---

